# Working with Liquibase Docker

- [liquibase docker](https://docs.liquibase.com/workflows/liquibase-community/using-liquibase-and-docker.html)
- [liquibase docker hub](https://hub.docker.com/r/liquibase/liquibase)

---

## In Action

1. Init liquibase project
2. Set `liquibase.properties` `url` to postgresql db

   ```properties
   liquibase.command.url=jdbc:postgresql://db:5432/demo
   ```

3. Create `docker-compose.yaml`

   ```yaml
   version: '3.9'

   services:
   db:
     image: postgres:16.2-alpine3.19
     container_name: db
     environment:
       - POSTGRES_PASSWORD=password
       - POSTGRES_USER=postgres
       - POSTGRES_DB=demo
     restart: always
     healthcheck:
     test: ['CMD-SHELL', 'pg_isready -U postgres -d demo']
     interval: 2s
     timeout: 10s
     retries: 5
     networks:
       - demo

   liquibase:
     image: liquibase/liquibase:4.26.0-alpine
     container_name: liquibase
     depends_on:
     db:
       condition: service_healthy
     networks:
       - demo

   adminer:
     image: adminer
     restart: always
     depends_on:
     db:
       condition: service_healthy
     ports:
       - 8080:8080
     networks:
       - demo

   networks:
   demo:
     name: demo
   ```

4. Set liquibase service's `volumes`

   ```yaml
   volumes:
     - ./:/liquibase/changelog/
   ```

5. Set liquibase service's `command`

   ```yaml
   command: --defaults-file=changelog/liquibase.properties update --changelog-file=changelog/example-changelog.yaml
   ```

6. Start docker-compose

   ```sh
   docker compose up -d
   ```

7. Check result: go to [http://localhost:8080](http://localhost:8080)

   - System: PostgreSQL
   - Server: db
   - Username: postgres
   - Password: password
   - Database: demo
