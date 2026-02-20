# Migration Guide
## Migration to Data Management API Version 5.0.0
This guide gives you some step-by-step information to perform a major update of KomMonitor Data Management API
from any version below the latest 5.0.0 version. The 5.0.0 Data Management API version introduces a completely new mandant concept, which requires the migration of the existing KomMonitor database schema. If you plan set up a
fresh instance of KomMonitor, you are fine and don't have to perform any migration steps. Otherwise, you
can use the instructions listed below, which supports you to perform the migration by the use of 
[Liquibase](https://docs.liquibase.com/pro/reference-guide-4-33/parameters/liquibase-catalog-name).

**Important: Make sure you have created a proper backup of your database, which can be used for
restoring the current state of the database, if the migration process fails. We strongly recommend 
that you apply the following migration steps to a copy of your database and only move to that database
if you are sure the migration was successful**
### From 4.x.x
This section captures the migration steps that are required to update from any version 4.x.x 
of the Data Management API to version 5.0.0.
#### 1) Capture current DB state
First, capture the current state of those tables of your KomMonitor DB that have to be manually enhanced
with additional values. In particular, these are the tables `indicatorspatialunits`, `metadatageoresources`,
`metadataindicators`, `metadataspatialunits`, `organizationalunits`, `permissions`. For this purpose,
you have to generate a changelog with the Liquibase [generate-changelog](https://docs.liquibase.com/pro/reference-guide-4-33/database-inspection-change-tracking-and-utility-commands/generate-changelog)
command that includes `data` in the `--diff-types` parameter. 

You can use the template listed below for this purpose. Just adapt the parameters to your environment.
Note, that the Liquibase Docker container must have access to your KomMonitor database and to the mounted data directories. 
It may be required to adapt the permissions of the mounted data directories so that the Liquibase Docker container is able to
write to these directories.:

```Shell
docker run --network=kommonitor \
-v /home/user/kommonitor/liquibase/changelog:/liquibase/db/changelog \
-v /home/user/kommonitor/liquibase/data:/liquibase/data_output \
liquibase/liquibase:4.33 generate-changelog \
--changelog-file=db/changelog/kommonitor-changelog-data-base.xml \
--diffTypes=data \
--include-objects="indicatorspatialunits,metadatageoresources,metadataindicators,metadataspatialunits,organizationalunits,roles" \
--dataOutputDirectory=data_output \
--driver=org.postgresql.Driver \
--url="jdbc:postgresql://kommonitor-db:5432/kommonitor_data" \
--username=kommonitor \
--password=kommonitor  
```

If command execution was successfull, you'll find a generated changelog in the `/home/user/kommonitor/liquibase/changelog` 
directory and for each table a CSV file in the `/home/user/kommonitor/liquibase/data:/liquibase/data_output` 
directory on your host.

Note, that you will only need the CSV files in the following steps, since the 
[db-schema-migration GitHub repo](https://github.com/KomMonitor/db-schema-migration) comes with several
prepared Liquibase changelog files for migration of different DB schema versions.

For editing the CSV files in the following steps, use a tool that is able to generate CSV files that matches
the following format specifications:
* use comma (,) as column seperator
* use dot (.) as decimal seperator in floating values
* all field values are quoted (")
* the CSV-files are UTF-8 encoded

For CSV files that have a differing format it can not be guaranted that data migration will succeed. 
However, it is possible to adapt some options of the `loadUpdateData` changesets in the [migration changelog](https://github.com/KomMonitor/db-schema-migration/blob/develop/changelog/kommonitor-changelog-4.x-5.0.0.xml)
in accordance to your custom CSV format. For this purpose, read the [Liquibase docs](https://docs.liquibase.com/pro/reference-guide-4-33/change-types/load-update-data).

#### 2) Adapt permission data
Edit the `roles.csv` file with a tool that lets you easily handle tabular data.
1. Rename the CSV file `roles.csv` to `permissions.csv`
2. Rename the column `roleid` to `permissionid`
3. Rename the column `rolename` to `name`
4. Add a new column `permissiontype`
5. Fill each cell for the column `permissiontype` with the value `resources`

#### 3) Adapt organizational unit data
Edit the `organizationalunits.csv` file with a tool that lets you easily handle tabular data.
1. Add new column `ismandant` -> Fill each cell for this column with `true` or `false`, dependent
on whether the organizational unit is a mandant or not
2. Add new column `mandant` -> Fill each cell for this column with the ID of an organizational unit that
that acts as mandant for the current organizational unit. Organizational units that have a `true` value
for the `ismandant` column must have their own ID for this field.
3. Add new column `parent` -> Fill each cell for this column with the ID of an organizational unit that
is parent for the current organizational unit. Organizational units that have a `true` value for the
`ismandant` column must have the value `null` for this field, since mandant do not have a parent
organizational unit.

**Important:** Make sure that the special organizational units "kommonitor" and "public" are not referenced
as parent or mandant in the CSV files. These entities are deprecated and will be deleted at initial
startup of the Data Management API. Also, do not reference these organizational units as owner
for datasets during the following steps.

#### 4) Adapt georesources
Edit the `metadatageoresources.csv` file with a tool that lets you easily handle tabular data.
1. Add new column `ispublic` -> Fill each cell for this column with `true` or `false`, dependent
on whether the georesource should be public or not.
2. Add new column `owner` -> Fill each cell for this column with the ID of the organizational unit
that is owner of a georesource

#### 5) Adapt spatial units
Edit the `metadataspatialunits.csv` file with a tool that lets you easily handle tabular data.
1. Add new column `ispublic` -> Fill each cell for this column with `true` or `false`, dependent
on whether the spatial unit should be public or not.
2. Add new column `owner` -> Fill each cell for this column with the ID of the organizational unit
that is owner of a spatial unit

#### 6) Adapt indicators metadata
Edit the `metadataindicators.csv` file with a tool that lets you easily handle tabular data.
1. Add new column `ispublic` -> Fill each cell for this column with `true` or `false`, dependent
on whether the indicator should be public or not.
2. Add new column `owner` -> Fill each cell for this column with the ID of the organizational unit
that is owner of an indicator

#### 7) Adapt indicators timeseries data
Edit the `indicatorspatialunits.csv` file with a tool that lets you easily handle tabular data.
1. Add new column `ispublic` -> Fill each cell for this column with `true` or `false`, dependent
on whether the indicator timeseries data for a certain spatial unit should be public or not.
2. Add new column `owner` -> Fill each cell for this column with the ID of the organizational unit
that is owner of the timeseries data for a certain spatial unit. Note, that the owner ID for the 
timeseries data of an indicator should be the same as the owner ID of the metadata for the same
indicator.

#### 8) Update DB to new schema
Now, with the adapted CSV files, you can perform the update of your KomMonitor DB to a new 5.x.x schema.
For this purpose, you can simply use a [prepared Liquibase changelog](https://github.com/KomMonitor/db-schema-migration/blob/develop/changelog/).
Choose the changelog script that fits to your current Data Management API version and the target version.
Download this file and place it at `/home/user/kommonitor/liquibase/changelog`. Make also sure that you 
have placed your CSV files at `/home/user/kommonitor/liquibase/data`. The command listed below performs
the database update by using the [Liquibase update command](https://docs.liquibase.com/pro/reference-guide-4-33/init-update-and-rollback-commands/update).
Just adapt it to your environment and execute the command.
```Shell
docker run --network=kommonitor \
-v /home/user/kommonitor/liquibase/changelog:/liquibase/db/changelog \
-v /home/user/kommonitor/liquibase/data:/liquibase/data_input \
liquibase/liquibase:4.33 update \
--changelog-file=db/changelog/kommonitor-changelog-4.1.x-5.1.0.xml \
--driver=org.postgresql.Driver \
--url="jdbc:postgresql://kommonitor-db:5432/kommonitor_data" \
--username=kommonitor \
--password=kommonitor 
```
This will apply all changesets to your database to update its schema and also loads the missing data, which
you have prepared in the CSV files, into the tables.

#### 9) Sync DB to root schema
With Data Management API version 5.0.0 we integrated Liquibase as fixed part to perform all future migration tasks.
This requires to baseline your migrated database to the target 5.x.x schema from the previous step. As a result, 
when you first start the Data Management API Liquibase automatically recognizes that your database has been migrated 
to a new schema and won't apply any changesets to it, which usually would be done if you start with a clean environment.

For this purpose, you can use the [Liquibase changelog-sync command](https://docs.liquibase.com/pro/reference-guide-4-33/database-inspection-change-tracking-and-utility-commands/changelog-sync)
as stated in the snippet below. Download all required [changelog files](https://github.com/KomMonitor/data-management/blob/master/src/main/resources/db/changelog)
and place it into the `/home/user/kommonitor/liquibase/changelog` directory. Within the `kommonitor-changelog-root.xml` 
remove all includings of versions that are above your migrated version. E.g. if you used `kommonitor-changelog-4.1.x-5.1.0.xml`
the previous step, you have to remove `<include file="db/changelog/kommonitor-changelog-5.1.1.xml"/>` from `kommonitor-changelog-root.xml`.
Then adapt the following command to your environment before execution.
```Shell
docker run --network=kommonitor \
-v /home/user/kommonitor/liquibase/changelog:/liquibase/db/changelog \
liquibase/liquibase:4.33 changelog-sync \
--changelog-file=db/changelog/kommonitor-changelog-root.xml \
--driver=org.postgresql.Driver \
--url="jdbc:postgresql://kommonitor-db:5432/kommonitor_data" \
--username=kommonitor \
--password=kommonitor
```

#### 10) Configure Keycloak
##### 10.1) Use Custom Keycloak image
We have built and published a custom Keycloak image that contains some KomMonitor specific extension, such as a custom
role mapper as well as a custom policy evaluation provider. To use the custom Keycloak image, you have to adapt your
Docker Compose setup for Keycloak according to our [Docker Compose template](https://github.com/KomMonitor/docker/blob/feature/multi-tenancy/prod/keycloak/docker-compose.yml).
Our custom image is built upon a recent Keycloak version. Usually, Keycloak automatically updates the DB schema when starting a new version for the first time. However, if you 
use an older version of Keycloak then our custom Keycloak image, you should review the [migration changes of Keycloak](https://www.keycloak.org/docs/latest/upgrading/)
and read the [upgrading instructions](https://www.keycloak.org/docs/latest/upgrading/#_upgrading).

Also note, that the custom image is built for supporting fixed DB provider, which can not be changed. Currently, we built images that support 
the following DB providers:
* [MSSQL](https://hub.docker.com/layers/kommonitor/keycloak/latest-mssql/images/sha256-cb74a77aff7922ab11897c9103bd0a5523c5d7e692e990515d11d27cd46be2f5)
* [PostgreSQL](https://hub.docker.com/layers/kommonitor/keycloak/latest-postgres/images/sha256-65854815b05d6b893f361cc6fd59c1dfb221ff88dc7f2e8c1160405bc59f50aa)

##### 10.2) Configure Admin CLI
The new version of the Data Management API utilizes a Keycloak Admin Client for managing, roles and policies in accordance
to the organizational units. For this purpose, it is required to allow the Data Management API to communicate with Keycloak.
You can prepare Keycloak as follows:
1. Open the Keycloak client configuration in the Keycloak Admin UI for the Admin Client: "Clients" -> "admin-cli" -> "Settings"
2. Enable "Client auhentication" and "Service account roles"
3. Assign "kommonitor-creator" under "Service accounts roles"
4. Generate a client secret under "Credentials"
5. Set the client secret in the Docker Compose setup for the Data Management API for the environment variable [KK_CLI_SECRET](https://github.com/KomMonitor/docker/blob/5db513ce6275c466beb576306e20bfa5efc88435/prod/kommonitor/.env#L24).

##### 10.3) Configure Role Mapper
Our pre-built Keycloak image comes with a custom role mapper that has to be set as default for the KomMonitor realm in Keycloak.
For this purpose, follow the steps below:
1. Open the "Client Scopes" configuration page
2. Select the "roles" scope 
3. Open the "Mappers" tab
4. Delete the "realm roles" mapper
5. Add a new mapper by clicking "Add mapper" -> "By Configuration"
6. Select the "Kommonitor Role Mapper"
7. Configure the "Kommonitor Role Mapper" as follows:
    * *Name*: `kommonitor realm roles`
    * *Multivalued*: `On`
    * *Token Claim Name*: `realm_access.roles`
    * All other fields can have the default values

##### 10.4) Create Groups Scope
KomMonitor services need information about group membership of a user. By default, that JWT that is granted by Keycloak
does not contain a group claim, which have to be configured additionally:
1. Open the "Client Scopes" configuration page
2. Create a new scope by clicking on "Create client scope" and set the following configuration parameters:
    * *Name*: `groups`
    * *Description*: `user groups`
    * *Type*: `default`
    * *Include in token scope*: `On`
3. After saving the new scope add a mapper by clicking on "Add mapper" -> "By Configuration" at the "Mappers" tab
4. Select the "Group Membeship" mapper
5. Configure the "Group Membeship Mapper" as follows:
    * *Name*: `groups`
    * *Token Claim Name*: `groups`
    * All other fields can have the default values
6. Add the newly created groups client scope to every single KomMonitor service that is registered as client at Keycloak. Below you find
the steps for the Data Management API client:
    * Open the "Clients" page
    * Select "kommonitor-data-management"
    * Open the "Client scopes" tab
    * Click "Add client scope"
    * Select "groups" scope and click "Add" -> "Default"
    * Repeat these steps for: "kommonitor-client-config", "kommonitor-importer", "kommonitor-processing-engine", 
    "kommonitor-processing-scheduler" and "kommonitor-web-client"

#### 11) Adapt Docker Compose setup
Adapt your Docker Compose setup for using the new KomMonitor component versions. This includes using our 
custom Keycloak image, updating the image versions of the Data Management API, the Importer API
and the Web Client and changing some environment variables
##### 11.1) Keycloak Setup
Check the [Docker Compose template](https://github.com/KomMonitor/docker/blob/master/prod/keycloak/docker-compose.yml) for setting up a production ready Keycloak instance.

Besides the Keycloak related configuration parameters, you'll find the `KOMMONITOR_REALMS` environment variable, which is dedicated to
our custom Keycloak image. For this parameter set all Keycloak realms as comma separated list, which should use the multi-tenancy feature.

##### 11.2) KomMonitor Setup
There is also a [Docker Compose templates](https://github.com/KomMonitor/docker/blob/master/prod/kommonitor/docker-compose.yml)
that provides a production ready configurations for all KomMonitor components. 

For the first startup after having your DB migrated, you have to enable the migration startup script by setting
the following environment variables to your Data Management API container in the `docker-compose.yml` file:
* `KOMMONITOR_MIGRATION_ENABLED=true`
* `KOMMONITOR_MIGRATION_VERSIONS=5.0.0`

This will execute some initial update routines at startup e.g., to initially create Keycloak groups
for all your extsing organizational units. There are also two optional config params, which control
the deletion of some deprecated legacy OrganizationalUnits and set to `true` by default:
* `KOMMONITOR_MIGRATION_DELETE_LEGACY_ADMIN_ORGANIZATIONALUNIT=true`: deletes the default "kommonitor" OrganizationalUnit and all of its associated permissions
* `KOMMONITOR_MIGRATION_DELETE_LEGACY_PUBLIC_ORGANIZATIONALUNIT=true`: deletes the deafault "public"  OrganizationalUnit and all of its associated permissions

E.g., if you have associated the `kommonitor` OrganizationalUnit as owner for some datasets (which is not recommended),
you can set `KOMMONITOR_MIGRATION_DELETE_LEGACY_ADMIN_ORGANIZATIONALUNIT` to `false` in order to preserve the 
`kommonitor ` OrganizationalUnit.


Note: After successfull startup, set `KOMMONITOR_MIGRATION_ENABLED` to `false` again, to prevent another migration routine
execution at next startup.


## Common Errors and Pitfalls
**Access denied exception during Liquibase changelog generation**  
You may run into an access denied error or some similiar when executing the `liquibase generate-changelog` command. Most probably,
the reason for this is that you mounted a data directory into the Liquibase Docker container, which is not writable from within the
container. Just adapt the permissions of this directory on your host machine with `chmod` before mounting it as volume.

**Unexpected error during Liquibase update**  
In some cases, the command `liquibase update` will fail with an unexpected error. This may be caused by strings within the CSV-files
that contain special characters. In particular, the `processdescription` column within `metadataindicators.csv` may contain problematic 
Latex formulars, such as `Formel<br/>$$ \frac{ A}{ I_{ref}} \times 100`. Replace these strings by an unproblematic string. After
succesfull migration you can set the original string again via KomMonitor Admin UI.

**401 error occurs during DataManagament API startup**  
Check if you have set the Keycloak admin-cli secret properly to `KK_CLI_SECRET` as mentioned in [this section](#102-configure-admin-cli).

**403 error occurs during DataManagament API startup**  
Check in Keycloak that the `kommonitor-creator` role is associated with the `realm-management` or `realm-admin` role.

