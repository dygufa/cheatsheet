# Cheatsheet

## Postgres

### psql (PostgreSQL interactive terminal)

#### Abrindo psql
`psql -U postgres`

- h - Host
- p - Porta
- U - Define usuário

#### Comandos dentro do psql
- \q - Sair
- \l - Lista os bancos de dados
- \c <db> - Conecta ao banco especificado
- \d - Lista as tabelas do banco selecionado

### Backup 

Backing up database using docker [postgres-backup-s3](https://github.com/schickling/dockerfiles/tree/master/postgres-backup-s3) image:

```
docker run --rm --network <container-network> \
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