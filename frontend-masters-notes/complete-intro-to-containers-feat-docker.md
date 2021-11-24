---
title: Complete Intro to Containers
description: 
published: true
date: 2021-11-24T22:09:36.982Z
tags: containers, docker
editor: markdown
---

# What Are Containers
## Why Containers
Historically, and in terms of layers of abstraction from the bare metal of a computer, it has gone
Bare Metal -> Virtual Machines -> Public Cloud -> Containers. 

Containers give us many of the security and resource-management features of VMs but without the cost of having to run a whole other operating system. It instead usings `chroot`, `namespace`, and `cgroup` to separate a group of processes from each other.

# chroot
`chroot` is a linux command that allows you to set the root directory of a new process. In the container use case, we just set the root directory to wherever the new container's new root directory should be. This enables a container process to be "jailed" to a particular directory which it cannot see out of. 

# Namespaces
## namespace
`chroot` above only restricts a process to a particular directory, but that process can still other processes. If there are two separate processes `chroot`ed to two different directories, those two different processes could see eachother. 

**Namespaces** allow you to hide processes from other processes.

# cgroups
`cgroups` provide away of allocating resources between different processes. A runaway process taking 100% CPU won't be able to take out other processes with `cgroups`.

# Docker Images With Docker
* Docker images are meant to be spun up and destroyed. They are ephemeral. You should just assume anything in the container will be destroyed.

# Tags
If you run `docker run -it node:latest` for example, `:latest` is the tag. It allows you to run different versions of the same container.


# Alpine Linux
Lightweight, security-oriented linux distro. 

# Features in Docker
## Bind Mounts
Allow you to mount files from your host computer into your container. 

This allows you to use the containers a much more flexible way than previously possible: you don't have to know what files the container will have when you build it and it allows you to determine those files when you run it.


# Reminders
Look more into build stages.