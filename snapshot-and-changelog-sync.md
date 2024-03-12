# Snapshot and Changelog Sync

- [`snapshot`](https://docs.liquibase.com/commands/inspection/snapshot.html): captures the current state of the url database, which is the target database.
- Support Format only `JSON` or `YAML`
- [`changelog-sync`](https://docs.liquibase.com/commands/utility/changelog-sync.html): is typically used when you want to baseline a new database environment.
- [`diff-changelig`](https://docs.liquibase.com/commands/inspection/diff-changelog.html): command displays the differences between two databases you are comparing. It also generates a changelog file containing deployable changesets to resolve most of these differences.
- [`include`](https://docs.liquibase.com/change-types/include.html): use the include tag in the root changelog to reference other changelogs.

---

## In Action

1. init project with `yaml`

   ```sh
   liquibase init project
   ```

2. Run `update` command

   ```sh
   liquibase update --changelog-file=example-changelog.yaml
   ```

3. Run `snapshot` command

   ```sh
   liquibase --outputFile=example-snapshot.yaml snapshot --snapshotFormat=yaml
   ```

4. Add a new table

   ```sql
   CREATE TABLE CUSTOMER (
       ID INT PRIMARY KEY,
       NAME VARCHAR(50) DEFAULT NOT NULL,
       AGE INT,
       LASTNAME VARCHAR(50) DEFAULT NOT NULL,
       `YEAR` INT NOT NULL
   );
   ```

5. Run `diffChangeLog` command

   ```sh
   liquibase --referenceUrl=jdbc:h2:tcp://localhost:9090/mem:dev --url="offline:h2?snapshot=example-snapshot.yaml" diffChangeLog --changeLogFile=example-changelog2.yaml
   ```

   ```sh
   liquibase --referenceUrl=jdbc:h2:tcp://localhost:9090/mem:dev --url="offline:h2?snapshot=example-snapshot.yaml" diff
   ```

   > liquibase history

6. Run `changelog-sync` command

   ```sh
   liquibase changelog-sync --changelog-file example-changelog2.yaml
   ```

   > liquibase history

7. Run `drop-all` command

   ```sh
   liquibase drop-all
   ```

8. Add `include` tag to ChangeLog file

   ```yaml
   databaseChangeLog:
     - include:
         file: example-changelog.yaml
   ```

9. Run `update` command

   ```sh
   liquibase update --changelog-file example-changelog2.yaml
   ```
