---
title: Docker Architecture
description: 
published: true
date: 2022-04-24T19:08:54.797Z
tags: docker
editor: markdown
---

# Overview
Docker uses a client-server architecture. The Docker **client** talks to the Docker **daemon**, which does the heavy lifting of building, running, and distributing your Docker containers. 

The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon. The Docker client and daemon communicate using a REST API, over UNIX sockest or a network interface. 

Another Docker client is Docker Compose, that lets you work with applications consisting of a set of containers.

## Docker Daemon
The daemon (`dockerd`) is a process that keeps running in the background and waits for commands from the client. The daemon is capable of managing various Docker objects.

## Docker Client
The client (`docker`) is a command-line interface program mostly responsible for transporting commands issued by users. 

## REST API
The REST API acts as a bridge between the daemon and the client. Any command issues using the client passes through the API to finally reach the daemon. 

# The Full Picture
![docker-run-hello-world.svg](/docker-run-hello-world.svg)
Above is a diagram of what happens when `docker run hello-world` is executed. 

1. You execute `docker run hello-world` command, where `hello-world` is the name of an image.

2. Docker reaches out to the daemon, tells it to get the `hello-world` image and run a container from that.

3. Docker daemon looks for the image within your local repository, and realizes that its not there, resulting in the `Unable to find image 'hello-world:latest' locally` that's printed on your terminal.

4. The daemon then reaches out to the default public registry which is Docker Hub and puls in the latest copy of the `hello-world` image, indicated by the `latest: Pulling from library/hello-world` line in your terminal.