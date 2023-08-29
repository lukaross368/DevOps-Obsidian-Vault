#networking 
#devops 
#IP 
#subnet

A Subnet mask reveals how many bits in the IP address are used for the network by masking the network portion of the IP address.

Example:

IP Address - 

Decimal form : 192.168.1.0
Binary form : 11000000.10101000.00000001.00000000

Subnet Mask - 

Decimal form : 255.255.255.0
Binary form : 11111111.11111111.11111111.00000000

##### Key point:

The Subnet mask hides the part of the IP address that defines the network. It does this by excluding any octets of the IP address that line up with the position of a bit in the binary form of the subnet mask. I.e. for the above example, we can tell that the first 3 octets make up the network part of the address since all 3 of the octets of the subnet mask are 1s. Therefore, {192.168.1} make up the network part of the address and {.0} makes up the host part of the address. This is how subnet masks indicate network and host portions of an IPV4 address.

Check the image below for another example. 

![[Subnet mask example.png]]

