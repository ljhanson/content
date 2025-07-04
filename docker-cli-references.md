---
title: Docker Commands Reference
date: 2019-10-08
slug: docker-reference
draft: false
---

| Command | Description |
| :----: | :----: |
| start | Start Container |
| stop | Stops Container|
| restart | Restart Container |
| kill | Kill Container |
| attach | Attach terminal to running container |
| exec | Excutes command within a running container |
| inspect | Detail output about running container in JSON |
| history | Shows history of container image|

Dockerfile Commands

| Command | Reference |
| :----: | :----: |
| FROM | Base image, usually first |
| WORKDIR | Set's working directory |
| ADD | Adds file from source to destination.  Can be URL, Will Unzip |
| COPY | Copy from host machine.  Best practice to use unless you need ADD's functionality. |
| EXPOSE | Expose a port from container at runtime |
| VOLUME | Creates a mount point for container |
| RUN | Executes command in a new layer and commits to image.  Can have many. |
| CMD | Provides default behavior for launching an instance.  Only one per image and not hole image is being built.|
| ENV | Sets and environment variable that is available through build and during container run. |
| ARG | Variables that can be passes into the build command.  Don't use for sensitive info. |
| LABEL | Key-Value parr's exposed as image metadata |

Dockerfile Best Practices

- Keep image small
- As few layers as possible
- Avoid breaking cache
- Avoid known vulnerabilities

Keeping Image Small

- Use small or slim base image
- Combine layers
- Use .dockerignore
- Use multistage build
  - Best for compiled code or have lot of intermediate steps
  - Keep final stage as small as possible
  - All other stages are discarded
- Change user to non-root user
  - Better security
  - Adds additional layer

HEALTHCHECK command

- Tells Docker how to check status of container
- HEALTHCHECK --interval=30s CMD curl -f <http://localhost/status> || exit 1

Compose File Syntax

- Image
- Build
- Image and Build
