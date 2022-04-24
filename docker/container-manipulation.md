---
title: Container Manipulation
description: 
published: true
date: 2022-04-24T19:20:35.079Z
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