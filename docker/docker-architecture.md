---
title: Docker Architecture
description: 
published: true
date: 2022-04-24T18:59:44.707Z
tags: docker
editor: markdown
---

# Docker Daemon
The daemon (`dockerd`) is a process that keeps running in the background and waits for commands from the client. The daemon is capable of managing various Docker objects.

# Docker Client
The client (`docker`) is a command-line interface program mostly responsible for transporting commands issued by users. 

# REST API
The REST API acts as a bridge between the daemon and the client. Any command issues using the client passes through the API to finally reach the daemon. 

