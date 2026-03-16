# ASG - Auto Scaling Group 

## ASG is a mechanism that automatically permist to up scale / down scale the resources to meed demand based on custom-defined metrics & thresholds.

AWS EC2 ASG ensures that you have the correct number of Amazon EC2 instances available to handle the load for your application.

### Benefits:
1. Setup Scaling Quickly
2. Make Smart Scaling Decisions
3. Automatically Maintain Performance
4. Pay Only For What You Need

### Auto-Scaling Group:
An Auto Scaling group contains a collection of EC2 instances that are treated as a logical grouping for the purposes of automatic scaling and management.

### Auto-Scaling Workflow:

AWS autoscaling will scale the application based on the load of application. Instead of scaling manually AWS auto scaling will scale the application automatically
when the incoming traffic is high it will scale up the application and when the traffic is low it will scale down the application.

### Create Auto-Scaling Launch Template in AWS:

Click on the EC2(Elastic Cloud Computing).
Scroll Down and click on the Launch Templates and click on the Create launch template , Type the Template name , choose AMi and everything else as we do to create an EC2.

### Create Auto-Scaling Group using Launch Template:
1. Create an EC2 instance and Click on the Create Auto Scaling group, Type the Auto Scaling group name.
2. Select your Template.
3. Select the VPC or go with the default VPC and also select the Availability zone.
4. Configure the Group size and Scaling policies.
5. Select as per your requirement: Desired: 4, Minimum: 4, Maximum: 8
6. Select the Target tracking scaling policy.- set metrics - cpu utilization , threshold 
7. Click on the Create Auto Scaling Group.
8. Now  the Auto Scaling is creating and it is also creates the no of desired state of the EC2 Instance.
9. Desired state selected is equal to 4 and   4 Instance is Running.

