#devops 
#cloud 
#AWS 
#VPC 
#security 

A security group acts as a firewall (see: [[Firewalls]]) that controls the traffic allowed to and from the resources in your virtual private cloud ([[VPC]]). You can choose the ports and protocols to allow for inbound traffic and for outbound traffic.

For each security group, you add separate sets of rules for inbound traffic and outbound traffic.

- When you create a security group, you must provide it with a name and a description.

- Security groups are stateful. For example, if you send a request from an instance, the response traffic for that request is allowed to reach the instance regardless of the inbound security group rules. Responses to allowed inbound traffic are allowed to leave the instance, regardless of the outbound rules.

Best practices

- Authorize only specific [[IAM]] principals to create and modify security groups.

- Create the minimum number of security groups that you need, to decrease the risk of error. Use each security group to manage access to resources that have similar functions and security requirements.

- When you add inbound rules for ports 22 (SSH) or 3389 (RDP) so that you can access your [[EC2]] instances, authorize only specific [[IP addresses]] ranges. If you specify 0.0.0.0/0 ([[IPv4]]) and ::/ ([[IPV6]]), this enables anyone to access your instances from any IP address using the specified protocol.

- Do not open large port ranges. Ensure that access through each port is restricted to the sources or destinations that require it.

- Consider creating [[NACL]]'s with rules similar to your security groups, to add an additional layer of security to your VPC. 