**# Commands**



These are the main Cisco IOS commands I used to configure and check the router.



1. **IPv4 Configuration**



enable

configure terminal

interface gigabitEthernet 0/0

ip address 192.168.10.1 255.255.255.0

no shutdown

exit



**2. IPv6 Configuration**



First, I enabled IPv6 routing:

ipv6 unicast-routing



Then I configured the IPv6 address:

interface gigabitEthernet 0/0

ipv6 address 2001:DB8:10::1/64

no shutdown

exit



**3. Checking Interfaces**



show ip interface brief

show ipv6 interface brief



These commands helped me check the interface status and verify the IPv4 and IPv6 addresses.



**4. Testing Connectivity**



I used "ping" from the PCs to test connectivity.



ping 192.168.10.1

ping 192.168.10.3



ping 2001:DB8:10::1

ping 2001:DB8:10::3



All required connectivity tests were successful after completing the configuration.



