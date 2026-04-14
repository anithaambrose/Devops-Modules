# Era's Over time:

**Application Era** - One Appliation per Server.

**Virtualization Era** - One Server with Host OS Server runs multiple VM's , each Vm has its own OS.

**Containerization Era** - One Server with Host OS  has a **container Engine** that bundles up multiple Applications with their dependencies Seperately, Together.

# What is a Virtual Machine?

Virtual Machine is a **virtual Environment that functions as a virtual computer system** with its own **OS, memory, storage, created on a physical hardware system** (located onpremise or off premise).

# Hypervisor :

Hypervisor is a **software that partitions the host systems resources** appropriately, to launch multiple VM's on top of it.

Virtualization Era lets you run multiple applications on a sungle server.

# Container:
 
 Container is a standard unit of software that packages code along with it dependencies so that the application runs quickly & reliably from one computing environment to another.
 
 Containers share the machines OS kernel , therefore do not require an OS per application hence lightweight.
 
 Container is just a process running from directory & all the data is coming from image.
 
 Conatinerization lets you shift the application from one environment to another quickly & effectively.

 So that what code works on developer machine will possibly works on devops engineers machine as well.

### Files and Folders in containers base images

 ```
   /bin: contains binary executable files, such as the ls, cp, and ps commands.

    /sbin: contains system binary executable files, such as the init and shutdown commands.

    /etc: contains configuration files for various system services.

    /lib: contains library files that are used by the binary executables.

    /usr: contains user-related files and utilities, such as applications, libraries, and documentation.

    /var: contains variable data, such as log files, spool files, and temporary files.

    /root: is the home directory of the root user.
```

### Files and Folders that containers use from host operating system

```
    The host's file system: Docker containers can access the host file system using bind mounts, which allow the container to read and write files in the host file system.

    Networking stack: The host's networking stack is used to provide network connectivity to the container. Docker containers can be connected to the host's network directly or through a virtual network.

    System calls: The host's kernel handles system calls from the container, which is how the container accesses the host's resources, such as CPU, memory, and I/O.

    Namespaces: Docker containers use Linux namespaces to create isolated environments for the container's processes. Namespaces provide isolation for resources such as the file system, process ID, and network.

    Control groups (cgroups): Docker containers use cgroups to limit and control the amount of resources, such as CPU, memory, and I/O, that a container can access.

```
    
# Docker:

Docker is a **open source containerization platform** , paas tool for **building, deploying &  managing** containerized applications.

Docker enables to **package applications into containers** that encapsulates **source code, libraries & dependencies** required to run the code in any environment.

# Docker Vs  Virtual Machine

|                         Docker                                 |                              VM                                        |
| -------------------------------------------------------------- | ---------------------------------------------------------------------- |
|  lightweight & easily portable as they dont have seperate OS   |             heavy/Bulky as VM has guest OS above the host OS           |
|   containers can be ported to diff Os & started immediately    |              Vm have seperate OS so porting is difficult               |
| security risks are high, as containers have shared host kernel |  more secure as they dont share OS, strong isloation with host kernel  |

# Advantages using Docker:

1. Avoid Conflicts of infrstructure level issues.

2. Portable & lightweight.

3. Efficient utilization of resources 


# Docker Architecture

![image](https://github.com/anithaambrose/Devops-Modules/blob/main/Docker/docker.gif)

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

## Docker Objects:

### Containers

Containers are created from docker images as they are ready applications. With the help of Docker API or CLI, we can start, stop, delete, or move a container.

### Images

An image contains instructions for creating a docker container. It is just a read-only template. It is used to store and ship applications.

### Storage

We can store data within the writable layer of the container but it requires a storage driver. Storage driver controls and manages the images and containers on our docker host. 

### Network

Docker networking provides complete isolation for docker containers. It means a user can link a docker container to many networks. It requires very less OS instances to run the workload.

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
