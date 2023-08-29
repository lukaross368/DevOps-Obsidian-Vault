#devops 
#cloud 
#AWS 
#networking 
#subnet 
#VPC 

This page is about subnets in the context of an AWS VPC, follow this link for more general information on [subnetworks](Subnetwork.md).

Each subnet must reside entirely within one [[Availability Zones]] and cannot span zones.

Subnets can be public or private. If a subnet is associated with a route table (see: [[VPC Route Tables]]) that has a route to an [[Internet Gateway]], it's known as a _public subnet_. If a subnet is associated with a route table that does not have a route to an internet gateway, it's known as a _private subnet_.

This has lots of security benefits, but say for example we have a public and private subnet in our VPC. We host our web servers in the public subnet as these should be accessible from the internet, and then deploy some databases or instances of a backend application in our private subnet. What if those instances need to connect to the internet to install dependency upgrades, but should not be accessible otherwise? 

This is where the [[NAT Gateway]] comes in! A NAT gateway acts as a one-way valve for traffic from a private subnet in our VPC out to the internet.

We can define A _subnet_ as a range of [[IP addresses]] in your [[VPC]]. You can create AWS resources, such as [[EC2]] instances, in specific subnets.

