# Commands Used - Ethernet Switching and Frame Forwarding 

This file contains the important commands I used to perform and verify the switching experiments. 

## 1. Checking the MAC Address Table 

```bash show mac address-table ``` 

Displays the MAC addresses learned by the switch and the ports associated with them. 

I used this command to verify whether the switch had learned the MAC addresses of PC0 and PC1. 

## 2. Clearing Dynamic MAC Address Entries 

```bash clear mac address-table dynamic ``` 

Removes dynamically learned MAC address entries from the switch's MAC address table. 

I used this command before performing the unknown unicast flooding experiment. 

## 3. Checking the Switch Version 

```bash show version ``` 

Displays information about the switch, including its model, IOS version, and hardware details. 

I used this command to identify the Cisco Catalyst 2960 switch and its IOS version. 

## 4. Checking Interface Status 

```bash 

show interfaces status 

Displays the status of switch ports, including connected devices, VLAN assignments, speed, and duplex information. 

This command is useful when checking whether switch interfaces are working properly. 

## 5. Checking Interface Details 

```bash 

show interfaces 

Displays detailed information about switch interfaces, including their operational status, speed, duplex settings, and traffic statistics. 

It is useful for checking interface-related problems. 

## 6. Testing Connectivity 

```bash ping 192.168.1.11 ``` 

Tests connectivity between PC0 and PC1. 

I used this command during the known unicast and unknown unicast experiments. 

## 7. Checking the ARP Table 

```bash arp -a 

Displays the IP addresses and their corresponding MAC addresses stored in a PC's ARP table. 

I used this command to verify that PC0 already knew PC1's MAC address before performing the unknown unicast experiment. 

## 8. Generating a Broadcast Request 

```bash ping 192.168.1.99 ``` 

Attempts to reach an unused IP address. 

Since the destination IP was not available in the ARP table, PC0 generated an ARP request, which was sent as a broadcast frame. 

Note: The ping was expected to fail because no device was configured with this IP address. The purpose was to observe broadcast forwarding. 

