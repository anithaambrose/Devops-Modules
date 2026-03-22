# DNS - Domain Naming System 

 DNS is **domanin naming system** , a service that translates **human-reable domain name to machine reable IP addresses**.

 **Directory service** that maps domain name to its corresponding IP addresses.

 DNS is a **resolver** 

 # AWS Route53 

**Highly available and scalable** domain name system (DNS) web service that performs **3** main functions.
  
    * Domain Registration.
    * DNS Routing.
    * Health Checking.

### Feature of Route53:
1. **DNS Registration & management**
       Allows users to **register & maintain** the domain name, if domain already exists they can configure the existing domain

2. **Traffic Management (Routing & Load Balancing)**
     * Traffic Routing - Based on geolocation, latency, health, and other factor
     * Health checks - keeps an eye on your website’s or application’s health and performance
     * DNS failover - If failover happens , we can create a backup plan by configuring in route53 by setup fallback for applications.
   
4. **Global DNS Resolver**
      Uses worldwide network & many DNS servers that are placed together, users can immediately access the website with low latency & high perfomance.

### Benefits of Route53:    
  
  * Flexible
  * Cost effective
  * Hisghly available & reliable
  * scalable

### Concepts of Route53:

1. Domain Registration - domain name , registar, registry, reseller, Top-level domain (TLD)
2. Domain Name system - DNS query, CIDR block, DNS resolver, DNS, hosted Zone, name servers, Private DNS, record , routing policy, subdomain, Time to live (TTL)
3. Routing Policy
    * Simple Routing - Use to route internet traffic to a single resource 
    * Failover Routing - routes traffic to another or alternate resource when the previous resource is unhealthy, uses ELB on active mode and the other on standby mode for easy switch on failover.
    * Geolocation Routing - route internet traffic to your resources based on the location of your users.
    * Geoproximity Routing - resources based on the geographic location of users and their resources based on the geographic location of users 
    * Latency Routing - route traffic to the resource that provides the best latency.
    * IP-based Routing - route traffic based on the location of your users, and have the IP addresses that the traffic originates from.
    * Multi-Value answer Routing - used to respond to DNS queries with up to eight healthy records selected at random.
    * Weighted Routing - routes multiple resources with a single domain name and controls the traffic to be routed to each resource , used for testing environments.
  
      

   
    
