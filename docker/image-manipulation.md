---
title: Image Manipulation
description: 
published: true
date: 2022-04-24T20:34:43.751Z
tags: docker
editor: markdown
---

# Create a Docker Image
Recall that images are multi-layered self-contained files that act as the template for creating containers. They are like a frozen, read-only copy of a container.

## Using a Dockerfile
A `Dockerfile` is a collection of instructions that, once processed by the daemon, results in an image.

### FROM
Every valid `Dockerfile` starts with a `FROM` instruction. This is the base of the resultant image.

### EXPOSE 
The `EXPOSE` instruction is used to indicate the port that needs to be published. 

Using `EXPOSE` doesn't mean that you won't need to `--publish` the port. You'll still need to use the `--publish` option explicitly. The `EXPOSE` option works like documentation for someone who's trying to run a container using your image.
### Example - Custom nginx
```
FROM ubuntu:latest

EXPOSE 80

RUN apt-get update && \
    apt-get install nginx -y && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

CMD ["nginx", "-g", "daemon off;"]
```
Each instruction, `FROM`, `EXPOSE`, `RUN` and `CMD`, create another layer of the image.