---
title: Docker Architecture
description: 
published: true
date: 2022-04-24T19:01:58.785Z
tags: docker
editor: markdown
---

# Overview
Docker uses a client-server architecture. The Docker **client** talks to the Docker **daemon**, which does the heavy lifting of building, running, and distributing your Docker containers. 

The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon. The Docker client and daemon communicate using a REST API, over UNIX sockest or a network interface. 

Another Docker client is Docker Compose, that lets you work with applications consisting of a set of containers.

# Docker Daemon
The daemon (`dockerd`) is a process that keeps running in the background and waits for commands from the client. The daemon is capable of managing various Docker objects.

# Docker Client
The client (`docker`) is a command-line interface program mostly responsible for transporting commands issued by users. 

# REST API
The REST API acts as a bridge between the daemon and the client. Any command issues using the client passes through the API to finally reach the daemon. 

