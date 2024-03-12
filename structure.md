# Structure

## Liquibase Structure

```txt
liquibase
         |-ABOUT.txt
         |-changelog.txt
         |-examples/
         |-GETTING_STARTED.txt
         |-internal/
         |-lib/
         |-LICENSE.txt
         |-licenses
         |-liquibase
         |-liquibase.bat
         |-README.txt
         |-UNINSTALL.txt
```

## Project Structure

1. Liquibase properties file

   ```properties
   url=jdbc:h2:tcp://localhost:9090/mem:dev
   username: dbuser
   password: letmein
   referenceUsername: dbuser
   referencePassword: letmein
   ```

2. Changelog: XML, YAML, JSON, SQL

   - XML example

     ```sh
     example.changelog.xml
     ```

   - YAML example

     ```sh
     example.changelog.yaml
     ```

   - JSON example

     ```sh
     example.changelog.json
     ```

   - SQL example

     ```sh
     example.changelog.sql
     ```
