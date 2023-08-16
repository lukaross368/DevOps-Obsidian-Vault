#AWS #devops #networking #cloud #VPC 


We can use VPC Peering (See [[Peering]] for a more general explanation from a networking perspective) to connect two or more VPC together so they can communicate.

Remember that VPC peering is a 1-to-1 relationship, in other words, for a VPC to talk to another VPC we need an explicit VPC peering between those two VPCs (Edge nodes cannot talk to each other)

#### Some key details

- Full Private IP connectivity between two VPCs
- Can Peer VPCs across [[Regions]]
- VPCs can be in different accounts
- VPC CIDR ranges must not overlap (see [[CIDR Notation]])

### Setup 

setup is a decentralised process

1) owner of a VPC sends a peering request to owner of another
2) peering request is accepted 
3) update routing tables on both sides using peering connection as the destination 