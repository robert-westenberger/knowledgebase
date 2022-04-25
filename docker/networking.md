---
title: Networking
description: 
published: true
date: 2022-04-25T03:33:19.848Z
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
### Host 
Removes the network isolation completely. Any container running under a `host` network is basically attached to the network of the host system.
### None
This driver disables networking for containers altogether.
### Overlay
Used for connecting multiple Docker daemons across computers.
### Macvlan
Allows assignment of MAC addresses to containers, making them function like physical devices in a network.
## List networks
`docker network ls`
# User-Defined Bridge Network
Docker comes with a default bridge network named `bridge`. Any container you run will be automatically attached to this bridge network. 
## Extra Features of User-Defined Bridge Networks
### Provide automatic DNS resolution between containers
Containers attached to the same network can communicate with each other using the container name. If you have two containers named `api` and `db`, the API container will be able to connect to the database container using the `db` name. 
### Provide better isolation
All containers are attached to the default bridge network by default which can cause conflicts among them. Attaching containers to a user-defined bridge can ensure better isolation. 
### Containers can be attached and detached from user-defined networks on the fly
During a container’s lifetime, you can connect or disconnect it from user-defined networks on the fly. To remove a container from the default bridge network, you need to stop the container and recreate it with different network options.
## Creating a User-Defined Bridge Network
`docker network create <network name>`
## Attach a Container to a Network in Docker
# Attach a Container to a Network
# Detach Containers From a Network
# Get Rid of Networks 