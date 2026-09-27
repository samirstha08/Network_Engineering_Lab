\# README



**1. Overview**



This lab was created in Cisco Packet Tracer to practice basic networking concepts and understand how devices communicate within the same network.



* **Topology**



&#x09;The lab consists of: 2 PCs, 1 Cisco Switch, 1 Cisco Router

&#x09;The switch connects the PCs and the router.



* **IP Addressing**



| Device | IP Address   | Subnet Mask   | Default Gateway |

| ------ | ------------ | ------------- | --------------- |

| PC1    | 192.168.10.2 | 255.255.255.0 | 192.168.10.1    |

| PC2    | 192.168.10.3 | 255.255.255.0 | 192.168.10.1    |

| Router | 192.168.10.1 | 255.255.255.0 | —               |



* **Configuration**



&#x09;The router interface was configured as the default gateway for the `192.168.10.0/24` network.



&#x09;The following basic Cisco commands were used:



&#x09;	enable

&#x09;	configure terminal

&#x09;	interface gigabitEthernet 0/0

&#x09;	ip address 192.168.10.1 255.255.255.0

&#x09;	no shutdown

&#x09;	exit



* **Connectivity Testing**



&#x09;The following tests were performed:



&#x09;	PC1 → PC2: Successful

&#x09;	PC1 → Router/Gateway: Successful



&#x09;The connectivity was tested using the "ping" command.



**2. Key Concepts Learned**



* IP addressing
* Subnet masks
* Default gateway
* Same-subnet communication
* Basic router interface configuration
* Basic Cisco IOS commands
* Connectivity testing using "ping"
* Checking interface status using "show ip interface brief"



**3. Key Learning**



When two devices are in the same subnet, they can communicate directly through the switch.



A default gateway is used when a device needs to communicate with a different network.



For this lab:



Network: 192.168.10.0/24

Gateway: 192.168.10.1

PC1:     192.168.10.2

PC2:     192.168.10.3



**4. Files**



* basic\_network.pkt : Packet Tracer lab file
* topology.png : Network topology
* commands.md : Commands used during the lab
* troubleshooting.md : Troubleshooting notes



