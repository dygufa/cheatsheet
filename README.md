# Cheatsheet

## Contents

- [Postgres](#postgres)
- [MongoDB](#mongodb)

## Postgres

### psql (PostgreSQL interactive terminal)

#### Starting psql
`psql -U postgres`

- h - Host
- p - Port
- U - User

#### Comandos dentro do psql
- \q - Quit
- \l - Returns database list
- \c <db> - Connects to the specified database
- \d - Returns table list from the current connected database
- `CREATE ROLE username WITH LOGIN PASSWORD 'password';` - Creates an user
- `DROP USER username;` - Deletes an user
- `CREATE DATABASE db` - Creates a database
- `GRANT ALL PRIVILEGES ON DATABASE db TO username;` - Grants all privileges to an user

### Backup 

Backing up one database using docker [postgres-backup-s3](https://github.com/schickling/dockerfiles/tree/master/postgres-backup-s3) image:

```
docker run --rm --network <network> \
    -e S3_ACCESS_KEY_ID=<S3_ACCESS_KEY_ID> \
    -e S3_SECRET_ACCESS_KEY=<S3_SECRET_ACCESS_KEY> \
    -e S3_BUCKET=<S3_BUCKET> \
    -e S3_PREFIX=<S3_PREFIX> \
    -e POSTGRES_DATABASE=<POSTGRES_DATABASE> \
    -e POSTGRES_USER=<POSTGRES_USER> \
    -e POSTGRES_PASSWORD=<POSTGRES_PASSWORD> \
    -e POSTGRES_HOST=<POSTGRES_HOST> \
    -e POSTGRES_PORT=<POSTGRES_PORT> \
    schickling/postgres-backup-s3
```

## MongoDB

### mongo 

- show dbs - List all dbs
- use <DB> - Set DB for use and create the DB if it doesn't already exist 
- show collections - List all collections for the selected DB
- db.<COLLECTION>.find() - List all entries for a collection

### Backup

Backing up all collections using docker [mongobackup-s3](https://github.com/firstandthird/mongobackup-s3) image:

```
docker run --rm --network <network> \
    --env AWS_ACCESS_KEY_ID=<AWS_ACCESS_KEY_ID> \
    --env AWS_SECRET_ACCESS_KEY=<AWS_SECRET_ACCESS_KEY> \
    --env S3BUCKET=<S3BUCKET> \
    firstandthird/mongobackup-s3
```