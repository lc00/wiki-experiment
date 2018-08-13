Use VPCs to segment your organization's resources:

* Different environments for your apps
* Marketing vs. Product, etc.

## Route Tables

* Determines how resources inside a VPC communicate with each other
* The internet gateway (`igw`) allows your internal traffic to reach the internet

## ACL

* Determines what kind of traffic is allowed in and out of a VPC
* A seconary line of defense - Security groups do most of the work

## NAT

* Network address translation
* Private IP addresses that have that go through a public gateway
* 3 blocks of IP addresses that are only used for private addresses:
    * The entire `10.0.0.0` block
    * `72.16` through `172.31`
    * `92.168` through `192.168`
* Private addresses are assigned with a DHCP server
    * They generally don't assign `.0`, `.1`, and `.255` to clients
* You can split these into sub-networks, that may or may not be able to communicate with each other

### CIDR

Classless Inter-Domain Routing.

`192.168.0.0/24`

* Means that the first 3 octets (8 bits * 3) are the network, the last octet is for device ("host") addresses
* Next subnet would be `192.168.1.0/24`
* A subnet needing more than 255 devices could open up the next octet with `192.168.0.0/16`

### Netmask

Alternative to CIDR.

`255.255.255.0`

* All 8 bits of the first 3 octets are reserved for the network, and none of the last octet
* You could open up the next octet with `255.255.0.0`
