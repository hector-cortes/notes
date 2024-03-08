## Internet vs Internets
Internet - Refers to the network that began as ARPAnet and continues today as a confederation of TCP/IP networks connected directly or indirectly to the U.S. backbones
* It is composed of different networks: Commercial TCP/IP backbones, Corporate and Government TCP/IP networks, and TCP/IP networks in other countries

internet (lowercase i) is any network made up of smaller networks using the same internetworking protocol. It doesn't have to use TCP/IP nor does it have to be connected to the larger Internet

## History of Domain Name System
1970s - ARPAnet is a small community of a few hundred hosts. The name-to-address mapping for every host on ARPAnet was contained in a HOSTS.txt file

Question: How/Does the HOSTS.txt file relate to /etc/hosts

The HOSTS.txt file was maintained by SRI's Network Information Center (NIC). Sysadmins would email in their updates to HOSTS.txt to NIC, and NIC would update their copy of HOSTS.txt. Sysadmins would also FTP into NIC's servers to download the latest copy of the HOSTS.txt file.
As the number of hosts on the ARPAnet expanded, this workflow become difficult and unmanageable. 

### Issues with HOSTS.txt
1. Traffic and Load
   *  The amount of network traffic and processor load involved in distributing the latest HOSTS.txt file was getting out of hand
2. Name Collisions
   *  There wasn't an easy way to guarantee that name collisions wouldn't occur. Anyone could technically say that they were authoritative over a given domain
3. Consistency
   *  Keeping the file up to date was also problematic. By the time the furthest hosts got the latest HOSTS.txt file, it may have already been out of date

### How these issues were resolved
Paul Mockapetris released RFCs 882 and 883 in 1984; These RFCs described the Domain Name System. They have since been superseded by RFCs 1034 and 1035, and are augmented by other RFCs detailing topics such as potential DNS security problems, implementation problems, administrative gotchas, mechanisms for dynamically updating nameservers and for securing zone data

## Overview of DNS
It is a distributed database. 


## Resolvers
Clients that access nameservers. Resolvers are responsible for
* Querying nameservers
* Interpreting the response receive from nameservers
* Returning the information to the programs that requested it

Resolvers that can't do much more than send the query out and wait for a response are referred to as _stub resolvers_
## Nameserver
They contain data about zones that they are authoritative for; They can also search through the DNS namespace to find information about zones they are not authoritative for in a process called name resolution