# LAB 1 - creating AMI image from an Existing EC2 server.
1.	create a normal ubuntu EC2 instance 
2.	connect in instance in AWS console/ putty.
3.	run the package update command - sudo apt update 
4.	install apache2 application by the following commands
   ```
    •	confirm if in ubuntu user 
    •	$sudo apt install apache2
    •	$sudo systemctl status apache2  - if active , runs the public ip address in browser to validate 
    •	sudo systemctl stop apache2 - reload browser to verify
    •	sudo systemctl start apache2 - refresh browser to confirm apache2 service running
   ```
5.Go to console, select instance and click actions - image & templates - create image - Give an AMI name, unselect reboot option, - click on create image .
Now AMI is created , Give it a Name in the dashboard page, wait until its status changes from pending to available.

# Lab 2 - Creating an EC2 using MyAMI (created by me)

1.	Launch instance from EC2 page 
2.	Give a name to the instance
3.	click MyAMI under Applications & OS image tab
4.	Select the previously created ami from lab 1 
5.	select key pair, allow all traffic (SSH, HTTTP, HTTPS)
6.	Launch instance Copy Public IP of the EC2 and run in browser to verify if apache2 is automatically up & running when instance is created.

# Lab 3 - Launch Amazon Linux by customizing instance type & creating new Security Group .

1.	Launch an EC2 from console by selecting Amazon Linux under AMI tab
2.	Choose instance type from the drop down icon
3.	choose a key-pair for authentication
4.	under network settings click on create a security group radio button
5.	duplicate the AWS console and on the left side panel select security group - create security group
6.	Under basic details - fill the name , description
7.	Under Inbound Rule - Do not assign any configs 
8.	Under Outbound Rule - No config changes needed , just leave it with default option (custom) 
9.	Click on create SG at the bottom of the page & return to EC2  launching browser
10.	Select existing SG option since we hav enow custom created our SG.
11.	Launch the instance & connect to it in AWS console
12.	Throws Error - this is becoz , our SG has no inbound Rules so  go to SG - inbound rules, edit inbound rules- choose SSH under type and Source - Anywhere IPV4 from the drop down lists & click on Save Rules , Now refresh the AWS console Putty , now the connection is established.

# Lab 4 - Scenario - If we are not a root user i.e an IAM user & we don't have permission to create AMI images, Plus we need to Create 5 ubuntu Server + Apache2 applications we can use user data concept by giving the steps under advanced tab, while provisioning the servers.

1.	create EC2 instances →AMI, Key pair, SG -only allow SSH traffic 
2.	Under Advanced details → place the following commands so it runs while launching the instance itself, reducing the manual efforts in execution of commands/ installing applications when trying to create multiple instances.
   
      •	apt update -y
      •	#install aApche2 (hhtpd for ubuntu)
      •	apt install apache2 -y
      •	#start the Service
      •	systemctl start apache2
      •	systemctl enable apache2
      •	#optional create simple index page
  	
      ```
      echo"<h1> Hello FRom EC2 with Apache2 on ubuntu!</h1>" > /var/www/html/index.html
      ```
4. Click on Launch instance & connect to it , check if ur in ubuntu user
   $ systemctl status apache2   ; $ uptime
5. copy public IP and run it in thw browsere and verify if ubuntu has installed ,
6.	If it throws Error , edit the inbound rule by getting into the attaching SG group inbound rule section and add rule - HTTP type traffic , source- Anywhere IPV4 , save rules
7.	Refresh the browser to validate 
8.	Display Hello Msgs from index.html page
 

# Lab 5 - Installing AWS CLI in an EC2 instance 
Option -1 Using the bundle (recommended latest Version)
1.	$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -O “awscliV2.zip”
2.	$ sudo apt install unzip
3.	$ unzip awscli-exe-linux-x86_64.zip
4.	$ sudo  ./aws/install → run aws CLI package
5.	$ aws --version. → to verify if aws cli is inatlled or not 
6.	$ aws configure → give the access key , secret key go to AW S console click on account name - security credentials - create access key - copy access key & secret access key , leave region & output format blank, Go back to CLI. 
7.	$ aws s3 ls  → displays bucket info
8.	$ aws ec2 describe-regions  → displays regions & configs
9.	$ aws help
10.	$ aws ec2 describe-instances  → displays ec2 instance & its configs

    
# HW task - 1 
1.	create an instance
2.	EC2 - windows , allow http, https, ssh.
3.	Connect with RDP, open CMD in windows 
4.	share the system info.
   
Note: for windows you can use RDP in PC , give the public IP & give key (.pem/.ppk)& connect with username 
1.	RDP works on 4 digit port No → find it 
2.	Find out if .pem/.ppk should be used or password can be used to connect .
