#devops 
#networking 
#osi

Open Systems Interconnect Model explains the 7 layers of communication of an org and their applications and is fundamental to the design of networks.

## Layer 1 - Physical 

1st and lowest layer. It's the layer most closely associated with the physical connection between devices.  It provides an electrical, mechanical and procedural interface to the transmission medium.

The Physical layer defines the means of transmitting a stream of raw bits over a physical data link connecting network nodes. The Physical layer consists of the electronic circuit transmission technologies of a network. 

Within the semantics of the OSI model, the physical layer translates logical communications requests from the data link layer into hardware-specific operations to cause transmissions or reception of electronic signals. 

## Layer 2 - Data Link

This layer is the protocol layer that transfers data between nodes in the physical layer. The data link layer provides the functional and procedural means to transfer data between network entities, and may also provide the means to detect and possibly correct errors that can occur in the physical layer.

Examples of data link protocols are Ethernet and Wi-Fi protocols.

Components of the Data link layer have [[MAC Addresses]] 

The data link provides for the transfer of data frames between hosts connected to the physical link.

The frame header contains the source and destination addresses that indicate which device originated the frame and which device is expected to receive and process it.

## Layer 3 - Network

The network layer is responsible for packet forwarding including routing through [[Routers]]

Sometimes called the logical addressing layer, it determine the address and the path to get your data through the network. In layer 3 we are using IP addresses and sending packets.

The network layer provides the means of transferring variable-length network packets from a source to a destination host via one or more networks. 

## Layer 4 - Transport 

The protocols of this layer provide end-to-end communication services for applications.

The best-known transport layer protocol is [[TCP]]. It is used for connection-oriented transmissions, whereas the connectionless [[UDP]] is used for simpler messaging transmissions.

Together, TCP and UDP comprise essentially all traffic on the Internet and are the only protocols implemented in every major operating system.

## Layer 5 - Session

The session layer provides the mechanism for opening, closing and managing a session between end-user application processes, i.e., a semi-permanent dialogue.

Within the service layering semantics of the OSI network architecture, the session layer responds to service requests from the presentation layer and issues service requests to the transport layer.

## Layer 6 - Presentation 

Within the service layering semantics of the OSI network architecture, the presentation layer responds to service requests from the application layer and issues service requests to the session layer through a unique presentation service access point (PSAP).

The presentation layer ensures the information that the application layer of one system sends out is readable by the application layer of another system. 

On the sending system, it is responsible for conversion to standard, transmittable formats. On the receiving system it is responsible for the translation, formatting, and delivery of information for processing or display.

## Layer 7 - Application 

The application layer specifies the shared communications protocols (see [[Network Protocols]]) and interface methods used by hosts in a communications network

The OSI model defines the application layer as only the interface responsible for communicating with host-based and user-facing applications.


