# PostgreSQL

## 🖥Commands🖥

### Connect to postgreSQL

```bash
psql -h <host> -U <user>
```

### Exit postgreSQL

```
\q
```

### List databases

```
\l
```

### Create database

```SQL
CREATE DATABASE <database>;
```

### Delete database

```SQL
DROP DATABASE <database>;
```

### Export database

#### Export one database

```bash
pg_dump -U <user> -W -F t <database> > <database-file>
```

#### Export all databases

Also exports roles and permissions so it's good for data recovery, can be VERY large file

```bash
pg_dumpall -U <user> -W > <databasefile.sql
```
### Import database

#### For .sql files

```bash
psql -U <user> -W -d <database-name> -f <database-file>
```

#### For other formats

You can be more selective on what to include in the database file.

```bash
pg_restore -U <user> -d <database> <database-export-file>
```
### Get database location

```SQL
SHOW data_directory;
```

### Create user

```SQL
CREATE USER <user> WITH ENCRYPTED PASSWORD '<password>';
```

### Change user password

```SQL
ALTER ROLE <user> WITH ENCRYPTED PASSWORD '<new-password>';
```

### Grant privileges to user

```SQL
GRANT <privileges> privileges ON database <database> TO <user>;
```


