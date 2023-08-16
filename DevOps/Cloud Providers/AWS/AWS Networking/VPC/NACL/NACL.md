#devops 
#networking 
#cloud 
#VPC 
#security 
#AWS 

A _network access control list (NACL)_ allows or denies specific inbound or outbound traffic at the subnet level (see: [[AWS Subnet]]).

You can use the default NACL for your [[VPC]], or you can create a custom NACL for your VPC with rules that are similar to the rules for your [[Security Groups]] in order to add an additional layer of security to your VPC.

The following diagram shows a VPC with two subnets. Each subnet has a NACL. 
When traffic enters the VPC,  the router sends the traffic to its destination. NACL A determines which traffic destined for subnet 1 is allowed to enter subnet 1, and which traffic destined for a location outside subnet 1 is allowed to leave subnet 1. 
Similarly, NACL B determines which traffic is allowed to enter and leave subnet 2.

![[NACL example.png]]