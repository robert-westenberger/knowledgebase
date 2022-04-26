---
title: Management Scripts in Docker
description: 
published: true
date: 2022-04-26T16:50:59.488Z
tags: docker
editor: markdown
---

# Writing Management Scripts in Docker
Managing a multi-container project along with network and volumes means writing a lot of commands. To simplify, we can use shell scripts and a Makefile.

## Examples
Examples below utilize two pretend containers, "notes-api" and "notes-db".
### `boot.sh`
Used for starting containers if they already exist.
```
#!/bin/bash
set -e

API_CONTAINER_NAME="notes-api"
DB_CONTAINER_NAME="notes-db"

if docker container ls --all | grep -q $DB_CONTAINER_NAME;
then
  printf "starting db container --->\n"
  docker container start $DB_CONTAINER_NAME;
  printf "db container started --->\n"
else
  printf "db container not found --->\n"
fi

printf "\n"

if docker container ls --all | grep -q $API_CONTAINER_NAME;
then
  printf "starting api container --->\n"
  docker container start $API_CONTAINER_NAME;
  printf "api container started --->\n"
else
  printf "api container not found --->\n"
fi

printf "\n"

printf "boot script finished\n\n"
```
### `build.sh`
Creates and runs the containers. It also creates the images, volumes, and networks if necessary.
```
#!/bin/bash
set -e

NETWORK_NAME="notes-api-network"
DB_CONTAINER_VOLUME_NAME="notes-db-data"
API_IMAGE_NAME="notes-api"
API_CONTAINER_NAME="notes-api"
DB_CONTAINER_NAME="notes-db"

DB_NAME="notesdb"
DB_PASSWORD="secret"

if docker network ls | grep -q $NETWORK_NAME;
then
  printf "network found --->\n"
else
  printf "creating network --->\n"
  docker network create $NETWORK_NAME;
  printf "network created --->\n"
fi

printf "\n"

if docker volume ls | grep -q $DB_CONTAINER_VOLUME_NAME;
then
  printf "volume found --->\n"
else
  printf "creating volume --->\n"
  docker volume create $DB_CONTAINER_VOLUME_NAME;
  printf "volume created --->\n"
fi

printf "\n"

printf "starting db container --->\n"
if docker container ls --all | grep -q $DB_CONTAINER_NAME;
then
  docker container start $DB_CONTAINER_NAME
else
  docker container run \
    --detach \
    --volume $DB_CONTAINER_VOLUME_NAME:/var/lib/postgresql/data \
    --name=$DB_CONTAINER_NAME \
    --env POSTGRES_DB=$DB_NAME \
    --env POSTGRES_PASSWORD=$DB_PASSWORD \
    --network=$NETWORK_NAME \
    postgres:12;
fi
printf "db container started --->\n"

printf "\n"

cd api;
printf "creating api image --->\n"
docker image build . --tag $API_IMAGE_NAME;
printf "api image created --->\n"
printf "starting api container --->\n"
if docker container ls --all | grep -q $API_CONTAINER_NAME;
then
  docker container start $API_CONTAINER_NAME
else
  docker container run \
      --detach \
      --name=$API_CONTAINER_NAME \
      --env DB_HOST=$DB_CONTAINER_NAME \
      --env DB_DATABASE=$DB_NAME \
      --env DB_PASSWORD=$DB_PASSWORD \
      --publish=3000:3000 \
      --network=$NETWORK_NAME \
      $API_IMAGE_NAME;
  docker container exec $API_CONTAINER_NAME npm run db:migrate;
fi
printf "api container started --->\n"

cd ..
printf "\n"

printf "build script finished\n\n"
```
### `destroy.sh`
Removes all containers, volumes and networks associated with this project.
```
#!/bin/bash
set -e

NETWORK_NAME="notes-api-network"
DB_CONTAINER_VOLUME_NAME="notes-db-data"
API_CONTAINER_NAME="notes-api"
DB_CONTAINER_NAME="notes-db"

if docker container ls --all | grep -q $API_CONTAINER_NAME;
then
  printf "removing api container --->\n"
  docker container rm $API_CONTAINER_NAME;
  printf "api container removed --->\n"
else
  printf "api container not found --->\n"
fi

printf "\n"

if docker container ls --all | grep -q $DB_CONTAINER_NAME;
then
  printf "removing db container --->\n"
  docker container rm $DB_CONTAINER_NAME;
  printf "db container removed --->\n"
else
  printf "db container not found --->\n"
fi

printf "\n"

if docker volume ls | grep -q $DB_CONTAINER_VOLUME_NAME;
then
  printf "removing db data volume --->\n"
  docker volume rm $DB_CONTAINER_VOLUME_NAME;
  printf "db data volume removed --->\n"
else
  printf "db data volume not found --->\n"
fi

printf "\n"

if docker network ls | grep -q $NETWORK_NAME;
then
  printf "removing network --->\n"
  docker network rm $NETWORK_NAME;
  printf "network removed --->\n"
else
  printf "network not found --->\n"
fi

printf "\n"

printf "destroy script finished\n\n"
```
### `shutdown.sh`
Stops all running containers
```
#!/bin/bash
set -e

API_CONTAINER_NAME="notes-api"
DB_CONTAINER_NAME="notes-db"

if docker container ls | grep -q $API_CONTAINER_NAME;
then
  printf "stopping api container --->\n"
  docker container stop $API_CONTAINER_NAME;
  printf "api container stopped --->\n"
else
  printf "api container not found --->\n"
fi

printf "\n"

if docker container ls | grep -q $DB_CONTAINER_NAME;
then
  printf "stopping db container --->\n"
  docker container stop $DB_CONTAINER_NAME;
  printf "db container stopped --->\n"
else
  printf "db container not found --->\n"
fi

printf "\n"

printf "shutdown script finished\n\n"
```