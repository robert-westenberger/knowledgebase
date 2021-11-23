---
title: Complete Intro to Containers
description: 
published: true
date: 2021-11-23T16:50:09.809Z
tags: containers, docker
editor: markdown
---

# What Are Containers
## Why Containers
Historically, and in terms of layers of abstraction from the bare metal of a computer, it has gone
Bare Metal -> Virtual Machines -> Public Cloud -> Containers. 

Containers give us many of the security and resource-management features of VMs but without the cost of having to run a whole other operating system. It instead usings chroot, namespace, and cgroup to separate a group of processes from each other.