# Docker Architecture

<img width="771" height="908" alt="image" src="https://github.com/user-attachments/assets/e9fb8a54-4edd-458c-ab76-21373992f8a6" />

## Docker Client:
Docker Client helps users interact with Docker. 
The most common client is the Docker Command Line Interface (CLI), which sends commands to the Docker Daemon via a REST API, typically over UNIX sockets or a network interface.

## Docker Daemon (dockerd):
Docker Daemon  is the core component that runs on the Docker Host. 
It listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes.
The daemon handles the lifecycle of containers, including building images, running instances, and managing resources. 

## Docker Host:
Docker Host is the environment where the Docker Daemon runs, providing the necessary infrastructure to execute and manage Docker applications.
It encompasses the Docker Daemon, along with the storage for images, running containers, and configured networks and volumes.

## Docker Registry:
Docker Registry is a centralized repository for storing Docker images.
Docker Hub is the most widely used public registry, where users can find and share pre-built images.
Users can also set up private registries for their own image management.

# Docker Commands 

## Installation 

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose docker-compose-plugin

## List docker images

docker images

## List running containers 

docker ps

## List All conatiners (Running & Exited )

docker ps -a

## Pulling image from registry

docker pull image:tag 

## Pushing image to registry

docker push localimage:tag useracct-name/<image-name>:tag 

## Run a container from image 

docker run -it --name container-name -p hostport:containerport image:tag /bin/bash

## Execute commands inside a container

docker exec -it <conatiner-id> /bin/bash

## Build an image from dockerfile.

 docker build -t image-name:tag /pathofdockerfile

## Inspect a dokcer image 

docker inspect <image-name>:tag 

## Stop a conatiner 

docker stop <conatiner-id>

## Start a conatiner 

docker start <container-id>

## Remove a container 

docker rm <conatiner-id>

## Remove a docker image

docker rmi <image-name>:tag 

## Build multiple containers in single go using docker-compose.yaml  (extarcts, downloads, pulls images, creates & runs containers)

docker compose up -d 

## Stop multiple containers at once 

docker compose down 

## Check container running using docker-compose 

docker compose ps 

## Check logs of docker-compose 

 docker compose logs 

## Create docker volume 

docker volume create <vol-name>

## Delete docker volume 

docker volume rm <vol-name>

## Delete unused volumes 

docker volume prune -y

## For more info on docker volume 

docker volume inspect <vol-name>

## Attaching volume while creating & running docker container 

docker run -it -name <cont-name> -v <vol-name>:/mountpoint-path  <image-name>:tag /bin/bash
                                     (or)
docker run -it --name <cont-name> --mount type=volume,source=<vol-name>,target=<mountpoint/path <image-name>:tag /bin/bash

## Create docker network

docker network create <net-name>

# Attaching network while creating & running docker container

docker run -it --name <cont-name> --network <net-name> <image-name>:tag /bin/bash

## Connect docker network to a running container

docker network connect <net-name> <cont-name>

## For more info on docker network

docker network inspect <net-name>

## Disconnect docker network from a running container 

docker network disconnect <net-name> <cont-name>

## Delete docker network

docker newtork rm <net-name>






