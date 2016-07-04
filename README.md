# Dockerized Flyway

Example (see `test` directory):

```
$ cd test

$ docker-compose up -d postgres
Creating network "test_default" with the default driver
Creating test_postgres_1

$ docker-compose run flyway flyway migrate
Flyway 4.0.1 by Boxfuse
Database: jdbc:postgresql://postgres:5432/postgres (PostgreSQL 9.5)
Successfully validated 1 migration (execution time 00:00.010s)
Creating Metadata table: "public"."schema_version"
Current version of schema "public": << Empty Schema >>
Migrating schema "public" to version 1 - create person table
Successfully applied 1 migration to schema "public" (execution time 00:00.081s).

$ docker-compose run flyway flyway info
Flyway 4.0.1 by Boxfuse

Database: jdbc:postgresql://postgres:5432/postgres (PostgreSQL 9.5)

+---------+---------------------+---------------------+---------+
| Version | Description         | Installed on        | State   |
+---------+---------------------+---------------------+---------+
| 1       | create person table | 2016-07-04 14:42:51 | Success |
+---------+---------------------+---------------------+---------+

$ docker-compose run postgres psql -h postgres -p 5432 -U postgres postgres -c "\dt"
             List of relations
 Schema |      Name      | Type  |  Owner
--------+----------------+-------+----------
 public | person         | table | postgres
 public | schema_version | table | postgres
(2 rows)
```

# Reference

https://flywaydb.org/getstarted/firststeps/commandline
