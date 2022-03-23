---
title: Docker QA
description: 
published: true
date: 2022-03-23T16:46:04.077Z
tags: docker, backend, interviewing
editor: markdown
---

# What is docker?
- Docker is a containerization platform which packages your application and all its dependencies together in the form of containers so as to ensure that your application works seamlessly in any environment be it development or test or production.
- Docker containers, wrap a piece of software in a complete filesystem that contains everything needed to run: code, runtime, system tools, system libraries etc. anything that can be installed on a server.
- This guarantees that the software will always run the same, regardless of its environment.

# How to link containers?
Use network port mapping

# What is the difference between docker run and docker create?
`docker create` creates a container in a stopped satte.

# What type of applications - Stateless or Stateful, are more suitable for dockerization?
It is preferable to create Stateless application for Docker Container. 

We can create a container out of our application and take out the configurable state parameters from application. 

Now we can run same container in Production as well as QA environments with different parameters. This helps in reusing the same Image in different scenarios. Also a stateless application is much easier to scale with Docker Containers than a stateful application.

# What is a Docker image?
Docker image is the source of Docker container. 

In other words, Docker images are used to create containers. 

Images are created with the build command, and they’ll produce a container when started with run. 

Images are stored in a Docker registry such as `registry.hub.docker.com`. 

Because they can become quite large, images are designed to be composed of layers of other images, allowing a minimal amount of data to be sent when transferring images over the network.

# What is a Docker container?
Docker containers include the application and all of its dependencies, but share the kernel with other containers, running as isolated processes in user space on the host operating system. Docker containers are not tied to any specific infrastructure: they run on any computer, on any infrastructure, and in any cloud.