**#README**



**IPv4 \& IPv6 Dual-Stack Network**



In this lab, I configured a small network with both IPv4 and IPv6 running at the same time. The main goal was to understand how IPv4 and IPv6 addresses work, how CIDR notation is used, and how devices communicate within the same network.



**Topology**



* 2 PCs
* 1 Switch
* 1 Router




**IP Addressing**



| Device | IPv4 Address    | IPv6 Address      |

| ------ | --------------- | ----------------- |

| R1     | 192.168.10.1/24 | 2001:DB8:10::1/64 |

| PC1    | 192.168.10.2/24 | 2001:DB8:10::2/64 |

| PC2    | 192.168.10.3/24 | 2001:DB8:10::3/64 |



The PCs use the router as their gateway:



* IPv4 Gateway: `192.168.10.1`
* IPv6 Gateway: `2001:DB8:10::1`



**What I Practiced**



* IPv4 and IPv6 addressing
* Network and host portions
* CIDR notation
* IPv4 and IPv6 default gateways
* Dual-stack configuration
* Basic IPv6 routing
* Connectivity testing using "ping"



**Result**



The configuration was tested successfully. PC1 and PC2 were able to communicate with each other and with the router using both IPv4 and IPv6.



