#devops 
#cloud 
#AWS 
#networking 
#VPC 
#security 

[[VPC]] Flow Logs is a feature that enables you to capture information about the IP traffic going to and from network interfaces in your VPC.

Flow Log data can be published to an [[S3]] Bucket.

After you create a flow log, you can retrieve and view the flow log records in the log group, bucket, or delivery stream that you configured.

Flow logs can help you with a number of tasks, such as:

- Diagnosing overly restrictive security group rules
- Monitoring the traffic that is reaching your instance
- Determining the direction of the traffic to and from the network interfaces

You can create a flow log for a VPC, a [[AWS Subnet]], or a particular instance.

Flow logs do not contain the payload data of your packets. They only contain the description of the packets. 

