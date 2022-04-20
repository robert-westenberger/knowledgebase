---
title: Docker
description: 
published: true
date: 2022-04-20T15:31:38.096Z
tags: docker
editor: markdown
---

# Docker 
## Advantages
### Portability / Consistency
Once you have tested your containerized application you can deploy it to any other system where Docker is running and you can be sure that your application will perform exactly as it did when you tested it.

A docker container allows an entire team to work in the same way, regardless of server machine or OS. 

### Performance
Although virtual machines are an alternative to containers, the fact that containers do not contain an operating system (whereas virtual machines do) means that containers have much smaller footprints than virtual machines, are faster to create, and quicker to start.

Docker containers are virtually identical in terms of performance in relation to bare metal. 


### Continuous Integration Efficiency
We can build a container image and use the same image over every step of the deployment process. 

The advantage of it is the ability to separate non-dependent steps and also run them in parallel. 

## Disadvantages
### Missing featuers
Container self registration, self-inspects, copying files from the host to the contaienr.
### Data in the container
If a container goes down, it needs a backup and recovery strategy. 
### 