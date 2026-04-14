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

•	Public - accessed by anyone (pulls & stores images) ex : Dockerhub 

 Dockerhub: https://app.docker.com/

•	Private - Limited Access ( only for granted privileges) ex: dockerhub pv-1 - paid version, jfrog 

   •	AWS  - ECR - Elastic Container Registry.
   •	Azure - Azure Container Registry 

## Docker Objects:

### Containers

Containers are created from docker images as they are ready applications. With the help of Docker API or CLI, we can start, stop, delete, or move a container.

### Images

An image contains instructions for creating a docker container. It is just a read-only template. It is used to store and ship applications.

### Storage

We can store data within the writable layer of the container but it requires a storage driver. Storage driver controls and manages the images and containers on our docker host. 

### Network

Docker networking provides complete isolation for docker containers. It means a user can link a docker container to many networks. It requires very less OS instances to run the workload.


# Docker File

•	A Dockerfile is a text document/ script containing instructions for building a Docker image.

•	The Dockerfile defines the base image, the application's source code, dependencies, and configurations needed for the service to run.

•	Create a new file named `Dockerfile` in the root directory of your microservice.

•	Each instruction in the dockerfile is called as Layer. All together are called Layers of an image.

![image](https://github.com/anithaambrose/Devops-Modules/blob/main/Docker/dockerfile.jpg)

## Keywords of dockerfile:

| Instruction | 	Description	| Example|
|--------------|--------------|--------|
|FROM	|Create a new build stage from a base image.	| FROM python:3.10-slim|
|COPY |	Copy files and directories from host machine (ec2)to container.|	COPY requirements.txt   .|
|     |           |COPY .  .|
|ADD	|Similar to copy, but has adv features like - fetching files from an url.	 |  |
|RUN	|Executes cmds inside the container.	| RUN pip install --no-cache-dir -r requirements.txt|
|ENV	|Sets environment variables in the container.	|   | 
|LABEL	|Adds metadata to an image. - owner, desc, version info	 |  |
|WORKDIR	|Change working directory where the commands needs to be executed.|	WORKDIR /app|
|EXPOSE	| Describe which ports your application is Listening on.|	EXPOSE 5001|
|CMD	| Specify default commands.	| CMD ["python","app.py"]|
|USER |	Set user and group ID.	|   | 
|VOLUME	|Create Volume mounts.	 |     |


# Docker Compose:

•	Service that makes it easier to create and run multi-container applications.

•	Docker Compose allows you to define your application’s containers as code inside a YAML file you can commit to your source repository.

•	It automates the process of managing several Docker containers simultaneously, such as a website frontend, API, and database service.

![image](https://github.com/anithaambrose/Devops-Modules/blob/main/Docker/dockercompose.jpg)

## Docker image optimization :

Reducing the size of the docker image by choosing the small size base image will  make the file light weighted & efficient.  This can be achieved by Multi stage docker build.

## Multi stage Docker Build:

•	Allows you to build create smaller, more efficient docker images by breaking the build process into multiple stages.

•	It avoids unnecessary files that need not be a part of application runtime.

## Benefits:

•	Reduced image Size

•	Improved Security

•	Simplified, Organized build process (easy to understanding dockerfile)

# Docker Volumes:

Docker is an ephemeral container. - meaning 

```
   •	It is short lived.
   
   •	Stateless
   
   •	Automatically deleted after it stops.
   
   •	No Persistence. - means no storage.
  ``` 

•	In order to store the data we need a mount a volume in the host machine & attached  it to Docker container to store - Application logs , user informations, etc

•	These Volume will be present even when the container is Stopped.& it resides on the host machine.

•	All volumes are kept in a specific directory on your host, typically /var/lib/docker/volumes for Linux systems, and are controlled by Docker.

•	This helps During Container Failure as these volume hold logs and user actions to inspect & troubleshoot.

## Interview Question - What's the  Need for Docker Volume ?

A volume is a docker's way to store persistent data outside the container. So that data survives even container restarts or stops.


# Docker Networks:

A virtual network created and managed by docker to enable communication between containers, host machine and any external.

Docker as default has a **bridge network**

## Types of N/w:
  
  1.	bridge    → default for standalone containers (single host)
  
  2.	host        → shares hosts network
  
  3.	overlay   →cross host networking in swarm (multiple host)
  
  4.	none        → disables networking for containers
  
  5.	macvlan  → assigns mac address for lan

 # Docker security ?

 Important for the docker images we create,

   •	Provide least privilege for containers limit users & container permissions
   
   •	isolation of networks : payment related application
   
   •	Size of the images - minimum base image size
   
   •	use official images from dockerhub
   
   •	Scan the images before use
   
   •	avoid unnecessary package downloads from dockerfile
   
   •	Never run the containers with root user privileges.
   
   •	Use Multi stage builds to minimize size.
   
   •	Never save any username & passwords in the docker files.

## what best practices or how to optimize docker images ?

Use Multi stage builds to minimize size & efficiency.

## Docker Ecosystem:
 
 Core components
  
   1.	engine
   2.	client
   3.	Daemon
   4.	registry
   2.	Dockerfile
   3.	docker Compose
   4.	docker Volumes
   5.	docker Networks
   6.	docker Swarm
   7.	docker health checks

## Operations  performed:
 
  1.	writing dockerfile
  2.	creating images, volumes, networks
  3.	Spinning up the containers
  4.	self hosted   to private registry & pushed images
  5.	added health check 

## Flow of this module : 

`
Dockerfile → build images → push to dockerhub  →Docker compose → swarm → stacks → health checks.
`

## Best Practices for writing Dockerfile:

  1.	use small images as base image to reduce size. ( such as slim & alpine versions)
 
  2.	use multi-stage builds
  
  3.	minimize layers (instruction set)
  
  4.	pin the image versions. or use specific tags than going for ubuntu:latest
  
  5.	use non-root user / Avoid root user in running containers.
  
  6.	use health checks for containers.
  
  7.	clean up binaries after installations like zip files downloaded from the internet.
  
  8.	use volumes for data persistency.
  
  9.	always push images to trusted registries / keep them in private.
  
  10.	add unwanted files to .dockerignore file..

## .dockerignore:

It prevents unnecessary files from added to the image build. it increases build speed & reduces size.
