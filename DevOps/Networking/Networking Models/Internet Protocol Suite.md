#devops 
#networking 

The **Internet protocol suite**, commonly known as **TCP/IP**, is a framework for organizing the set of [[Network Protocols]] used in the Internet and similar computer networks according to functional criteria.

The foundational protocols in the suite are the Transmission Control Protocol (see [[TCP]] ) , the User Datagram Protocol (see [[UDP]]), and the Internet Protocol (see [[IP]]).

### Application Layer

This layer includes protocols used by most applications for proving user services and exchanging application data over the network. Examples of application layer protocols are [[HTTP]] and [[DHCP]].

### Transport Layer 

TCP and UDP take place in the transport layer. 

Once the application layer gets the data it wants to communicate from the application, it will then communicate with the transport layer via a port.  Ports can be assigned different protocols i.e. Port 443 for HTTPS. 

Once it has the data from the application layer, the transport layer chops it into Data Packets, which it then sends across the network with the help of a [router](Routers).

### Internet Layer

Uses IP.
Packets are routed with the help of [[IP addresses]]. 

### Link Layer

The protocols of the link layer operate within the scope of the local network connection to which a host is attached. The link layer is used to move packets between the Internet layer interfaces of two different hosts on the same link.




