---
title: Container Manipulation
description: 
published: true
date: 2022-04-24T19:27:56.187Z
tags: docker
editor: markdown
---

# How to Run a container
## Generic syntax
`docker run <image name>`

## Restructured syntax
`docker <object> <command> <options>

- `<object>` indicates the type of Docker object you'll be manipulating. This can be a `container`, `image`, `network`, or `volume` object.

- `command` indicates the task to be carried out by the daemon, that is the `run` command. 

- `options` can be any valid parameter that can override the default behavior of the command, like the `--publish` option for port mapping.

Following this syntax, the `run` command can be written as follows: 

`docker container run <image name>` .

The `image name` can be of any image from an online registry or your local system. 

# How to Publish a Port
Since containers are isolated, your host system doesn't know anything about what's going on inside a container. Hence, applications running inside a container remain inaccessible from the outside. 

To allow access from outside of a container, you must publish the appropriate port inside the container to a port on your local network. 

## Common syntax for `--publish` or `-p` option
`--publish <host port>:<container port>`

So for `--publish 8080:80`, any request sent to port `8080` of the host will be forwarded to port `80` inside the container.

# How to Use Detached Mode
