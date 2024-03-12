# Postgresql

- [postgresql](https://docs.liquibase.com/start/tutorials/postgresql/postgresql.html)

---

## In Action

1. liquibase.properties for `postgresql`

   ```properties
   url: jdbc:postgresql://<host>:<port>/<dbname>
   username: dbuser
   password: letmein
   referenceUsername: dbuser
   referencePassword: letmein
   ```

2. Change Directory to postgres

   ```sh
   cd postgres
   ```

3. Start with `docker-compose`

   ```sh
   docker compose up -d
   ```

4. Check Database

   1. target demo: go to [http://localhost:8080](http://localhost:8080)

      - System: PostgreSQL
      - Server: target
      - Username: postgres
      - Password: password
      - Database: demo

   2. target demo: go to [http://localhost:8080](http://localhost:8080)
      - System: PostgreSQL
      - Server: reference
      - Username: postgres
      - Password: password
      - Database: demo

5. Run `update` command for `target db`

   ```sh
   liquibase --defaults-file liquibase.properties update --changelog-file example-changelog.yaml
   ```

6. Run `update` command for `reference db`

   ```sh
   liquibase --defaults-file liquibase2.properties update --changelog-file example-changelog2.yaml
   ```

7. Run `diff` command

   ```sh
   liquibase --defaults-file liquibase.properties diff
   ```
