# Manage changesets with `context` and `context-filter`

- [contexts](https://docs.liquibase.com/concepts/changelogs/attributes/contexts.html): are tags that control whether commands like update run certain changesets.

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

3. Add context to Changeset id 2

   ```yaml
   - changeSet:
     id: 2
     author: your.name
     labels: example-label
     context: '@test'
   ```

   The attribute `context: '@test'` causes a changeset to not run if Liquibase runs without any contexts provided.

4. Run `update` command

   ```sh
   liquibase update --changelog-file=example-changelog.sql
   ```

5. Run `history` command

   ```sh
   liquibase history
   ```

6. Run `update` command with `context-filter`

   ```sh
   liquibase update --context-filter=test --changelog-file=example-changelog.sql
   ```

7. Run `history` command

   ```sh
   liquibase history
   ```
