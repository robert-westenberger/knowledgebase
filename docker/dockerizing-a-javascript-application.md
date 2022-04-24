---
title: Dockerizing a Javascript Application
description: 
published: true
date: 2022-04-24T22:26:12.307Z
tags: docker
editor: markdown
---

# Writing a Development Dockerfile
## Good objectives for a development dockerfile
- Get a good base image for running JS applications, like node.
- Set the default working directory inside the image.
- Copy the `package.json` file into the image.
- Install necessary dependencies.
- Copy the rest of the project files.
- Start the development server by executing `npm run dev` (or relevant command).

