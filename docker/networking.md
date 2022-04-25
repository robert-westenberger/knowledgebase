---
title: Networking
description: 
published: true
date: 2022-04-25T02:01:32.384Z
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
# Create a User-Defined Bridge
Docker comes with a default bridge network named `bridge`. Any container you run will be automatically attached to this bridge network. 
## Extra Features of User-Defined Bridge Networks

# Attach a Container to a Network
# Detach Containers From a Network
# Get Rid of Networks 