# Liquibase devcontainer

Example of managing database schema in a VSCode project.
For PostgreSQL + Liquibase.

1. Open project in container
2. (pgadmin)[http://localhost:5050]: to view the data in the database.
- Username: dude@secret.io
- Password: supersecret
- Register:
-- Host Name: postgres
-- Database: mydatabase
-- Username: nottheadmin
-- Password: metadata
3. liquibase VSCode terminal: to update database schema via Liquibase

Credentials: ./.devcontainer/.env
Liquibase Properties: ./db/liquibase.properties


## Debug
If Credentials aren't working:
```
docker volume rm $(docker volume ls -q --filter dangling=true)
```