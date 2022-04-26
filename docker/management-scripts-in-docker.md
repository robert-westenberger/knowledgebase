---
title: Management Scripts in Docker
description: 
published: true
date: 2022-04-26T16:49:33.783Z
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
