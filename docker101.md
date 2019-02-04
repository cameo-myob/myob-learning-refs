[Docker Quick Start Video Tutorial](https://medium.freecodecamp.org/docker-quick-start-video-tutorials-1dfc575522a0)

## Docker 101
- Containers run like processes on the kernel through the docker engine
- this means the docker engine can control the container's access to CPU, memory etc
- docker engine only exposes the kernel, not the native os
- this means containers need operating system inside them to run
- containers can have different OS to the native machine
- which means all OS need to be able to use the same kernel
- on mac, this means linux/debian/ubuntu/alpine
- in addition to os, container must bundle all dependencies (gems, packages etc) too
- a Dockerfile is a textfile, list of instructions that you pass to docker engine to tell it how to build your container
- docker build command to pass dockerfile to engine, which follows instructions to build docker image
- docker run on docker iamge will start a conatiner based on that image
- has to be named `Dockerfile`

## Getting Started with Docker on a Mac
- base images can be found at [Docker Hub](https://hub.docker.com/)
- basic Dockerfile:
```
FROM node:9.3.0-alpine (the base image)
```
- above dockerfile will create container and immediately close it as it doesn't run and processes
- to use dockerfile to build image use `docker build .` to build from current directory, else use path to directory
- `docker images` will show all docker images
- `docker build . -t <repo-name>:<tag>` to use custom repository name and tag for image
- to run image use `docker run <image-id>`
- `docker run -it <image-id> /bin/sh` to run container with interactive terminal
- `docker run -it --name <container-name> <image-id> /bin/sh` to run named container with interactive terminal
- can also run processes directly - `docker run -it <image-id> node server.js`
- `docker ps` to check docker processes
```
FROM node:9.3.0-alpine

WORKDIR /app (directory in container)

ADD . /app (ADD <source-destination> <work-directory>)
```
- `docker run -p 8000:8000 -it <image-id> node server.js` maps local port 8000 to container port 8000
- `CTRL P` + `CTRL Q` detaches local terminal from container terminal without stopping container
- `docker stop <container-id>` to kill container

## Using CMD inside Dockerfile
- `CMD` syntax in Dockerfile
```
CMD ["node", "server.js"] (first is command, subsequent are params)
```
- need to rebuild image every time you change the dockerfile
- `docker ps` to see running docker processes

## Debug Broken Docker Builds
- `RUN apk --update add vim` in Dockerfile will add vim to docker container to help with debugging
- use intermediate containers to help debug issues with dockerfile


## Docker Cheat Sheet
### List Docker CLI commands
`docker`
`docker container --help`

### Display Docker version and info
`docker --version`
`docker version`
`docker info`

### Execute Docker image
`docker run hello-world`

### List Docker images
`docker image ls`

### List Docker containers (running, all, all in quiet mode)
`docker container ls`
`docker container ls --all`
`docker container ls -aq`

# Use an official Python runtime as a parent image
`FROM python:2.7-slim`

# Set the working directory to /app
`WORKDIR /app`

# Copy the current directory contents into the container at /app
`COPY . /app`

# Install any needed packages specified in requirements.txt
`RUN pip install --trusted-host pypi.python.org -r requirements.txt`

# Make port 80 available to the world outside this container
`EXPOSE 80`

# Define environment variable
`ENV NAME World`

# Run app.py when the container launches
`CMD ["python", "app.py"]`

```
docker build -t friendlyhello .  # Create image using this directory's Dockerfile
docker run -p 4000:80 friendlyhello  # Run "friendlyname" mapping port 4000 to 80   
docker run -d -p 4000:80 friendlyhello         # Same thing, but in detached mode
docker container ls                                # List all running containers
docker container ls -a             # List all containers, even those not running
docker container stop <hash>           # Gracefully stop the specified container
docker container kill <hash>         # Force shutdown of the specified container
docker container rm <hash>        # Remove specified container from this machine
docker container rm $(docker container ls -a -q)         # Remove all containers
docker image ls -a                             # List all images on this machine
docker image rm <image id>            # Remove specified image from this machine
docker image rm $(docker image ls -a -q)   # Remove all images from this machine
docker login             # Log in this CLI session using your Docker credentials
docker tag <image> username/repository:tag  # Tag <image> for upload to registry
docker push username/repository:tag            # Upload tagged image to registry
docker run username/repository:tag                   # Run image from a registry
```



# Useful commands
`docker ps -a` shows all running and stopped containers
`docker history <image-name>` shows all layers that make up the image
`CTRL + P`, `CTRL + Q` will detach from container 
`docker attach <container-id>` will attach to container
`docker run -d <image-name>` will start container detached
`docker stop <container-id>` will kill container
`docker rmi <image-id>` to remove image/layer

### When running a `Dockerfile`
- Make the `Dockerfile`
- `docker build .` in the same directory as the file
- `docker build -f <path-to-file> .` to build a file in a different location
- `docker build -t <repo-name> .` to tag image and save in repository