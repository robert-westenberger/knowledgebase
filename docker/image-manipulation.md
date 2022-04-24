---
title: Image Manipulation
description: 
published: true
date: 2022-04-24T22:28:44.253Z
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
### COPY
The `COPY` instruction (`COPY <source> <destination`) copies files from your local filesystem and into an image.
### ADD 
The `ADD` command has two forms:
```
ADD [--chown=<user>:<group>] <src>... <dest>
ADD [--chown=<user>:<group>] ["<src>",... "<dest>"]
```
The `ADD` instruction copies new files, directories or remote file URLs from `<src>` and adds them to the filesystem of the image at the path `<dest>`.
### ARG
```
ARG <name>[=<default value>]
```
The `ARG` instruction defines a variable that users can pass at build-time to the builder with the `docker build` command using the `--build-arg <varname>=<value>` flag.
#### Default Values
```
FROM busybox
ARG user1=someuser
ARG buildno=1
# ...
```

### WORKDIR
The `WORKDIR` instruction sets the default working directory.

It is set for any `RUN`, `CMD`, `ENTRYPOINT`, `COPY` and `ADD` instructions that follow it in the Dockerfile. If the `WORKDIR` doesn’t exist, it will be created even if it’s not used in any subsequent Dockerfile instruction.

It can be used multiple times per Dockerfile.

### ENTRYPOINT
An `ENTRYPOINT` instruciton allows you to config a container that will run as an executable.

### USER
The `USER` instruction sets the default user for the image. By default, Docker runs containers as the root user. This can pose a security threat in some cases, so it's usually best to run as a non-root user.
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
`docker image tag <image id> <image repository>:<image tag>`

OR 

`docker image tag <image repository>:<image tag> <new image repository>:<new image tag>`
### Example (Of using a tag)
Taking the official `mysql` image for example, in order to run `mysql` version `5.7`, we would execute

`docker container run mysql:5.7`, where `mysql` is the image repo and `5.7` is the tag.


# List and Remove Docker Images
The `image ls` command will list all images on your local system.

`docker image ls`

Images listed here can be deleted using the `image rm` command. 

# Removing an Image
`docker image rm <image identifier>`

## By Force
The `--force` option skips any confirmation questions. You can use the `--all` option to remove all cached images in your local registry. 

## Remove All Cached Images
The `--all` or `-a` option will remove all cached images in your local registry.

# View Layers of an Image
The `docker image history <image repository>:<tag>` will list the layers of an image, ordered by age. 


# Share Docker Images Online
1. Create an account at any of the online registries.
2. Login from the command line using `docker login`.
3. Push the image by executing `docker image push <image repository>:<image tag>`.
	In order to push it to a registry, the image must be tagged. 