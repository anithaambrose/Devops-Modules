# Docker Commands 

## Installation 

### Add Docker's official GPG key & repository to Apt sources 

https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository
 
### Docker Packages

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

## Docker - Orchestration  - Docker SWARM

### Initialize  docker swarm  - node as manager/ Master

docker swarm init --advertise-addr <ip_address>

### add nodes to docker swarm using generated Token to addd nodes as worker node to master node 

docker swarm join --token <token> <ipaddress>:2377

### View Docker Information 

docker info

### To View all Nodes.

docker node ls

## To deploy & run an Application Stack 

docker stack deploy -c <docker-composefile> <app-stack-name>

## To view docker stack applications running.

docker stack ls 

## To view services running using docker stack 

docker service ls

## To view container-node info of a running application.

docker stack ps <app-stack-name>

## To delete app stack & services 

 docker stack rm <app-stack-name>
