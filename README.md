# dockerTemplate

## Docker cli, server, registry

- <https://docs.docker.com/install/>
- server dockerd
- cli docker
- docker registry to hold images
  - <https://docs.docker.com/registry/>
    - docker run -d -p 5000:5000 --restart=always --name registry registry:2
  - <https://docs.docker.com/registry/introduction/>
  - docker pull, docker push
  - The Registry is open-source, under the permissive Apache license.
  - docker pull ubuntu instructs docker to pull an image named ubuntu from the official Docker Hub. This is simply a shortcut for the longer docker pull docker.io/library/ubuntu command
  - <https://docs.docker.com/registry/deploying/>

### Docker registries

- Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default


## Use Case

Running your own Registry is a great solution to integrate with and complement your CI/CD system. In a typical workflow, a commit to your source revision control system would trigger a build on your CI system, which would then push a new image to your Registry if the build is successful. A notification from the Registry would then trigger a deployment on a staging environment, or notify other systems that a new image is available.

## Dockerfiles

- ADD - copies the files from a source on the host into the container's own filesystem at the set destination
- CMD - can be used for executing a specific command within the container
- ENTRYPOINT - sets a default application to be used every time a container is created with the image
- ENV - sets environment variables
- EXPOSE - associates a specific port to enable networking between the container and the outside world
- FROM - defines the base image used to start the build process
- MAINTAINER - defines a full name and email address of the image creator
- RUN - central executing directive for Dockerfiles
- USER - sets the UID (or username) which is to run the container
- VOLUME - is used to enable access from the container to a directory on the host machine
- WORKDIR - sets the path where the command, defined with CMD, is to be executed

Create a .dockerignore file in the same directory as your Dockerfile. This will prevent your local modules and debug logs from being copied onto your Docker image.

## Build images from Dockerfile

- docker build -t "NAME:Dockerfile" .
- docker build -t "webdev:Dockerfile" .
- docker build -t "appdev:Dockerfile" .
- docker build -t "secdev:Dockerfile" .
- docker images - list all docker immages

## Containers

- A container is a runnable instance of an image

## Services

- Scale containers
- Create replicas
- Swarm mode

## Docker Compose <https://docs.docker.com/compose/>

- File format: <https://docs.docker.com/compose/compose-file/>

1. Define your app’s environment with a Dockerfile so it can be reproduced anywhere.

2. Define the services that make up your app in docker-compose.yml so they can be run together in an isolated environment.

3. Run docker-compose up and Compose starts and runs your entire app.

- You can set a custom project name by using the -p command line option or the COMPOSE_PROJECT_NAME environment variable.

### Integrate Dockerfile into docker-compose.yml

- see docker-compose.yml
- docker-compose up/down/restart
- you could also define everything within the docker-compose.yml file, but making use of both Dockerfile and docker-compose.yml makes for a much more flexible and efficient system

## Dockerizing a nodejs web app

- <https://nodejs.org/de/docs/guides/nodejs-docker-webapp>
- create Dockerfile
- docker build -t \<your username\>/node-web-app
- If you need to go inside the container you can use the exec command:
  - docker exec -it \<container id\> /bin/bash
