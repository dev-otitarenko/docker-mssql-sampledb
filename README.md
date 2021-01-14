# Sample database for examples

This is the docker image with MS SQL database for mostly all my samples. You can find script for creation all tables [here](https://github.com/dev-otitarenko/docker-mssql-sampledb/blob/main/db/init.sql) 

# Checking parameters

Before running the docker container with DB, please change parameters **(SA_PASSWORD, ports, container_name)** in [docker-compose.yml](https://github.com/dev-otitarenko/docker-mssql-sampledb/blob/main/docker-compose.yml) suitable for you:
```sh
version: '2'
services:
  db:
    build: db
    image: mcmoe/mssqldocker
    restart: always
    environment:
      ACCEPT_EULA: Y
      SA_PASSWORD: <your password>
    ports:
      - 1433:1433
    container_name: <name for container with sample db>
    volumes:
      - ./docker/samples-db/data:/var/opt/mssql
```

# Running container

```sh
docker-compose -f ./docker-compose.yml build
docker-compose -f ./docker-compose.yml up -d
```

If you have some issues with the container, please check log or run using following command
```sh
docker-compose -f ./docker-compose.yml up
```

# Checking container

```sh
docker stats
```

Happy coding
