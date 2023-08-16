#devops #networking #VPC #AWS #cloud 

A second option after [[VPC Peering]] to securely connect your VPCs together.

### What is Transit Gateway?

A distributed managed routing service that is deployed into a region (see: [[Regions]]) then you can attach VPCs in that same region to.

This will allow any-to-any communicate between the VPCs which is preferable in some cases to VPC peering's 1-to-1 connection.

Transit routing has its own routing table (similar to [[VPC Route Tables]]) 

### Key details

- centralized private IP connectivity between multiple VPC's
- VPCs must be in the same region as transit gateway
- VPCs can be in different accounts
