---
title: Volumes and Bind Mounts
description: 
published: true
date: 2022-04-24T23:22:58.691Z
tags: docker
editor: markdown
---

# Functionality
A file or directory on the host machine is mounted into a container. 

The generic syntax is

```
--volume <local file system directory absolute path>:<container file system directory absolute path>:<read write access>
```