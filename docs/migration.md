# Migration Guide
## Migration to Version 5.0.0
### From 4.x.x
#### 1) Create current DB state
First, capture the current state of those DB tabled that have to be manually enhanced with additional 
values. In particular, these are the tables `indicatorspatialunits`, `metadatageoresources`,
`metadataindicators`, `metadataspatialunits`, `organizationalunits`, `permissions`. For this purpose,
you have to generate a changelog with the Liquibase [generate-changelog](https://docs.liquibase.com/commands/inspection/generate-changelog.html)
command that includes `data` in the `--diff-types` parameter. 

You can use the template listed below for this purpose. Just adapt the parameters to your environment.
Note, that the Liquibase Docker container must have access to your KomMonitor database and to the mounted data directories:

```
docker run --network=kommonitor \
-v /home/user/kommonitor/liquibase/changelog:/liquibase/changelog \
-v /home/user/kommonitor/liquibase/data:/liquibase/data_output \
liquibase generate-changelog \
--changelog-file=changelog/kommonitor-changelog-data-4.0.0.xml \
--diffTypes=data \
--include-objects="indicatorspatialunits,metadatageoresources,metadataindicators,metadataspatialunits,organizationalunits,permissions" \
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
TBD

#### 9) Sync DB to inital 5.0.0 schema
TBD