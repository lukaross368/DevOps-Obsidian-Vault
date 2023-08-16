#devops 
#cloud 
#networking 
#AWS 

#### What is an availability zone?

AWS Cloud computing resources are housed in highly available data centre facilities.
To provide additional scalability and reliability, these data centre facilities are located in different physical locations. These locations are categorized by _regions_ and _Availability Zones_.

AWS [[Regions]] are large and widely dispersed into separate geographic locations.

Availability Zones are distinct locations within an AWS Region that are engineered to be isolated from failures in other Availability Zones. They provide inexpensive, low-latency network connectivity to other Availability Zones in the same AWS Region.

For example, to describe the Availability Zones within the US East (N. Virginia) Region (us-east-1) that are enabled for your account, run the following command:

```
aws ec2 describe-availability-zones --region us-east-1
```

