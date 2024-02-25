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

The "shell" can be started via `docker exec` into container. Convenience aliases are defined to make this easier:

Interactive mode:

```shell
hbase-shell
```

General purpose bash _inside_ the container, e.g run a script file in non-interactive shell:

```shell
hbash "cat /workspace/lab/hbase/script.rb | hbase shell -n"
```

(Note that the repo root's `lab/` directory is mounted at `/workspace/lab/` inside the container)

