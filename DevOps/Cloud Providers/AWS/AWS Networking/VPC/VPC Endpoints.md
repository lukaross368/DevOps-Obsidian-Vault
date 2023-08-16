#devops #cloud #VPC #networking #AWS 

### What are VPC Endpoints? 

A VPC endpoint is a way of connecting a VPC to another AWS hosted Service (ones that don't live inside VPCs) over the AWS network. For example [[S3]] buckets or [[Dynamo DB]]

### Why do you want to use VPC Endpoints? 

Private connection that doesn't go over the internet. 
Also going in and out to the internet is slower. 
Also its Cheaper than going via public internet

### Key features of VPC endpoints

- highly available and scalable virtual devices 
### Types of VPC endpoint 

- Gateway Endpoints
- Interface Endpoints

#### Gateway Endpoints

Can only be used with S3 and Dynamo DB.
We create a Gateway Endpoint and with an update in the routing table in our VPC we navigate  traffic through that Endpoint to privately communicate with S3 or Dynamo DB without any Public IP addresses

#### Interface Endpoints

#todo 