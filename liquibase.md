# Liquibase

## Part I: Basic

1. [Structure](./structure.md)
2. [Basic Command-line](./basic-command-line.md)
3. [Tag](./tag.md)
4. [Snapshot and Changelog Sync](./snapshot-and-changelog-sync.md)
5. [Generate Changelog](./generate-changelog.md)
   - schema
   - data

## Part II

1. [PostgreSQL](https://docs.liquibase.com/start/tutorials/postgresql/postgresql.html)

   ```properties
   url: jdbc:postgresql://<host>:<port>/<dbname>
   username: dbuser
   password: letmein
   referenceUsername: dbuser
   referencePassword: letmein
   ```

   ```sh
   liquibase --defaults-file liquibase.properties
   ```

2. Workflow
   - manage test data(filter with label)
   - too many changelog
