# ELB - Elastic Load Balancer

### Load Balancer is used to control & distribute incoming traffic for efficient use of resources.

## ELB - Elastic Load Balancer is a web service provided by AWS by which incoming traffic is efficiently & automatically distributed across multiple targets and virtual appliances in one or more Availability Zones (AZs).

### Benefits:

1. Security - Secure your applications with SSL/TLS termination, integrated certificate management, and client certificate authentication.

2. Automatic scaling - Deliver applications with high availability and automatic scaling.

3. Monitor in real time - Monitor the health and performance of your applications in real time, uncover bottlenecks, and maintain SLA compliance.


## Types of ELB:

1. Application Load Balancer
2. Network Load Balancer
3. Gateway Load Balancer

When you use Elastic Load Balancing with Auto Scaling, you can build highly available, fault-tolerant applications which automatically scale capacity up or down based on fluctuations in demand.

# when to choose ALB or NLB?

Choosing between an Application Load Balancer (ALB) and a Network Load Balancer (NLB) depends primarily on whether you need intelligent, content-based routing (Layer 7) or extreme performance with low latency (Layer 4)

## Application Load Balancer:

The Application Load Balancer distributes incoming HTTP and HTTPS traffic across multiple targets based on URL path (/api, /blog), hostnames, HTTP headers, or query strings.

It intelligently provide scalability, performance, and availability & also guarantees that your servers are not overworked and are prepared to handle traffic spikes.

ALB operates at Layer 7 (Application Layer) of the OSI model and is the best choice for modern, content-aware web applications, APIs, and microservices.

### Benefits of ALB:

- Support for **Path** conditions: You can configure your listener with rules that **orward requests based on the URL** in the request.
This allows you to break down your application into smaller services (microservices) and route requests to the appropriate service based on the URL’s content.

- Support for **Host** conditions: You can configure your listener with rules that **forward requests based on the host field in the HTTP header**. 
This allows you to route requests to many domains using a single load balancer.

Routing is supported based on request information such as HTTP header conditions and methods, query parameters, and source IP addresses.

You can send routing requests to numerous applications on a single EC2 server.

An instance or IP address can be registered with numerous target groups on a separate port.

```
- Works at Layer 7 (application Layer)
- supports host & path based routing 
- Ideal for HTTP/HTTPS traffic
- Use Case	Web Apps, Microservices, REST APIs
```

### ALB components:

1. listener :  checks for connection requests from clients, using the protocol and port that you configure.

2. Rules that you define for a listener determine how the load balancer routes requests to its registered targets. Each rule consists of a priority, one or more actions, and one or more conditions.

   When the conditions for a rule are met, then its actions are performed. You must define a default rule for each listener, and you can optionally define additional rules.
3. Target group : TG routes requests to one or more registered targets, such as EC2 instances, using the protocol and port number that you specify.
    You can register a target with multiple target groups. You can configure health checks on a per target group basis. Health checks are performed on all targets registered to a target group that is specified in a listener rule for your load balancer.

[ALB architecture](https://docs.aws.amazon.com/images/elasticloadbalancing/latest/application/images/component_architecture.png)

## Network Load Balancer:

* Network Load Balancer designed to handle millions of requests per second with ultra-low latency , operates at the transport layer of OSI (Layer 4).

* NLB Routes connection requests to targets (Amazon EC2 instances, microservices, and containers) within Amazon VPC, based on IP protocol data.

* Ideal for load balancing of both TCP and UDP traffic,

* Network Load Balancer is optimized to handle sudden and volatile traffic patterns while using a single static IP address per Availability Zone.

* It is integrated with other popular AWS services such as Auto Scaling, Amazon EC2 Container Service (ECS), Amazon CloudFormation, and AWS Certificate Manager (ACM).

### Features of Network Load Balancer:

* Connection-based Layer 4 Load Balancing
* Low Latency
* Static IP and Elastic IP support
* Integration with Amazon Route 53
* Integration with AWS Services

 ```
 - Works at Layer 4 (Transpot layer)
 - Supports Ip & Port based routing.
 - Ideal for TCP/UDP traffic
 - Use Case	- 	Gaming, Streaming, IoT, SaaS
 ```

 ## Gateway Load Balancer:

Gateway Load Balancer helps you easily deploy, scale, and manage your third-party virtual appliances. 

It gives you one gateway for distributing traffic across multiple virtual appliances while scaling them up or down, based on demand. 

This decreases potential points of failure in your network and increases availability.

### Benefits:

* Scale your virtual appliance instances automatically.
* Bring higher availability to your third-party virtual appliances.
* Monitor continuous health and performance metrics.

### How Gateway Load Balancer Works:

Clients make requests to your application.

The load balancer receives the request based on the route table configurations that are set within your VPC, Internet Gateway, or Transit Gateway.

The load balancer routes requests to a target group consisting of a scalable fleet of appliances (for example, firewalls, deep packet inspection systems, URL filtering systems etc.) to process traffic flows.

The virtual appliance processes the traffic, and forwards it back to the load balancer, or drops the traffic based on its configuration. 
This type of load balancer acts as a bump-in-the-wire between the source and destination.

The load balancer forwards the traffic to its destination.

```
The "Double" Load Balancer Pattern
If you need the advanced routing features of an ALB (Path-based routing, WAF) but also need static IP addresses (from NLB), you can place an NLB in front of an ALB. 

Default to ALB for most web workloads, and choose NLB specifically for the performance, IP, or protocol requirements.
```
