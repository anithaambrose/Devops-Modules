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

## Stop a Conatiner 

docker stop <conatiner-id>

## Start a Conatiner 

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

## Create Docker Volume 

docker volume create <vol-name>

## Delete Docker Volume 

docker volume rm <vol-name>

## Delete unused Volumes 

docker volume prune -y

## For more info on docker volume 

docker volume inspect <vol-name>

## Attaching volume while creating & running docker container 

docker run -it -name <cont-name> -v <vol-name>:/mountpoint-path  <image-name>:tag /bin/bash
                                     (or)
docker run -it --name <cont-name> --mount type=volume,source=<vol-name>,target=<mountpoint/path <image-name>:tag /bin/bash





