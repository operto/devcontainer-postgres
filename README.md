# DevContainer + PostgreSQL
Example of managing PostgreSQL in a VSCode project.
- [VSCode](https://code.visualstudio.com/) [DevContainer](https://code.visualstudio.com/docs/devcontainers/containers)
- [Postgres](https://www.postgresql.org/)
- [PGAdmin](https://www.pgadmin.org/)
- [Liquibase](https://www.liquibase.org/)

## Overview
- This project is to show you how to run a local development environment across teams that leverage PostgreSQL as the database. While developing and testing software you will need to ensure that databases share a common schema, and can require data to be loaded so that other developers can test software correctly.
- This is a container based solution that allows you not add additional dependancies on a developers machine.
- This example comes with PGAdmin so that engineers can view the database and the data for understanding and debugging.

### How this works
1. .devcontainer
- .env: File that has the configuration for the docker containers
- devcontainer.json: VSCode devcontainer json file which sets up the environment, you will find the docker-compose file, a post startup command which does the 'liquibase update' and the ports that are exposed
- docker-compose.yml: The Docker compose file that loads up all required containers.
2. .db
- liquibase.properties: Contains the credentials that liquibase uses to update the schema
- mydatabase.xml: controls the revision list, and order to apply schema changes
- changelog-***.xml: change log files that manage individual revisions to the database schema
- default-insert-for-admin_config.sql: Data file that is loaded in change-log-5.0.xml; which is related to that specific change
3. Dockerfile: Container that VSCode runs in, this is the terminal with liquibase as a tool.

## How to
1. Open VSCode
2. Open project in container
3. [PGAdmin](http://localhost:5050): to view the data in the database.
- Username: dude@secret.io
- Password: supersecret
4. PGAdmin register database:
- Host Name: postgres
- Database: mydatabase
- Username: nottheadmin
- Password: metadata
5. liquibase VSCode terminal: to update database schema via Liquibase


## Debug
Credentials: ./.devcontainer/.env
Liquibase Properties (credentials must match .env): ./db/liquibase.properties

If you change credentials and they aren't working:
```
docker volume rm $[docker volume ls -q --filter dangling=true]
```