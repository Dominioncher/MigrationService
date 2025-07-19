# MigrationService

This service allow to start sql migration scripts on different databases.

### How to Use
1. Create folder with migration sql scripts.

```
- migrations
  - 1
    - 1.sql
    - 2.sql
    - 3.sql
  - 2
    - 1.sql
    - 2.sql
```
2. Mount this folder to container. Service check migrations in /etc/migrations folder
```
    volumes:
      - ./migrations:/etc/migrations
```

3. Start container

### Environment Variables
- ```DBProvider``` - (```Oracle```) DataBase type connected to
- ```Host``` - DB Host
- ```User``` - DB User
- ```Password``` - DB Password
- ```(optional) Purge``` - (```true/false```) Full clear DB schema before start migrations

### Usage Example:
docker-compose.yml
```
  migrations:
    image: dominioncher/migrationservice
    environment:
        - DBProvider=Oracle
        - Host=localhost:1521/XEPDB1
        - User=test
        - Password=test
    volumes:
      - ./migrations:/etc/migrations
```
