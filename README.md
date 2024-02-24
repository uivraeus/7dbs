# Lab environment for "Seven Databases in Seven Weeks"

## PostgreSQL

Database runs in separate container, with service name "postgres".

Environment variables, e.g. PGUSER and PGPASSWORD, prepared to match defaults for the database server.

### How to access

```shell
psql
```

Or after the `7dbs` database has been created (`createdb 7dbs`):

```shell
psql 7dbs
```

### Extensions from contrib-packages

The [contrib](https://www.postgresql.org/docs/current/contrib.html) content is available in the [postgres container image](https://hub.docker.com/_/postgres) but the extensions must be loaded into the database using [`CREATE EXTENSION`](https://www.postgresql.org/docs/16/sql-createextension.html). So, after connecting to the `7dbs` database, load what you need according to the following example.

```sql
CREATE EXTENSION fuzzystrmatch;
```

## HBase

Running in "standalone mode" in a separate container with service name "hbase"

### How to access

The "shell" can be started via `docker exec` into container. A convenience alias is defined to make this easier:

```shell
hbase-shell
```
