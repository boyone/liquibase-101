# Tag

- [`tag`](https://docs.liquibase.com/commands/utility/tag.html): used to mark the current database state, version, release, or any other information by adding the tag to the last row in the `DATABASECHANGELOG` table.

---

## In Action

1. init

   ```sh
   liquibase init project
   ```

2. Run `update` command

   ```sh
   liquibase update --changelog-file=example-changelog.sql
   ```

3. Run `tag` command

   ```sh
   liquibase tag version_1
   ```

4. Add `ChangeSet` to `ChangeLog`

   ```sql
   -- changeset boyone:4
   create table customer (id int not null, name varchar(50), age int, lastname varchar(50), "year" int not null, constraint constraint_5 primary key (id));
   --rollback DROP TABLE company;
   ```

5. Run `rollback` command

   ```sh
   liquibase rollback version_1
   ```

---

## Tag Database

- [`tagDatabase`](https://docs.liquibase.com/change-types/tag-database.html):

  ```yaml
  changes:
    - tagDatabase:
        - tag: version_1
  ```

1. init project with `yaml`

   ```sh
   liquibase init project
   ```

2. Add `tagDatabase` to `changeSet id 3`

   ```yaml
   - tagDatabase:
       - tag: version_1
   ```

3. Run `update` command

   ```sh
   liquibase update --changelog-file=example-changelog.yaml
   ```

4. Add `ChangeSet` to `ChangeLog`

   ```yaml
   - changeSet:
       id: 4
       author: demo
       changes:
         - createTable:
             columns:
               - column:
                   constraints:
                     nullable: false
                     primaryKey: true
                   name: id
                   type: int
               - column:
                   name: name
                   type: varchar(50)
               - column:
                   name: age
                   type: int
               - column:
                   name: lastname
                   type: varchar(50)
               - column:
                   constraints:
                     nullable: false
                   name: year
                   type: int
             tableName: customer
   ```

5. Run `rollback` command

   ```sh
   liquibase rollback version_1
   ```

6. Add `tagDatabase` to `changeSet id 4`

   ```yaml
   - tagDatabase:
       - tag: version_2
   ```

7. Run `drop-all` command

    ```sh
    liquibase drop-all
    ```

8. Run `update-to-tag` command

    ```sh
    liquibase update-to-tag --tag version_1 --changelog-file example-changelog.yaml
    ```