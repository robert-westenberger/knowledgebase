---
title: Image Manipulation
description: 
published: true
date: 2022-04-24T21:20:12.824Z
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
### RUN 
The `RUN` instruction executes a command inside the container shell. 
### CMD
The `CMD` instruction sets the default command for your image. 


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

## Building an Image
To perform an image build, the daemon needs the name of the `Dockerfile` and the build context.

Executing `docker image build .` will build an image. The daemon finds any file named `Dockerfile` within the context. 

The `.` sets the context for the build. The context means the directory accessibile by the daemon during the build process.

## Tagging Docker Images
Just like containers, you can assign custom identifiers to your images instead of relying on the randomly generated ID. It's just called **tagging** instead of naming.

### At Build Time
Generic syntax is
`--tag <image repository>:<image tag>`

The repository is usually known as the image name and the tag indicates a certain build or version.

### Tagging an Existing Image
Use the `image tag` command.
### Example (Of using a tag)
Taking the official `mysql` image for example, in order to run `mysql` version `5.7`, we would execute

`docker container run mysql:5.7`, where `mysql` is the image repo and `5.7` is the tag.


`
