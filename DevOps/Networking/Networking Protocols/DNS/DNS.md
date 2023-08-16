#devops 
#networking 
#networkingProtocols 
#DNS

Domain Name System

Computers (and other network devices) use [[IP addresses]] to identify each other, whereas humans use names. DNS bridges this gap.

DNS resolves domain names to IP addresses.

When you enter a domain name into your web browser, the DNS server will search its Database to find a matching IP address for that domain name. It will then resolve that domain name to that IP.
Then your computer is able to communicate with the target network device.

First your web browser looks for the domain name lookup it its cache before contacting the DNS server. If it cant find it there it will send a query to the 'Resolver Server' (usually your ISP or 'Internet Service Provider') It then checks its own cache for the domain name lookup. 

If the resolver server cannot find it, it will then send the query to the next level. The Root server (Top of the DNS hierarchy). 

The Root server then contacts a TDL server (Top level Domain) which has stored information for top level domains such as; .COM, .NET, .ORG etc.

TDL then directs the resolver to an ANS (Authoritative Name Server) which is responsible for knowing everything about the domain (which includes IP). 

The resolver then returns the IP to your computer and stores the lookup in its cache to improve performance. 

![[DNS.png]]



