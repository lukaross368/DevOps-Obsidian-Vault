#devops 
#networking 
#IP 

An **Internet Protocol address** (**IP address**) is a numerical label such as _192.0.2.1_ that is connected to a computer network that uses the Internet Protocol (see [[IP]]) for communication. 

An IP address serves two main functions: network interface identification and location addressing.

Every Device has to have an IP address for communication purposes

[[IPV4]] defines an IP address as a 32-bit number. Due to depletion of available IPV4 address, a new version of IP ([[IPV6]]), using 128 bits for the address, was standardized in 1998.

Address are written and displayed in human-readable notations. 

- 192.0.2.1 (IPV4)
- 2001:db8:0:1234:0:567:8:1 (IPV6)

The size of the routing prefix of the address is designated in [[CIDR Notation]] by suffixing the address with the number of significant bits, e.g., _192.0.2.1/24_, which is equivalent to the historically used [[Subnet Mask]] _255.255.255.0_.

IP addresses consist of 2 parts, A network address and host address. The reason IP addresses are broken down into network and host addresses is to break a large network into subnetworks (See: [[Subnetwork]]). This allows more efficient communication of large networks, since the large networks can be broken down into subnetworks. [[Routers]] control the flow of data between subnets 

