---
title: Volumes and Bind Mounts
description: 
published: true
date: 2022-04-26T16:14:01.098Z
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
- Volumes are easier to back up or migrate than bind mounts.
- You can manage volumes using Docker.
- They work on both Linus and Windows containers.
- Can be safely shared among multiple containers.
- Volume drivers let you store volumes on remote hosts or cloud providers, to encrypt the contents of volumes, or to add other functionality.
- New volumes can have their content pre-populated by a container.
- Volumes on Docker Desktop have much higher performance than bind mounts from Mac and Windows hosts.
- Volumes are often a better choice than persisting data in a container’s writable layer, because a volume does not increase the size of the containers using it, and the volume’s contents exist outside the lifecycle of a given container.

## Named Volumes
Very similar to an anonymous volume, except that you can refer to a named volume using it's name. 
### Creating a named volume
```
docker volume create <volume name>
```
## Anonymous Volumes
An anonymous volume is identical to a bind mount except that you don't need to specify the source directory. 
### Generic Syntax
```
--volume <container file system directory absolute path>:<read write access>
```