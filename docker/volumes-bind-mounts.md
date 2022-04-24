---
title: Volumes and Bind Mounts
description: 
published: true
date: 2022-04-24T23:33:04.794Z
tags: docker
editor: markdown
---

# Bind Mounts
## Functionality
A file or directory on the host machine is mounted into a container. 
## Generic syntax
```
--volume <local file system directory absolute path>:<container file system directory absolute path>:<read write access>
```
# Volumes

# Anonymous Volumes
## Functionality
An anonymous volume is identical to a bind mount except that you don't need to specify the source directory. 
## Generic Syntax
```
--volume <container file system directory absolute path>:<read write access>
```