# Migration Guide
## Migration to Data Management API Version 5.0.0
This guide gives you some step-by-step information to perform a major update of KomMonitor Data Management API
from any version below the latest 5.0.0 version. The 5.0.0 Data Management API version introduces a completely new mandant concept, which requires the migration of the existing KomMonitor database schema. If you plan set up a
fresh instance of KomMonitor, you are fine and don't have to perform any migration steps. Otherwise, you
can use the instructions listed below, which supports you to perform the migration by the use of 
[Liquibase](https://docs.liquibase.com/home.html).

**Important: Make sure you have created a proper backup of your database, which can be used for
restoring the current state of the database, if the migration process fails.**
### From 4.x.x
This section captures the migration steps that are required to update from any version 4.x.x 
of the Data Management API to version 5.0.0.
#### 1) Capture current DB state
First, capture the current state of those tables of your KomMonitor DB that have to be manually enhanced
with additional values. In particular, these are the tables `indicatorspatialunits`, `metadatageoresources`,
`metadataindicators`, `metadataspatialunits`, `organizationalunits`, `permissions`. For this purpose,
you have to generate a changelog with the Liquibase [generate-changelog](https://docs.liquibase.com/commands/inspection/generate-changelog.html)
command that includes `data` in the `--diff-types` parameter. 

You can use the template listed below for this purpose. Just adapt the parameters to your environment.
Note, that the Liquibase Docker container must have access to your KomMonitor database and to the mounted data directories. 
It may be required to adapt the permissions of the mounted data directories so that the Liquibase Docker container is able to
write to these directories.:

```Shell
docker run --network=kommonitor \
-v /home/user/kommonitor/liquibase/changelog:/liquibase/db/changelog \
-v /home/user/kommonitor/liquibase/data:/liquibase/data_output \
liquibase generate-changelog \
--changelog-file=db/changelog/kommonitor-changelog-data-4.0.0.xml \
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

#### 2) Adapt permission data
Edit the `roles.csv` file with a tool that lets you easily handle tabular data.
1. Rename the CSV file `roles.csv` to `permissions.csv`
2. Rename the column `roleid` to `permissionid`
3. Add a new column `permissiontype`
4. Fill each cell for the column `permissiontype` with the value `resources`

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
Now, with the adapted CSV files, you can perform the update of your KomMonitor DB to the new schema
of version 5.0.0. For this purpose, you can simply use a [prepared Liquibase changelog](https://github.com/KomMonitor/db-schema-migration/blob/develop/changelog/kommonitor-changelog-4.x-5.0.0.xml).
Download this file and place it at `/home/user/kommonitor/liquibase/changelog`. Make also sure that you 
have placed your CSV files at `/home/user/kommonitor/liquibase/data`. The command listed below performs
the database update by using the [Liquibase update command](https://docs.liquibase.com/change-types/update.html).
Just adapt it to your environment and execute the command.
```Shell
docker run --network=kommonitor \
-v /home/user/kommonitor/liquibase/changelog:/liquibase/db/changelog \
-v /home/user/kommonitor/liquibase/data:/liquibase/data_input \
liquibase update \
--changelog-file=db/changelog/kommonitor-changelog-4.x-5.0.0.xml \
--driver=org.postgresql.Driver \
--url="jdbc:postgresql://kommonitor-db:5432/kommonitor_data" \
--username=kommonitor \
--password=kommonitor 
```
This will apply all changesets to your database to update its schema and also loads the missing data, which
you have prepared in the CSV files, into the tables.

#### 9) Sync DB to inital 5.0.0 schema
With Data Management API version 5.0.0 we integrated Liquibase as fixed part to perform all future migration tasks.
This requires to baseline your migrated database to the 5.0.0 schema. As a result, when you first start the Data
Management API in version 5.0.0, Liquibase automatically recognizes that your database has been migrated to the
new schema and won't apply any changesets to it, which usually would be done if you start with a clean environment.
For this purpose, you can use the [Liquibase changelog-sync command](https://docs.liquibase.com/commands/utility/changelog-sync.html)
as stated in the snippet below. Download the [5.0.0 base changelog](https://github.com/KomMonitor/data-management/blob/0e0bf6122457b3cee9d7d1b1cc59e1e21aa093b8/src/main/resources/db/changelog/kommonitor-changelog-5.0.0.xml)
and place it into the `/home/user/kommonitor/liquibase/changelog` directory. Again, adapt the command to your
environment before execution.
```Shell
docker run --network=kommonitor \
-v /home/user/kommonitor/liquibase/changelog:/liquibase/db/changelog \
liquibase changelog-sync \
--changelog-file=db/changelog/kommonitor-changelog-5.0.0.xml \
--driver=org.postgresql.Driver \
--url="jdbc:postgresql://kommonitor-db:5432/kommonitor" \
--username=postgres \
--password=postgres

```

#### 10) Adapt Docker Compose setup
Adapt your Docker Compose setup for using the new KomMonitor component versions. This includes using our 
custom Keycloak image, updating the image versions of the Data Management API, the Importer API
and the Web Client and changing some environment variables. Our [Docker Compose templates](https://github.com/KomMonitor/docker/blob/feature/multi-tenancy/prod/kommonitor/docker-compose.yml)
provide working configurations. 

For the first startup after having your DB migrated, you have to add the environment variable 
`KOMMONITOR_MIGRATIONS=5.0.0` to your Data Management API container in the `docker-compose.yml` file.
This will execute some initial update routines at startup e.g., to initially create Keycloak groups
for all your extsing organizational units. After successfull startup, delete this environment variable from your 
`docker-compose.yml` again.