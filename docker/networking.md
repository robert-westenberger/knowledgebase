---
title: Networking
description: 
published: true
date: 2022-04-25T01:39:52.370Z
tags: docker
editor: markdown
---

# Network Basics
Consider an application that is split across multiple containers. 
It is powered by an Express.js server and a PostgreSQL database in two separate containers.

A network in Docker is another logical object like a container and image. There is a plethora of commands under `docker network` group for manipulating networks.
## Networking Drivers
### Bridge
The default networking driver in Docker. This can be used when multiple containers are running in standard mode and need to communicate with eachother. 
## List networks
`docker network ls`
# Create a User-Defined Bridge
# Attach a Container to a Network
# Detach Containers From a Network
# Get Rid of Networks 