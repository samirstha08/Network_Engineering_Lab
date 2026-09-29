**# Troubleshooting**



During this lab, I faced a small IPv6 connectivity issue.



* IPv6 Ping Failed



&#x09;At first, the IPv6 ping from one PC to another showed : Destination host unreachable.

&#x09;I checked the IPv6 configuration and found that **PC2** did not have an IPv6 address configured.

&#x09;Therefore, I assigned : 2001:DB8:10::3/64

&#x09;After configuring the address, I tested the connection again and the ping worked successfully.



1. **Checking the Router Interface**



Before testing connectivity, I checked whether the router interface was active.



I used:



show ip interface brief and show ipv6 interface brief.



The interface needed to be up/up and have the correct IPv4 and IPv6 addresses.



If the interface was down, I would have used:



interface gigabitEthernet 0/0

no shutdown



These helped me confirm that the router interface was up and that both IPv4 and IPv6 addresses were configured correctly.



**2. Checking IPv6 Routing**



For IPv6 communication through the router, I enabled IPv6 routing using : ipv6 unicast-routing



Without this command, the router would not forward IPv6 packets between different IPv6 networks.



**3. Checking IP Addresses**



When testing connectivity, I made sure that the devices had the correct addresses.



For IPv4:

R1   192.168.10.1/24

PC1  192.168.10.2/24

PC2  192.168.10.3/24



For IPv6:

R1   2001:DB8:10::1/64

PC1  2001:DB8:10::2/64

PC2  2001:DB8:10::3/64



**4. Testing Connectivity Step by Step**



Instead of testing everything at once, I tested the network step by step:



PC1 - PC2 using IPv4

PC1 - PC2 using IPv6

PC1 - R1 using IPv4

PC1 - R1 using IPv6

PC2 - R1 using IPv4

PC2 - R1 using IPv6



This made it easier to identify where a problem was occurring.



**What I Learned**



The main lesson from troubleshooting this lab was to check the configuration step by step instead of guessing.



For connectivity problems, I should first check:



* IP address
* Subnet mask/prefix
* Default gateway
* Interface status
* IPv6 routing
* Connectivity using ping



After correcting the configuration, all IPv4 and IPv6 connectivity tests worked successfully. The problem was caused by a missing IPv6 configuration on **PC2**. This showed me that checking the configuration step by step is important when troubleshooting network connectivity.



