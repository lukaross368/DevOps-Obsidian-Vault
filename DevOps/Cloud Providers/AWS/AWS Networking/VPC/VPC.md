#devops #cloud #AWS #networking 

### Overview 

#### What is a VPC?

Virtual Private Cloud (VPC)

Your own Network in the cloud.

Essentially acts as a Cloud Data Centre for you to deploy and host cloud services in a safe and practical way.  

Say for example we have a AWS [region](Regions.md) which is made of of some [[Availability Zones]]. A VPC is the isolated network zone that spans all availability zones in a region. Now we may want to Deploy some [[EC2]] or [[RDS]] instances into our availability zones. We can also setup subnets in our VPC (see: [[AWS Subnet]]) to partition our network. A Subnet can only span 1 availability zone. 

Key points: 

- VPC is an isolated network within a region. 
- VPCs Span all availability zones in a region.
- Subnets partition the VPC into smaller subnetworks
- A Subnet can only span 1 availability zone. 

![[VPC diagram.png]]

You can Setup an internal IP range for your VPC ([[IPV4]] or [[IPV6]]). Each subnet will take a subset of that VPC IP range (determined by some subnet mask) 

VPCs, by default, come with an [[Internet Gateway]]. The internet gateway manages communication from your VPC to the Internet and visa versa. 

[[Security Groups]] are security rules which can be applied on a 'per instance' level in a VPC. On a higher level than security groups we have a [[NACL]] which applies security rules on the Subnet level. We can see logs of the IP traffic in [[Flow Logs]]

![[VPC - controlling access.png]]

What about routing? 

By default we get a route table (see: [[VPC Route Tables]]), which can control how network traffic is routed when leaving your VPC. You can also control routing between subnets (just like a router in a real network!)

#### Why do we need a VPC?

We want our network to be isolated in the cloud so we can manage multiple networks on our AWS account that are isolated from each other. 

Even if we don't need multiple networks in the cloud, AWS services (things like EC2 instances) need a network to be deployed into. Setting up a VPC with the correct configuration for your particular use case(s) is definitely best practice.

Also we more easily and preciously control access to our resources with a VPC.

#### DNS Services

VPC by default provides DNS resolution but you should consider [[Route 53]] when thinking about DNS in your custom VPC.

#### Basic Setup Steps

- Select CIDR range (see [[CIDR Notation]])
- Divide [[IP addresses]] range into Subnets
- Route public subnets to Internet Gateway
- Route private subnets to [[NAT Gateway]]
- Configure Security groups
- Deploy Instances 

#### Connecting Multiple VPCs

This can be done in two ways. [[VPC Peering]] or with [[Transit Gateways]]

[[VPC Endpoints]]







