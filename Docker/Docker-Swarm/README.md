# Integrating Docker Swarm with AWS autoscaling Group 

## Docker swarm adds containers to available node when a nodes goes DOWN. 

## ASG adds worker nodes(EC2) when nodes goes down
```
ASG - Takes care of Infrastructure Provisioning & Management.
SWARM - Takes care of Orchestration - Container rescheduling.
```

What you build is:

> **ASG manages EC2 nodes** + **user-data script makes them join Swarm automatically**


#  Architecture (what you’re building)

```
AWS Auto Scaling Group
        ↓
 Launch EC2 instances
        ↓
 User Data script runs
        ↓
 Instance joins Docker Swarm
        ↓
 Swarm schedules containers
```

---


## 🔹 1. Create a an EC2 for Swarm manager (manual step)

On your main node:
```
docker-compose.yaml
version: "3.8"
services:
  backend:
    image: redis
    ports:
      - "6379:6379"
    volumes:
      - db:/data
    networks:
      - backend
  frontend:
    image: dockersamples/examplevotingapp_vote
    ports:
      - "8000:80"
    environment:
      - ENV_DBNAME=backend
      - ENV_PWD=admin
      - ENV_PORT=6379
    depends_on: 
      - backend
    volumes:
      - app:/var/lib/app/data
    networks:
      - frontend
      - backend
    deploy:
      replicas: 3
      restart_policy:
        condition: on-failure
    healthcheck:
      test: ["CMD","curl","-f","http://localhost"]
      interval: 15s
      timeout: 5s
      retries: 3
      start_period: 10s
networks:
  frontend:
  backend:
volumes:
  app:
  db:
```
### docker swarm creation 

```bash
docker swarm init
```

You’ll get something like:

```bash
docker swarm join --token SWMTKN-1-xxxxx <MANAGER-IP>:2377
```

PORT - **2377** connect worker nodes with Manager node.

### Verify if manager & worker nodes are created & joined to the swarm.

```bash
docker info
```

### Command for node to leave swarm 

```bash
docker swarm leave
```
---

## 🔹 2. Create Launch Template (IMPORTANT STEP)

In AWS:

* Go to EC2 → Launch Templates → Create

* Choose:

  * AMI: Ubuntu / Amazon Linux

  * Instance type: t3.micro (for testing)

---

## 🔹 3. Add **User Data script** (this is the core)

Paste this:

```bash
#!/bin/bash

# Install Docker
apt-get update -y
apt-get install -y docker.io

systemctl start docker
systemctl enable docker

# Join Swarm (REPLACE values)
docker swarm join \
  --token SWMTKN-1-xxxxx \
  <MANAGER-PRIVATE-IP>:2377
```

👉 This makes every new EC2 instance:

* Install Docker

* Automatically join Swarm

---

## 🔹 4. Create Auto Scaling Group

* Attach Launch Template
* Set:

  * Desired: 2
  
  * Min: 1
  
  * Max: 5

* Set CPU Threshold Capacity 

👉 Now AWS will:

* Launch instances

* Run user-data

* Nodes join Swarm automatically

---

## 🔹 5. Verify nodes in Swarm

On manager:

```bash
docker node ls
```
👉 You should see new nodes joining automatically

## 🔹 6. Create Application Stack 

### deploy the application stack, to create replicas.

```bash
docker stack deploy -c docker-compose.yaml STACK_NAME
```
### verify  stack creation

```bash
docker stack ls
```

### check for services running inside the stack 

```bash
docker service ls
```

### check which node is running the specific services/ containers

```bash
docker stack ps STACK_NAME 
```

### Display the  config of the application stack.

```bash
docker stack config -c docker-compose.yaml
```
### command to remove stack 

```bash
docker stack rm STACK_NAME
```
---


# 🔥 Now the magic happens

When CPU load increases:

1. ASG launches new EC2 instances

2. They join Swarm automatically

3. Swarm now has more capacity

4. You can scale services:

```bash
docker service scale VOTING_APP_frontend=5
```

---

# ⚠️ Important production considerations

## 🔸 1. Use PRIVATE IP in swarm join command (not public ip )

```bash
<MANAGER-PRIVATE-IP>:2377
```

---

## 🔸 2. Security Group rules

Allow between nodes:

* TCP **2377** → Swarm management
* TCP/UDP **7946** → node communication
* UDP **4789** → overlay network


---

## 🔸 3. Token rotation (advanced)

```bash
docker swarm join-token worker
```

👉 Tokens can change → don’t hardcode long-term

---

## 🔸 4. Better approach (production-grade)

Instead of hardcoding token:

👉 Store token in:

* AWS SSM Parameter Store
* AWS Secrets Manager

Then fetch in user-data script

---

## 🧪 Test it (real DevOps scenario)

1. Increase ASG desired capacity
2. Watch:

```bash
docker node ls
```

3. Scale service:

```bash
docker service scale VOTING_APP_frontend=6
```

👉 You’ll see containers spread across new nodes

---

##  Interview-ready explanation

If asked:

> How do you integrate Docker Swarm with AWS Auto Scaling?

Answer:

* Use ASG to manage EC2 nodes
* Use Launch Template with user-data script
* Script installs Docker and joins Swarm using token
* New instances automatically become worker nodes
* Swarm schedules containers on available nodes

---

