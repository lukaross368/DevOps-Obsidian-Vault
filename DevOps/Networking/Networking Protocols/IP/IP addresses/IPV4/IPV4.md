#devops 
#networking 
#IP 

32-bit numeric address written as 4 numbers separated by periods. 

Example : 192.168.1.0

- Each number separated by a dot is called an octet 
- each octet is a number ranging from 0 to 255
- first 2 octets comprise the Network address 
- last 2 octets comprise the Host address
- the network address is a number that's assigned to a particular network
- host address is what's assigned to hosts in that network such as computers, servers, routers etc.

With IP version 4 there is a concept of Public vs Private IP addresses. 

#### Public IP address

- a public IP address is registered on the internet
- they are unique
- assigned by ISP (Internet service providers)

#### Private IP address

- not publicly registered on the internet
- not unique
- a device with a private IP that wants to connect to the internet must have its IP address converted to a public address before it can access the internet
- only used internally 
- assigned by the router to internal devices using [[DHCP]]

![[PublicVsPrivateIP-001.png]]

![[PublicVsPrivateIP-002.png]]

![[PublicVsPrivateIP-003.png]]

Private addresses are converted to public addresses in order to access the internet using a service called [[NAT]] (network address translation) which is built into [[Routers]].

This also works in the opposite direction. If something on the internet wants to communicate with one of our devices on our private network, it talks to the public IP address of the router which then uses NAT to route the message to the internal private IP.

Private IP addresses have 3 different classes which use 3 default [[Subnet Mask]] to split addresses into 3 different sized ranges of which you will select depending on your use case.

![[InternalIPClasses.png]]