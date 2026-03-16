# Lab 1 - Create AMI & Launch Instance with AMI.

### Specifications to create for AMI:
•	Os - ubuntu
•	App - node.js & npm Utility - pm2
•	Application Code 

1.	Create An **EC2 instance**
2.	Connect to EC2
3.	Install dependencies , packages & run the application code 
```
$sudo apt update;
$sudo apt install nodejs 
$sudo apt install -g pm2
$sudo apt install npm
$git clone https://github.com/techfarmersrikanth/Simple-Nodejs-Server.git
$ls
$cd simple-Nodejs-Server/; 
$ls 
$npm install
```
4. Got to console Select the EC2 instance → Actions →Images & templates → create image →Give a name & description → create image.
5. Go to AMI tab → wait until it moves from pending to Available.
6. Go to Launch Template on the Left side Panel. NOTE: Launch Template is like Blueprint (config) to Launch EC2 instance. i.e., Config Like SG, Key-pair, Permissions. A bundle of these configs are considered as Launch Template.
7. Go to SG → create a new one similar to my_SG (all TCP + All traffic under inbound rules) - this is an EC2 SG
8. Go to Launch Template → click Launch template on top right side ( give a name , description, Under AMI click my AMI's , choose the new AMI created, Instance Type - t2.micro, Key Pair & SG - my_SG)

   Under Advanced Details sections, user data place the following commands
```
#!/bin/bash
cd /home/ubuntu/Simple-Nodejs-Server
pm2 start app.js
```
1. Click on **Launch template**
2. Go To Target Group under Load Balancers
3. Click on create target group
```
choose target group  instance radio button
target group -  name 
port as http - 8080 , click next 
```
4. select the target group insatnces & click on include as pending below,
5. Click create target group , TG is successfully created now
6. Now Go to Security Group tab Create a new SG, select my_SG_ALB  → this is for Application Load balancer
7. under inbound rule see if port 80 is avail & edit inbound rule to add  - ignore step if port is already available.
8. All traffic & All TCP from the drop down , Source - Anywhere IPV4 then save rules.

1. Now Go to **Load Balancer** Tab
2. Select Create Load Balancer
3. Click on Application LB
  •	Give a name, defaults - internet facing, IPV4
  •	Select first 3 availability Zones under network settings
  •	Select the SG-my-SG-ALB from dropdown list
  •	Under Listener- http-port- 80, choose target group under default action drop down box
  •	create Load Balancer
  LB gets successfully created. verify open LB -copy DNS name, paste in browser - see if it works

1. Now Go to **EC2 instances**
2. connect to the EC2 server
   ```
   $clear; $pm2 start app.js
   ```
3. To verify copy the public ip & paste in browser along with port no (ex : 65.0.32.220:8080)
4. Output - No error , Displays the Line so works 

