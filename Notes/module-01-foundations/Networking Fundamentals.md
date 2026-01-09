**Networking Fundamentals**
An IP address identifies a location of a resource within a network. There are two parts to it; one part identifies the network, and another part identifies the host within the network.

There are two types of IP addresses.

<img width="711" height="507" alt="Screenshot from 2026-01-09 12-01-27" src="https://github.com/user-attachments/assets/de087c39-a96e-4304-992c-1c0ff0db5e15" />


**IPv6** was developed in 1998 to replace IPv4. IPv6 uses 128-bit addresses. IPv6 addresses are eight groups of four hexadecimal digits for a total of 128 bits. The groups are written with a colon as a separator. 

A full IPv6 address is often expressed in a shortened form; for example, 50b2:6400:0000:0000:0000:6c3a:b17d:0:10a9 can be written as 50b2:6400::6c3a:b17d:0:10a9.

IPv6 uses 128-bit (2128) addresses, allowing 3.4 x 1038 unique IP addresses. This is equal to 340 trillion trillion trillion IP addresses, so all devices can have a unique address. 

IPv6 supports automatic configuration.


To summarize, the network can be identified by using 16-28 bits in the 32 bit IPv4 address.
Correspondingly, the resources in the subnet can be identified by using 4-16 bits in the 32 bit IPv4 address.

**Amazon Virtual Private Cloud**

Amazon VPC is your network environment in the cloud. With Amazon VPC, you can launch AWS resources into a virtual network that you have defined. 
VPCs deploy into one of the AWS Regions and can host resources from any Availability Zone within its Region. You can use both IPv4 and IPv6 in your VPC for secure and easy access to resources and applications.
A VPC is a virtual network dedicated to your AWS account.

**VPC Components**

**Public subnets**
A public subnet is associated with a route table that has a route to an internet gateway. It lets you reach resources inside that subnet from the public internet by assigning public IP addresses. Your public subnet configuration acts as a two-way door—allowing traffic to flow either direction, invited or not invited.

Public subnets use the following:
-Internet gateways allow communication between resources in your VPC and the internet.
-Route tables are set of rules that the VPC uses to route network traffic. In a public subnet, it includes a route to the internet gateway.
-Public IP addresses can be reached from the internet. 
-Private IP addresses are only reachable on the network.

<img width="705" height="231" alt="Screenshot from 2026-01-09 12-32-05" src="https://github.com/user-attachments/assets/8fda7b21-b530-4d7c-91d3-736c7f53f8b0" />

**Internet gateway**
An internet gateway is a horizontally scaled, redundant, and highly available VPC component that permits communication between instances in your VPC and the internet. It imposes no availability risks or bandwidth constraints on your network traffic. An internet gateway supports IPv4 and IPv6 traffic.

An internet gateway serves two purposes: 

Provides a target in your route table for internet-routable traffic.

Protects IP addresses on your network by performing network address translation (NAT).

An internet gateway performs network address translation (NAT) by mapping public and private IP addresses. In this example, the internet gateway translates the source IP address of a request from the private IP address used on the network (172.31.2.15), to the public IP address (54.56.9.10). The recipient directs its response to the public IP address. 
The internet gateway receives the response and translates the public IP address to the matching private IP address. The VPC routes the response to the requester.

<img width="671" height="414" alt="Screenshot from 2026-01-09 12-33-31" src="https://github.com/user-attachments/assets/d2d0fdac-d8ed-4470-8d3c-7fab2f240dcd" />

**Route Table**

A route table contains a set of rules (routes) that are used to determine where network traffic is directed. When you create a VPC, it automatically has a main route table. 
Initially, the main route table (and every route table in a VPC) contains only a single route: This is a local route that permits communication for all the resources within the VPC. You can't modify the local route in a route table. Whenever you launch an instance in the VPC, the local route automatically covers that instance. 
You can create additional custom route tables for your VPC.

<img width="671" height="317" alt="Screenshot from 2026-01-09 12-35-12" src="https://github.com/user-attachments/assets/7d5735c8-f271-4e2e-b74b-8bf42fdb741a" />

**Private Subnets**
Private subnets allow indirect access to the internet. Traffic stays within your private network. A private IP address assigned to an EC2 instance will never change unless you manually assign a new IP address on the network interface of the EC2 instance. 

While you can put web-tier instances into a public subnet, we recommend that you put web-tier instances inside private subnets behind a load balancer placed in a public subnet.

<img width="699" height="380" alt="Screenshot from 2026-01-09 12-36-48" src="https://github.com/user-attachments/assets/d5cf9638-b77c-417e-89f9-14d501cd0e7d" />

**Deafault VPC**

Each AWS account comes with a default  VPC that is preconfigured for you to use immediately. You don't have to create and configure your own VPC. This diagram is a default VPC. 
The CIDR block for the default VPC is always a /16 subnet mask. In this example, the CIDR block of 172.31.0.0/16 means that this VPC can provide up to 65,536 IP addresses. It includes one public subnet in each Availability Zone in the Region. These subnets use a /20 subnet mask, providing 4,096 addresses per subnet.
It also includes an internet gateway. The VPC uses a main route table to connect the subnets to the internet gateway.

<img width="699" height="375" alt="Screenshot from 2026-01-09 12-38-27" src="https://github.com/user-attachments/assets/5426fc47-d082-423f-b4a3-59a636af8c34" />



