# VPC - Virtual Private Cloud 

## VPC - Virtual Private Cloud that lets you to own a private, isolated network within a public cloud Environment.
## Provides Security, Control over networking & ability to isolate work;loads by defining IP range , subnets to control network.

## AWS VPC - Amazon VPC enable you to launch AWS resources in a private isolated network within the AWS.

### Why use an Amazon VPC:

1. You can spin up a logical environment of what was previously in a **data center within minutes** in the cloud.
2. More **cost-effective** than maintaining equipment in a company data center.
3. **pay for only the resources that you use.**
4. **secure, scalable, and reliable.**

## IP addressing in Amazon VPC:

## CIDR - Classless Inter Domain Routing:
CIDR is an **IP Allocating method** that improves data routing efficiently on the internet.

When you create a VPC, you must specify the IPv4 address range by choosing a CIDR block, such as 10.0.0.0/16.

Formats of CIDR:
```
Network Address - series of numberical digits pointing to network identifier.
Host Address - series of numberical digits indicating the host on individual devices.
```
CICD - Collection of IP address that share the same network.
IANA - assigns large CIDR to regional network and regional network assigns smaller block to local internet registries.

### IP Range Calc:
```
IP range/subnet mask => bits-subnet mask  = bits => 2^bits = Total no of ip's in range.
```
```
10.10.1.0/30 => 32-30 = 2 => 2^2 = 4
10.10.1.0/24 => 32-24 = 8 => 2^8 = 256
10.10.1.0/16 => 32-16 = 16 => 2^16 = 65536
10.10.1.0/8 => 32-8 = 24 => 2^24 = 16777216
```


#### AWS reserves the first four IP addresses and the last IP address of every subnet for internal purposes.
#### Example:
|       IP Address      |                Purpose            |
| :-------------------- | :---------------------------------|
|      10.0.0.0         |          Network address          |
|      10.0.0.1         |           VPC router              |
|      10.0.0.2         |  Domain Name System (DNS) server  |
|      10.0.0.3         |     Reserved for future use       |
|      10.0.0.255       |    Network broadcast              |


## AWS VPC components:

1. **Amazon VPC:** logically isolated environment for your resources within the cloud. You can choose a Region here.

2. **Internet Gateway:**  Component that enables instances in a VPC to connect to the internet.

**Subnet:** Logical network segments within your VPC ( segment of VPC's Ip range).
They enable you to subdivide your VPC network into smaller networks inside a single Availability Zone.
One subnet per Availability Zone because a subnet cannot span zones.

3. **Public Subnet:** public subnet is associated with a route table that has a route to an internet gateway.

4. **Private Subnet:** private subnet does not have an internet gateway on the route table that is associated to it. However, a NAT gateway can be a route on this route table.

5. **Routing Table:** Rules to control how a network traffic is drected (route+ traffic info) within a VPC.


6. **Security Group:** Firewall for instances 
SG are Statefull - Stateful means that if requests from your instance are sent, the response traffic is allowed to flow back regardless of the inbound rules. 
SG rules set are based on allow condition only with respective to Protocal, Port, IP range,  Internet Control Message Protocol (ICMP) type, and source or destination.
SG are associated with instances 

7. **NACL - Network Access Control List:** Firewall for Subnets , 
Stateless - 
Stateless means you seperately have to allow both request and response.
Network ACLs have separate inbound and outbound rules - Supports allow and deny rules.

## Difference between Security Groups & NACL:

|            Security Group:                   |            NACL                              |
| :------------------------------------------- | :--------------------------------------------|
|     Operates at the instance level           | Operates at the subnet level                 |
|        Supports allow rules only             |  Supports allow & deny rules                 |
|            Stateful                          |            Stateless                         |
|        Evaluates all rules                   |      Process rules in order                  |
| Applies to an instance only if associated    |   Automatically applies to all instances in  |

8. **Primary network interface (elastic network interface):**
An elastic network interface is a virtual network interface (NIC) that connects an instance to a network.
Each instance in a VPC has a default network interface, the primary network interface, which cannot be detached from the instance.


9. **NAT Gateway:** Network Address Translation. 
Allows access to private subnet instances to connect outside the VPC to the internet via Elastic IP address.
NAT gateway is assigned an Elastic IP address, which is a public IP address and is located in the public subnet.


### Steps to create functional Amazon VPC: 
For creating functional VPC, we must create these components:

1. VPC
2. Internet Gateway
3. Subnets
4. Route table
5. Security Groups
6. NACL






















