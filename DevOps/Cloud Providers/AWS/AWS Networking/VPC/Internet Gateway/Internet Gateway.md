#devops 
#cloud 
#AWS 
#networking 
#VPC

An internet gateway is a horizontally scaled, redundant, and highly available [[VPC]] component that allows communication between your VPC and the internet.

It supports IPv4 and IPv6 traffic.

An internet gateway enables resources in your public subnets (see: [[AWS Subnet]]) (such as [[EC2]] instances) to connect to the internet if the resource has a public [[IPV4]] address or an [[IPV6]] address. Similarly, resources on the internet can initiate a connection to resources in your subnet using the public IPv4 address or IPv6 address. For example, an internet gateway enables you to connect to an EC2 instance in AWS using your local computer.

An internet gateway provides a target in your [[VPC Route Tables]] for internet-routable traffic.

To enable access to or from the internet for instances in a subnet in a VPC using an internet gateway, you must do the following:

-  Create an internet gateway and attach it to your VPC.
-  Add a route to your subnet's route table that directs internet-bound traffic to the internet gateway.
- Ensure that instances in your subnet have a public IPv4 address or an IPv6 address.
- Ensure that your network access control lists [[NACL]] and security group (see: [[Security Groups]]) rules allow the desired internet traffic to flow to and from your instance.

AWS diagram symbol. 

![[Internet gateway icon.png]]


