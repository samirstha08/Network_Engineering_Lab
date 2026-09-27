**# TROUBLESHOOTING**



While doing this lab, I checked a few basic things to make sure the PC and router were communicating properly.



1. **Router Interface**



At first, the router interface needed to be enabled before it could be used for communication.

&#x20;

I used the following command : no shutdown



After that, I checked the interface using : show interface gigabitethernet 0/0 and show ip interface brief.



This helped me confirm whether the interface was working properly.



2\. **Checking IP Configuration**



I also checked the IP configuration of the PC using : ipconfig



I made sure that the PC was using an IP address from the same network as the router interface.



The router interface was configured as : ip address 192.168.10.1 255.255.255.0



3\. **Testing Connectivity**



After configuring the devices, I used "ping" command to check whether the PC could communicate with the router.



ping 192.168.10.1



If the ping works, it confirms that the basic connection between the PC and router is working.



**# What I Checked**



When checking the connection, I mainly looked at:



* PC IP address and subnet mask
* Router interface IP address
* Router interface status
* Cable connection
* Ping response



These basic checks helped me understand how to find simple connectivity problems in a network.



