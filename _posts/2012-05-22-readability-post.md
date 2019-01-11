---
layout: post
title: "Docker 101 🐳"
date: 2019-01-11
excerpt: "Basic Docker Commands"
tags: [sample post, readability, test]
comments: true
---

Docker is a computer program that performs operating-system-level virtualization, also known as “containerization”. Docker allows to run multiple containers on a single linux OS. Containers are used for fast application deployment. Containers are running instances of an image . Unlike in virtualization using VMWare, containers have only one base operating system. Therefore, containers are widely used in the Dev-Ops environment for faster application deployment.

When a virtualized environment is created, there are a lot of resources that get allocated such as RAM, hard disk etc. When a virtual machine boots up, it may not consume all the resources that were allocated to it. Therefore, in this case many resources get wasted and that’s where containers can be more helpful. Containers use only the resources that are needed.

Important Docker commands:

- List all containers (only IDs) : `docker ps -aq`
- Stop all running containers:   `docker stop $(docker ps -aq)`
- Remove all containers: `docker rm $(docker ps -aq)`
- Remove all images: `docker rmi $(docker images -q)`
- Create image using this directory’s Dockerfile : `docker build -t mycontainer` . -t is used to name a container.
- Run “mycontainer” mapping port 8080 to 80: `docker container run -p 8080:80 mycontainer`
- Map a volume to docker containers : `docker run -p 8080:80 -v /Desktop/docker/src:/var/www/html mycontainer`
- Run “mycontainer” mapping port 8080 to 80, but in background/detached mode: `docker run -d -p 8080:80 mycontainer`
- See a list of all running containers: `docker container ls`
- Gracefully stop the specified container: `docker container stop <hash>`
- See a list of all containers, even the ones not running: `docker container ls -a`
- Force shutdown of the specified container: `docker kill <hash>`
- Remove the specified container from this machine: `docker container rm <hash>`
- Show all images on this machine: `docker images -a`
- Log into a CLI session using your Docker credentials: `docker login`
- Tag <image> for upload to registry: `docker tag <image> username/repository:tag`
- Upload tagged image to registry: `docker push username/repository:tag`
- Run image from a registry: `docker run username/repository:tag`
- List Docker volume: `docker volume ls`
- List Docker Network: `docker network ls`

#### LEGACY COMMANDS:

- LEGACY: Remove the specified image from this machine: `docker rmi <imagename>`
- LEGACY:Remove all images from this machine: `docker rmi $(docker images -q)`
- LEGACY: Remove all images with dependencies: `docker images -q | xargs docker rmi –f`

