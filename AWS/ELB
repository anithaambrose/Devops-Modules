## ELB - Elastic Load Balancer

Load Balancer is used to control & distribute incoming traffic for efficient use of resources.

ELB an AWS Elastic Load Balancer is a web service provided by AWS which incoming traffic is efficiently & automatically distributes  across multiple targets and virtual appliances in one or more Availability Zones (AZs).

Based on availabilty of the target the load gets distributed.
Availability is checked every 30 seconds based on healthy & unhealthy checks (ping requests to servers(targets)) .

Benefits:

1. Security
Secure your applications with SSL/TLS termination, integrated certificate management, and client certificate authentication.

2. Automatic scaling
Deliver applications with high availability and automatic scaling.

3. Monitor in real time
Monitor the health and performance of your applications in real time, uncover bottlenecks, and maintain SLA compliance.

Types of ELB:
1. Application Load Balancer
2. Network Load Balancer
3. Gateway Load Balancer

When you use Elastic Load Balancing with Auto Scaling, you can build highly available, fault-tolerant applications which automatically scale capacity up or down based on fluctuations in demand.

Application Load Balancer:

Application Load Balancers intelligently provide scalability, performance, and availability. They also guarantee that your servers are not overworked and are prepared to handle traffic spikes.

Application Load Balancer, aka ALB, is an Elastic Load Balancer or ELB on AWS. It operates at the application layer (the seventh layer) of the Open Systems Interconnection (OSI) model.

The Application Load Balancer distributes incoming HTTP and HTTPS traffic across multiple targets.

Benefits of ALB:

Support for Path conditions: You can configure your listener with rules that forward requests based on the URL in the request. This allows you to break down your application into smaller services (microservices) and route requests to the appropriate service based on the URL’s content.

Support for Host conditions: You can configure your listener with rules that forward requests based on the host field in the HTTP header. This allows you to route requests to many domains using a single load balancer.

Routing is supported based on request information such as HTTP header conditions and methods, query parameters, and source IP addresses.

You can send routing requests to numerous applications on a single EC2 server.

An instance or IP address can be registered with numerous target groups on a separate port.


Network Load Balancer:

Network Load Balancer operates at the connection level (Layer 4), routing connections to targets (Amazon EC2 instances, microservices, and containers) within Amazon VPC, based on IP protocol data.

Ideal for load balancing of both TCP and UDP traffic, Network Load Balancer is capable of handling millions of requests per second while maintaining ultra-low latencies.

Network Load Balancer is optimized to handle sudden and volatile traffic patterns while using a single static IP address per Availability Zone.

It is integrated with other popular AWS services such as Auto Scaling, Amazon EC2 Container Service (ECS), Amazon CloudFormation, and AWS Certificate Manager (ACM).

Features of Network Load Balancer:

Connection-based Layer 4 Load Balancing
Low Latency
Static IP and Elastic IP support
Integration with Amazon Route 53
Integration with AWS Services

How Network Load Balancer Works:

Clients make requests to your application.

The load balancer receives the request either directly or through an endpoint for private connectivity (via AWS PrivateLink).

The listeners in your load balancer receive requests of matching protocol and port, and route these requests based on the default action that you specify. 
You can use a TLS listener to offload the work of encryption and decryption to your load balancer.

Healthy targets in one or more target groups receive traffic according to the flow hash algorithm

Gateway Load Balancer:
Gateway Load Balancer helps you easily deploy, scale, and manage your third-party virtual appliances. 
It gives you one gateway for distributing traffic across multiple virtual appliances while scaling them up or down, based on demand. 
This decreases potential points of failure in your network and increases availability.

Benefits:

Scale your virtual appliance instances automatically.
Bring higher availability to your third-party virtual appliances.
Monitor continuous health and performance metrics.

How Gateway Load Balancer Works:

Clients make requests to your application.

The load balancer receives the request based on the route table configurations that are set within your VPC, Internet Gateway, or Transit Gateway.

The load balancer routes requests to a target group consisting of a scalable fleet of appliances (for example, firewalls, deep packet inspection systems, URL filtering systems etc.) to process traffic flows.

The virtual appliance processes the traffic, and forwards it back to the load balancer, or drops the traffic based on its configuration. 
This type of load balancer acts as a bump-in-the-wire between the source and destination.

The load balancer forwards the traffic to its destination.
