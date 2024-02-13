# Lab environment for "Seven Databases in Seven Weeks"

## PostgreSQL

Database runs in separate container, with service name "postgres" (can be resolved has hostname)

Environment variables, e.g. PGUSER and PGPASSWORD, prepared to match defaults for the database server.

### How to access

```shell
psql
```

Or after the `7dbs` database has been created:

```shell
psql -d 7dbs
```

Or just:

```shell
psql 7dbs
```

