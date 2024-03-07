# Lab environment for "Seven Databases in Seven Weeks"

All databases run in separate containers but in the same network namespace as the main dev-container ("app") and can therefore be accessed via localhost.

## PostgreSQL

Database runs in a container named "7dbs_devcontainer-postgres-1".

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

Running in "standalone mode" in a container named "7dbs_devcontainer-hbase-1"

### How to access

The "shell" can be started via `docker exec` into container. Convenience aliases are defined to make this easier:

Interactive mode:

```shell
hbase-shell
```

General purpose bash _inside_ the container, e.g run a script file in non-interactive hbase shell:

```shell
hbase-bash "cat /workspace/lab/hbase/script.rb | hbase shell -n"
```

Or just start an interactive bash shell inside the hbase container:

```shell
hbase-bash bash
```

(Note that the repo root's `lab/` directory is mounted at `/workspace/lab/` inside the container)

## MongoDB

Database runs in a container named "7dbs_devcontainer-mongodb-1".

### How to access

```shell
mongosh
```

Or for a specific database:

```shell
mongosh book
```

The [MongoDB for VS Code](https://www.mongodb.com/products/tools/vs-code) extension is also available for database interaction.
