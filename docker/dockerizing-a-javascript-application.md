---
title: Dockerizing a Javascript Application
description: 
published: true
date: 2022-04-24T23:55:36.493Z
tags: docker
editor: markdown
---

# Writing a Development Dockerfile
## Good Objectives for a Development Dockerfile
- Get a good base image for running JS applications, like node.
- Set the default working directory inside the image.
- Copy the `package.json` file into the image.
- Install necessary dependencies.
- Copy the rest of the project files.
- Start the development server by executing `npm run dev` (or relevant command).

## Typical development Dockerfile
```
FROM node:lts-alpine

EXPOSE 3000

USER node

RUN mkdir -p /home/node/app

WORKDIR /home/node/app

COPY ./package.json .
RUN npm install

COPY . .

CMD [ "npm", "run", "dev" ]
```