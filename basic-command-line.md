# Basic Command Line

- [init](https://docs.liquibase.com/commands/init/home.html): to help users quickly set up a new Liquibase project, make a copy of an existing project, or quickly start the H2 in-memory database.
- [`update`](https://docs.liquibase.com/commands/update/home.html): deploy changes to the database.
- [`rollback`](https://docs.liquibase.com/commands/rollback/home.html): rollback previously deployed changes.
- [`status`](https://docs.liquibase.com/commands/change-tracking/status.html): states the number of undeployed changesets. Running status lists all undeployed changesets.
- [`history`](https://docs.liquibase.com/commands/change-tracking/history.html): lists all deployed changesets and their deploymentIds.

---

## In Action

1. init

   ```sh
   liquibase init project
   ```

2. start-h2

   ```sh
   liquibase init start-h2
   ```

3. Open file `example-changelog.sql`
4. Run `update` command

   ```sh
   liquibase update --changelog-file=example-changelog.sql
   ```

5. Run `status` command

   ```sh
   liquibase status
   ```

6. Run `history` command

   ```sh
   liquibase history
   ```

7. Run `rollback` command

   ```sh
   liquibase rollback-count --count=1 --changelog-file=example-changelog.sql
   ```

8. Run `status` command

   ```sh
   liquibase status
   ```

9. Run `update` command

   ```sh
   liquibase update --changelog-file=example-changelog.sql
   ```

10. Run `rollback-count` command

    ```sh
    liquibase rollback-count --count=2 --changelog-file=example-changelog.sql
    ```

11. Run `update-count` command

    ```sh
    liquibase update-count --count=1 --changelog-file=example-changelog.sql
    ```

---

## Direct Database Commands

- `drop-all`: use this to drop all objects in your database
- `execute-sql`: use this to run a SQL query or file on your database
- `db-doc`

  ```sh
  liquibase db-doc --output-directory=doc
  ```
