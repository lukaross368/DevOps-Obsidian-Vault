#devops 
#cloud 
#networking 
#AWS 

#### What are local zones?

Local Zones are an extension of AWS [[Regions]] that are geographically close to your users.
You can extend any [[VPC]] from the parent AWS Region into Local Zones. 

To do so, create a new subnet (see: [[AWS Subnet]]) and assign it to the AWS Local Zone. When you create a subnet in a Local Zone, your VPC is extended to that Local Zone. The subnet in the Local Zone operates the same as other subnets in your VPC.