computer network 
- system of interconnected network and computerized peripherals
- information and resource sharing
- wired or wireless

internetwork/internet
- network of networks
- TCP/IP protocol suite
- IP addressing protocol
- IPv4 -> IPv6
- client-server model
- WWW, FTP

classification of networks
1. geographical span - PAN, LAN, MAN, WAN
2. interconnectivity - mesh, bus, ring, star, hybrid
3. administration - public or private
4. architecture - client/server, peer-to-peer, hybrid

PAN
- Bluetooth or IR enabled devices

LAN
- private IP addresses
- ethernet, ring topology

MAN
- b/w LAN and WAN

WAN
- internet - all connected WANs

topologies
- arrangement with which computer systems or network devices are connected to each other
- physical or logical
- both can be same or different on same network

point-to-point
- two hosts
- sender <-> receiver

bus topology
- shared single communication line or cable, hosts, line terminator
- multiple hosts sending data -> collision
- solved by CSMA/CD - Carrier Sense Multi Access/Collision Detection
- or set one host as master
- host failure ✔️
- communication line ❌- single point of failure 
- unidirectional flow

star topology
- point to point connection b/w hosts and hub
- single point of failure ❌ - hub
- hubs:
	1. L1 - hub/repeater
	2. L2 - switch/bridge
	3. L3 - router/gateway

ring topology
- each host connects to exactly two adjacent hosts
- sender -> intermediate hosts (0 if data sent to adjacent hosts)-> receiver
- every host is a point of failure

mesh topology
- point to point connection with every other host or to few hosts only
- i.e. full mesh/partially mesh
- most reliable network structure
- full mesh have `n(n-1)/2` connections, `n ->` number of hosts  

tree/hierarchical topology
- core layer (uppermost) - distribution layer (middle) - access layer (lowermost)
- point of failure - root, and every node
- every connection serves as point of failure, failing of which divides the network into unreachable segment

hybrid topology
- internet
- [hybrid topology](hybrid%20topology.canvas)

