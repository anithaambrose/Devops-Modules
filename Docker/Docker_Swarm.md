
# Container Orchestration:

Managing the lifecycles of containers, especially in large , dynamic environments

Automating the provisioning, deployment & the management of Scaling & Networking  operations of the containers.

# Tools of container orchestration :

  1.	Docker Swarm ( By docker)     → used for small & decent sized Applications
  
  2.	Kubernetes ( By Google)        → used for Large Applications
  
  3.	Nomad ( By Hashicorp)

## Why is Container Orchestration is needed?

 Container are ephemeral by nature, they stop when process inside them finishes or ends because of an error.

Also a single container per service may not be sufficient enough to handle the growing traffic to the application.
for these scenarios.

we need a tool that can bring up the stopped containers or to spin up new ones's to handle the growing traffic & to ensure Load balancing & high availability of the application all the time.

## Benefits of container Orchestration:

1.	 Automatic Scheduling:  Decides which applications needs to runs on which containers.	
        scheduled based on availability of nodes/containers

2.	Scaling: Scales Container (up & down)  based on demand.

3.	High Availability:  if container or node(ec2) fails/ crashed , New container takes over the process.

4.	Rolling Updates:  For newer updates from irctc 1.0 to irctc 1.1 image version → There wont be any downtime.
        Application will always be Up and running.

5.	Self healing - if container crashes , orchestrator will restart automatically.

6.	Load Balancing: Distribution of traffic evenly across replicas of a application.

7.	Declarative configuration: helps to define the requirements. 

# Blue/Green Deployments

its a technique that minimizes downtime and reduces risk by running two identical production environments: a "blue" environment (current live version) and a "green" environment (new version).

|------------------Blue Env-------------|----------------Green Env (backup)----------|
|initially  version 9.0 | 	initial version 9.0 |
| before updating LB will be pointing to Green Env only |
| during update to version 9.1	| acts a standby server that handles traffic |
| LB will now point to Blue env as well , but initially with few user  only& then lets in more users over time.| 
| after update with version 9.1 | 	becomes backup|

 
# Docker SWARM:

•	is an Orchestration solution, to manage container in a cluster.

•	No special installation required as it is native to docker

•	Used for Small scaled applications

•	best management system for orchestration - that creates a pool/ cluster of hosts to run containers.

•	Cluster - set of connect machines that works together.

•	When new machine joins the cluster it becomes the Node in the swarm.

## What can one do by using docker swarm?

•	Deploy new containers to replace failed ones.

•	Scale the number og container for load balancing

•	Rolling out applications updates among the containers in rolling updates.

•	Rollback of applications to older versions

•	bring down a node for maintenance without any application downtime.

![image] ()

## Terminologies:

•	Service - series of tasks - is the image for 

•	Task - commands inside a container.

•	Leader - specific to manager node.

## Docker stack 

Each application in docker will be called as a stack 

## What is a Docker health check ?

Its a way to tell docker how to test if the container is  working as expected.

## Use-cases:

Helps Triggers auto restart

Helps  improve availability in orchestration(docker swarm).

Helps in load balancing (only routes the healthy containers)

## Why do we need it ?

To ensure services are up and running as expected.

### health check cmd :

HEALTHCHECK  [OPTIONS]  CMD command

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
