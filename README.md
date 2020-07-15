# Java Spring Basics

A boilerplate reference project on Java Spring web server, with persistent data storage in PostgreSQL

Inspired by [this](https://www.youtube.com/watch?v=r-6BwGW4Sr8) YouTube tutorial by [AmigosCode](https://amigoscode.com/)

## Run/Build Locally

With Maven, run `maven clean install` followed by `maven spring-boot:run`

## Database Setup

```bash
docker run --name postgres-spring -e POSTGRES_PASSWORD=password -d -p 5432:5432 postgres:alpine # run postgres database in container
docker exec -it <container id> bin/bash # activate bash
psql -U <database username> # connect to postgres database
CREATE DATABASE demodb; # create database with name demodb
\c demodb # connect to demodb
\dt # view data tables
```

Then, run `main()` to trigger migrations. Afterwards, run the following:
```bash
\d person # view person table
CREATE EXTENSION "uuid-ossp"; # add uuid extension
SELECT uuid_generate_v4(); # confrim uuid extension works
INSERT INTO person (id, name) VALUES (uuid_generate_v4(), 'John Doe'); # insert new person
SELECT * FROM person; # confirm new person is added
```

## Usage  

- Once app is running, make a POST request to `http://localhost:8080/api/v1/person` to get user details


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)



