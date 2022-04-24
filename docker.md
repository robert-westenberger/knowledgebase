---
title: Docker
description: 
published: true
date: 2022-04-24T18:55:57.481Z
tags: docker
editor: markdown
---

# Advantages
## Portability / Consistency
Once you have tested your containerized application you can deploy it to any other system where Docker is running and you can be sure that your application will perform exactly as it did when you tested it.

A docker container allows an entire team to work in the same way, regardless of server machine or OS. 

## Performance
Although virtual machines are an alternative to containers, the fact that containers do not contain an operating system (whereas virtual machines do) means that containers have much smaller footprints than virtual machines, are faster to create, and quicker to start.

Docker containers are virtually identical in terms of performance in relation to bare metal. 


## Continuous Integration Efficiency
We can build a container image and use the same image over every step of the deployment process. 

The advantage of it is the ability to separate non-dependent steps and also run them in parallel. 

# Disadvantages
## Missing featuers
Container self registration, self-inspects, copying files from the host to the contaienr.
## Data in the container
If a container goes down, it needs a backup and recovery strategy. 
## Mainly used for console / terminal based apps, not GUI
You can still run GUI-based applicaitons developed with python and the QT framework in a linux container. You can also use X11 forwarding, but this is somewhat awkward (why?)
## Persistent data storage is complicated
By design, all of the data inside a container disappears forever when the container shuts down, unless you save it somewhere else first. There are ways to save data persistently in Docker, such as Docker Data Volumes, but this is arguably a challenge that still has yet to be addressed in a seamless way.

# Concepts
## Container
A container is an abstraction at the application layer that packages code and dependencies together. Instead of virtualizing the entire physical machine, containers virtualize the host operating system only. 

They are a lot lighter than traditional virtual machines, so a large number of containers can be run simultaneously without affecting the performance of the host system. 

If you were to, for example, execute `uname -a` in a terminal in both the host operating system and inside a container, you will see both the host OS and the container are using the same kernel.

Containers are just images in a running state.
## Image
Multi-layered self contained files that act as the template for creating containers. They are like a frozen, read-only copy of a container. Images can be exchanged through registries.

## Registry
An image registry is a centralized place where you can upload your images and can also download images created by others. 

[Docker Hub](https://hub.docker.com/) is the default public registry for Docker.

Through the Open Container Initiative, container images are now standardized, so an image built with Docker can be used with another runtime like Podman.

