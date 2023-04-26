# Liquibase devcontainer
Example of managing database schema and data in a VSCode project.
- [VSCode](https://code.visualstudio.com/) (DevContainer)[https://code.visualstudio.com/docs/devcontainers/containers]
- (Postgres)[https://www.postgresql.org/]
- (PGAdmin)[https://www.pgadmin.org/]
- (Liquibase)[https://www.liquibase.org/]

## Overview
The goal of this project is to show you how to run a local development environment across teams that leverage PostgreSQL as the database. While developing and testing software you will need to ensure that databases share a common schema, and can require data to be loaded so that other developers can test software correctly.
This is a container based solution that allows you not add additional dependancies on a developers machine.
This example comes with PGAdmin so that engineers can view the database and the data for understanding and debugging.

## How to

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