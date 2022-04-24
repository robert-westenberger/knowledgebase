---
title: Container Manipulation
description: 
published: true
date: 2022-04-24T20:01:27.833Z
tags: docker
editor: markdown
---

# Create a Container
`container create` creates a container from a given image. The container won't be running after this command.
# Start a Container
The `container start` command can be used to start any stopped or kiled container. The syntax is 
`docker container start <container identifier>`. 

The `container start` command starts any container in detached mode by default and retains any port configurations made previously.
# Run a container
`container run` is, in reality, executing both `container create` and `container start`. 
## Syntax
### Generic Syntax
`docker run <image name>`

### Restructured syntax
`docker <object> <command> <options>

- `<object>` indicates the type of Docker object you'll be manipulating. This can be a `container`, `image`, `network`, or `volume` object.

- `command` indicates the task to be carried out by the daemon, that is the `run` command. 

- `options` can be any valid parameter that can override the default behavior of the command, like the `--publish` option for port mapping.

Following this syntax, the `run` command can be written as follows: 

`docker container run <image name>` .

The `image name` can be of any image from an online registry or your local system. 

# Options
## Publishing Ports
Since containers are isolated, your host system doesn't know anything about what's going on inside a container. Hence, applications running inside a container remain inaccessible from the outside. 

To allow access from outside of a container, you must publish the appropriate port inside the container to a port on your local network. 

### Common syntax for `--publish` or `-p` option
`--publish <host port>:<container port>`

So for `--publish 8080:80`, any request sent to port `8080` of the host will be forwarded to port `80` inside the container.

## Detached Mode
The `--detach` or `-d` option will override the default behavior of containers attaching themselves to the terminal window from which they are run. 

This means that if you then close that terminal window, the container will continue running.

## Interactive Mode
The `-it` option passed to `container run`
## Name or Rename a Container
By default, every container has two identifiers:

- `CONTAINER ID` - a random 64 character-long string.
- `NAME` - combination of two random words, joined with an underscore.

The `--name` option can be used to name the container.

## Remove Containers As Soon as They Are Stopped
Ther `--rm` option for `container run` and `container start` will remove the containers as soon as they're stopped. 
# List Containers
## Currently running
The `container ls` command can be used to list containers that are currently running.
## All containers (including stopped or killed containers)
Pass the `--all` option... so 
`docker container ls --all`.

# Rename a container
`docker container rename <container identifier> <new name>`.

See the "Name or Rename a Container" subsection above for more information about the `--name` option for the `run` command, for initially giving a name to a container.

# Stop or Kill a Running Container
## Containers Running in the Foreground
Close the terminal window, or hit `ctrl + c`. 
## Containers Running in the Background
### `container stop`
`docker container stop <container identifier>` where `container identifier` can either be the id or the name of the container.

The `stop` command shuts down a container gracefully by sending a `SIGTERM` signal. If the container doesn't stop within a certain period, a `SIGKILL` signal is sent which shuts down the container immediately. 
### `container kill`
`docker container kill <container identifier>` will send a `SIGKILL` signal instead.


# Rebooting a Running Container
`docker container restart <container identifier>`.

The `container restart` command attempts to stop the target container and then starts it back up again, whereas the start command just starts an already stopped container.

# Remove Dangling Containers
The `container rm` command, whos generic syntax is
`docker container rm <container identifier>`. 

## Remove Multiple Containers At Once
Pass identifiers to the `docker container rm` command separated by spaces.

## Remove All Dangling Containers
You can use the `container prune` command to remove all dangling containers in one go.


