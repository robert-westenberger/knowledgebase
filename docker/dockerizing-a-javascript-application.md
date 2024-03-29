---
title: Dockerizing a Javascript Application
description: 
published: true
date: 2022-04-25T01:08:11.251Z
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

## Typical Development Dockerfile
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

# Running a Development Container
- We want to bind mount the source code directory on our host machine into the running container.

- We want to create an anonymous volume for the `node_modules` directory inside the container so it won't be overwritten by a (nonexistent) directory in the bind mount. 

# Performing Multi-Staged Builds in Docker
In production mode, `npm run build` command compiles your JS code into static HTML, CSS, and JS. To run, you don't need any other runtime dependencies. All you need is a server like `nginx` for example.

## Creating a production build
### Naive Approach
1. Use `node` as the base image and build the application.
2. Install `nginx` inside the node image and use that to serve the static files.

The `node` image is big and most of the stuff it carries is unnecessary to serve your static files.
### Better Approach
- Use `node` image as the base and build the application.
- Copy the files created using the `node` image to an `nginx` image. 
- Create the final image based on `nginx` and discard all `node` related stuff.


#### Multi-staged Dockerfile build
```
FROM node:lts-alpine as builder

WORKDIR /app

COPY ./package.json ./
RUN npm install

COPY . .
RUN npm run build

FROM nginx:stable-alpine

EXPOSE 80

COPY --from=builder /app/dist /usr/share/nginx/html
```
In the above `Dockerfile`, on the first line we use the `as builder` syntax to assign a name to that particular stage of the build so it can be referred to later on. 

In the second stage of the build, we copy the compiled website assets from the first stage into the serve folder for nginx.

##### Building Production Image
`docker image build --tag appname:prod .`

##### Running the Production Container
```
docker container run \
    --rm \
    --detach \
    --name hello-dock-prod \
    --publish 8080:80 \
    hello-dock:prod
```

# How to Ignore Unnecessary Files
Use a `.dockerignore` file for ignoring unnecessary files. 

Files and directories in a `.dockerignore` will be ignored by the `COPY` instruction. 

If you do a bind mount, the `.dockerignore` will have no effect.

## Example `.dockerignore`
```
.git
*Dockerfile*
*docker-compose*
node_modules
```