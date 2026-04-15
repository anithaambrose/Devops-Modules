
# Container Orchestration:

Managing the lifecycles of containers, especially in large , dynamic environments

Automating the provisioning, deployment & the management of Scaling & Networking  operations of the containers.

# Tools of container orchestration :

  1.	Docker Swarm ( By docker)     → used for small & decent sized Applications
  
  2.	Kubernetes ( By Google)        → used for Large Applications
  
  3.	Nomad ( By Hashicorp)

## Why is Container Orchestration is needed?

####  Container are ephemeral by nature, they stop when process inside them finishes or ends because of an error.

Also a **single container per service may not be sufficient enough to handle the growing traffic** to the application.

for these scenarios,we need a tool that can, 
    ```
    1. bring up the **stopped containers** 
    2. to spin up new ones's to **handle growing traffic** 
    3. to ensure **Load balancing & high availability** of the application all the time.
    ```
## Benefits of container Orchestration:

### 1.	Self healing - if container crashes , orchestrator will restart automatically.

### 2.	Rolling Updates:  For newer updates from irctc 1.0 to irctc 1.1 image version → There wont be any downtime.
   
   **Application will always be Up and running.**

### 3.	Scaling: Scales Container (up & down)  based on demand.

### 4.	Load Balancing: Distribution of traffic evenly across replicas of a application.

5.	 Automatic Scheduling:  Decides which applications needs to runs on which containers.	
   
   **scheduled based on availability of nodes/containers**

6.	High Availability:  if container or node(ec2) fails/ crashed , New container takes over the process.

7.	Declarative configuration: helps to define the requirements. 

# Blue/Green Deployments

its a technique that **minimizes downtime and reduces risk** by running **two identical production environments**

a "blue" environment (**current live version**) and a "green" environment (**new version**).

|   Blue Env|Green Env (backup)|
|-----------|---------------|
|initially  version 9.0 | 	initial version 9.0 |
| *before updating LB will be pointing to Green Env only*|
| during update to version 9.1	| acts a standby server that handles traffic |
| *LB will now point to Blue env as well , but initially with few user  only& then lets in more users over time*| 
| after update with version 9.1 | 	becomes backup|

 
# Docker SWARM:

Docker SWARM is an **Orchestration solution, to manage container** in a cluster.

•	No special installation required as it is NATIVE TO DOCKER

•	Used for SMALL SCALED APPLICATIONS

•	best management system for orchestration - that creates a pool/ cluster of hosts to run containers.


# DOCKER SWARM ARCHITECTURE :

  
![image](https://github.com/anithaambrose/Devops-Modules/blob/main/Docker/docker%20swarm.png)


## What can one do by using docker swarm?

•	DEPLOYS new containers to replace failed ones.

•	SCALES the number og container for load balancing

•	Rolling out applications updates among the containers in ROLLING UPDATES.

•	ROLLBACK of applications to OLDER VERSIONS

•	bring down a node for maintenance WITHOUT APPLICATION DOWNTIME.


### Cluster - set of connect machines that works together.

•	When new machine joins the cluster it becomes the NODE in the swarm.


## Terminologies in Cluster:

•	Service - series of tasks - CONTAINERS

•	Task - COMMANDS inside a container.

•	Leader - specific to manager node / Clusters Leader 


## Docker STACK 

Each application in docker will be called as a stack.


## States of Nodes:

(*)  -   Current Node 

READY -   node is recognized by manager 

ACTIVE -  node is used as worker node 

## Use-cases od docker orchestor:

* Helps **Triggers auto restart**

& Helps  **improve availability** in orchestration(docker swarm).

* Helps in **load balancing** (only routes the healthy containers)


## What is a Docker health check ?

Its a way to tell docker how to test if the container is  working as expected.

## Why do we need it ?

To ensure services are up and running as expected.

### health check cmd :
`
HEALTHCHECK  [OPTIONS]  CMD command
`
