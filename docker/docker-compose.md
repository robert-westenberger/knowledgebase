---
title: Docker Compose
description: 
published: true
date: 2022-04-27T15:04:10.806Z
tags: docker
editor: markdown
---

# Overview
Docker Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services. Then with a single command, you create and start all ther services from your configuration.

## Execute Commands Inside a Running Service in Docker Compose
Just like `container exec`, there is an `exec` command for `docker-compose`. 

`docker-compose exec <service name> <command>`

Unlike `container exec`, you don't need to pass the `-it` flag, `docker-compose` will pass it automatically.