# AWS LAMBDA 

## Serverless-Architecture:

Previously we used work on not just coding , but also the infrastructure building and maintaining in order to run our applications smoothly.
So they came up with server-less computing where developers asked only to focus on Code and not the underlying architecture.
This saved time &  improved performance of the developers.

## AWS Lambda
  
  AWS Lambda is a **server-less computing service** that allows you to run programs without having to worry about provisioning, maintaining, or waiting for servers to be built
  
  Lambda handles provisioning and scaling of the resources i.e  takes care of  - OS, security , networking & other dependencies and User only provides the application code.
  
  Auto scales based on demand/ traffic.

## Serverless Computing :
  Technology of **abstracting the servers, OS the infrstructure** . 
  A cloud computing execution model in which the cloud provider dynamically **manages the allocation of machine resources**.
  
### Advantages:
  * No maintance of servers.
  * scalable/flexible
  * no need to pay for idle capacity resources.
  * cost effective.

 ### AWS Lambda Features Server-less: 
 
•	Run code without provisioning or maintaining a server. 
•	Automatic Scaling: Scale your applications automatically as per the workload. 
•	Pay per use: Billed per millisecond of use.
•	Consistency: Performance consistency is achieved by selecting the right memory size for the function. 
•	Language support: AWS Lambda supports multiple programming languages.

### Lambda Functions:
  Lambda is a **Event driven function**.

#### Event source - any aws service , custom application stream of data or queue that triggers lambda function to run.

Lambda contains a Function that *executes the programming code in one of the supported programming languages*. 
The user can bring the code without changing its bulk, but a function handler must be included. 

•	The function handler has two objects: the event object and the context object. 
    •	Event Object: Allows the event source to pass information to the Lambda function. 
    •	Context Object: Contains information specific to the runtime environment of the programming language used and allows communication within the function. 
The configuration of the code specifics depends on the programming language used.

### Lambda Event Sources Types:

  •	Push-based model -  a service that directly triggers Lambda
    o	Synchronous - Lambda returns a response back to the event source
    o	Asynchronous - Lambda does handle retries
  
  •	Pull-based model -Information is flowing through a stream or put in a queue that Lambda periodically polls, and it then goes into action when certain events are detected 
    o	Stream: Lambda will stop polling while it retries the message.
    o	 Queue: Lambda will return the message to the queue if the invocation fails or times out but will also keep retrying until it’s either successful or expires.
  

#### Workflow:
  Uploading an image to s3 bucket is an event. s3 is the event source,  such an  Event can be configured to trigger lambda function to perform actions to send an email notification.

#### Note on Lamda service usage using lambda functions:
  Used to remove/delete stale resources, in order ro cut cost/optimize them by giving conditions such as a resource that is unused for upto 30 days are considered as stale & terminated.

### Access Permissions:

  •	Security is crucial when dealing with Lambda because of its power to run code and take actions that affect other AWS services. 

•	**Two types** of security **permissions**:
    o	Invocation permissions 
    o	Execution roles. 

•	**Invocation** permissions are only needed for push event sources 
    o	granted through an **IAM resource policy automatically** created when **configuring** an AWS service as an **event source**.

•	 Execution roles grant Lambda permissions to interact with other AWS services. 
    o	They include an IAM policy defining **what Lambda is allowed to do** 
    o	**Trust policy** allowing Lambda to **assume the execution role** and perform actions on the other service.

### Pricing :
  
  Lambda's free tier allows you to use 1 million requests and 400,000GB seconds per month. 

### Parts of Lambda Cost:

  1.	Number of Requests.
  2.	Gigabit Seconds (Amount of Time X Amount of Resources)
     
  •	A Lambda request starts each time it executes the function in response to an event trigger. 
  •	Gigabit seconds are the **amount of time your function runs multiplied by the amount of memory** it uses.
  
### Limitations :

  •	Lambda function can only run for **15 minutes maximum**.
  •	 Functions must adhere to a **10 GB RAM and 10 GB storage** limit. 

### Monitoring: 

•	Lambda integrates with **CloudWatch and X-Ray** for monitoring and troubleshooting.
•	 CloudWatch monitors the number of invocations, duration of each **request, errors, and other metrics**.
•	 Lambda Insights is an additional **monitoring extension** that provides **aggregate information for all functions** in your account or region. 
•	X-Ray is a **monitoring and troubleshooting tool** that allows you to view requests as they travel through your application and identify bottlenecks and errors. 
•	TCP/IP and network traffic information are **unavailable by default** for Lambda but may be available through Flow Logs " if Lambda runs inside a Virtual Private Cloud (VPC)" .

### Lambda Containers :
Containers package all necessary code and dependencies to run a program into a small bundle that can be run on any machine or OS.



