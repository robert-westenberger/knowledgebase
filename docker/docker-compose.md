---
title: Docker Compose
description: 
published: true
date: 2022-04-27T15:08:05.547Z
tags: docker
editor: markdown
---

# Overview
Docker Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services. Then with a single command, you create and start all ther services from your configuration.

# Execute Commands Inside a Running Service in Docker Compose
Just like `container exec`, there is an `exec` command for `docker-compose`. 

`docker-compose exec <service name> <command>`

Unlike `container exec`, you don't need to pass the `-it` flag, `docker-compose` will pass it automatically.

# Access Logs
`docker-compose logs <service name>`

# Stop Services in Docker Compose
## Using the `down` command
`docker-compose down --volumes`
Stops all running containers and removes them from the system. It also removes any networks. 

The `--volumes` option indicates that you want to remove any named volumes defined in the `volumes` block. 
## Using the `stop` command
Functions identically to `container stop` command. It stops all the containers for the application and keeps them. 
