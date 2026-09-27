**# COMMANDS USED**



This document contains the commands used during the Networking Fundamentals lab in Cisco Packet Tracer.



**1. Router Configuration Commands**



* enable : Used to enter privileged EXEC mode.



* configure terminal : Used to enter global configuration mode.



* interface gigabitethernet 0/0 : Used to enter configuration mode for the GigabitEthernet 0/0 interface.



* ip address 192.168.10.1 255.255.255.0 : Used to assign the IP address and subnet mask to the router interface.



* no shutdown : Used to activate the router interface.



* exit : Used to leave the interface configuration mode.



**2. Interface Verification Commands**



* show ip interface brief : Used to check the IP addresses and status of the router interfaces and helped me check whether the interface was up/up after configuration.



* show interface gigabitethernet 0/0 : Used to view detailed information about the GigabitEthernet 0/0 interface.



**2. PC Commands**



* ipconfig : Used to check the IP address, subnet mask, and default gateway of a PC.
* ping : Used to test connectivity between two devices.

&#x09;

&#x09;	ping 192.168.10.3

&#x09;	The ping command was used to verify communication between PC1 and PC2.





**3. Connectivity Testing**



* Ping PC1 to PC2



&#x09;ping 192.168.10.3



* Ping PC2 to PC1



&#x09;ping 192.168.10.2



* ping PC and the Router

&#x09;

&#x09;ping 192.168.10.1

&#x09;

