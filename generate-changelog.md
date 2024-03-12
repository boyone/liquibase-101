# Generate Changelog

- [generateChangeLog](https://docs.liquibase.com/commands/inspection/generate-changelog.html): creates a changelog file that has a sequence of changesets which describe how to re-create the current state of the database.

---

## In Action

1. Run `generate-changelog` with default `--diff-types`

   ```sh
   liquibase generate-changelog --changelog-file example-changelog.yaml
   ```

2. Run `generate-changelog` with default `--diff-types=data`

   ```sh
   liquibase generate-changelog --changelog-file example-changelog.yaml --data-output-directory=data --diff-types=data
   ```

3. Run `generate-changelog` with specific `--diff-types`

   ```sh
   liquibase generate-changelog --changelog-file example-changelog.yaml --data-output-directory=data --diff-types=columns,data,foreignkeys,indexes,primarykeys,tables,uniqueconstraints,views
   ```

4. Run `generate-changelog` with all `--diff-types`

   ```sh
   liquibase generate-changelog --changelog-file example-changelog.yaml --data-output-directory=data --diff-types=catalogs,checkconstraints,columns,data,databasepackage,databasepackagebody,foreignkeys,functions,indexes,primarykeys,sequences,storedprocedures,triggers,uniqueconstraints,views
   ```


