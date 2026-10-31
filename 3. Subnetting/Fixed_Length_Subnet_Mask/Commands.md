# **Router Configuration Commands** 

This file contains the main Cisco IOS commands used to configure R1 and R2 in the FLSM lab. 

## **Router R1 Configuration** 

R1 connects LAN 1, LAN 2, and R2. It also contains static routes to LAN 3 and LAN 4. 

```
enable
configure terminal
hostname R1
interface gigabitEthernet 0/0
 ip address 192.168.10.1 255.255.255.192
 no shutdown
exit
interface gigabitEthernet 0/1
 ip address 192.168.10.65 255.255.255.192
 no shutdown
exit
interface gigabitEthernet 0/2
 ip address 10.0.0.1 255.255.255.252
 no shutdown
exit
ip route 192.168.10.128 255.255.255.192 10.0.0.2
ip route 192.168.10.192 255.255.255.192 10.0.0.2
end
copy running-config startup-config
```

## **Router R2 Configuration** 

R2 connects LAN 3, LAN 4, and R1. Static routes are used to reach LAN 1 and LAN 2. 

```
enable
configure terminal
hostname R2
interface gigabitEthernet 0/0
 ip address 192.168.10.129 255.255.255.192
 no shutdown
exit
interface gigabitEthernet 0/1
 ip address 192.168.10.193 255.255.255.192
 no shutdown
exit
interface gigabitEthernet 0/2
 ip address 10.0.0.2 255.255.255.252
 no shutdown
```

```
exit
```

```
ip route 192.168.10.0 255.255.255.192 10.0.0.1
ip route 192.168.10.64 255.255.255.192 10.0.0.1
```

```
end
```

```
copy running-config startup-config
```

When prompted for the destination filename, press Enter to accept the default `startupconfig` . 

## **Purpose of Common Router Commands** 

The following commands are used during router configuration and verification. 

|**Command**|**What it is used for**|
|---|---|
|`enable`|Enters privileged EXEC mode to access administrative<br>commands.|
|`configure terminal`|Enters global configuration mode to configure the router.|
|`hostname R1`|Sets the router's name to R1, making it easier to identify.|
|`interface gigabitEthernet`<br>`0/0`|Selects a specific router interface for configuration.|
|`ip address`|Assigns an IP address and subnet mask to an interface.|
|`no shutdown`|Enables an interface that is administratively disabled.|
|`exit`|Leaves the current configuration mode and returns to the<br>previous mode.|
|`ip route`|Adds a static route to a destination network through a<br>specified next-hop address.|
|`end`|Exits configuration mode and returns to privileged EXEC<br>mode.|
|`copy running-config`<br>`startup-config`|Saves the current configuration so it remains available<br>after a router restart.|



## **Verification Commands** 

These commands were used to check the router interfaces, routing table, and connectivity. 

||**Command**|**Purpose**|
|---|---|---|
|`show ip`|`interface brief`|Checks interface IP addresses and status|
|`show ip`|`route`|Displays directly connected networks and static routes|
|`show ru`|`nning-config`|Displays the active router configuration|
|`show ip`|`protocols`|Displays routing protocol information|
|`ping 10`|`.0.0.2`|Tests connectivity from R1 to R2|
|`ping 10`|`.0.0.1`|Tests connectivity from R2 to R1|



## **PC Configuration** 

Each PC was assigned a unique IPv4 address, the subnet mask `255.255.255.192` , and the gateway address of its LAN. 

**PC IPv4 Address Default Gateway** PC1 192.168.10.2 192.168.10.1 PC2 192.168.10.3 192.168.10.1 PC3 192.168.10.4 192.168.10.1 PC4 192.168.10.66 192.168.10.65 PC5 192.168.10.67 192.168.10.65 PC6 192.168.10.68 192.168.10.65 PC7 192.168.10.130 192.168.10.129 PC8 192.168.10.131 192.168.10.129 PC9 192.168.10.132 192.168.10.129 PC10 192.168.10.194 192.168.10.193 PC11 192.168.10.195 192.168.10.193 PC12 192.168.10.196 192.168.10.193 

## **Connectivity Testing** 

The following ping tests were used to verify the network: 

```
ping 192.168.10.65
ping 192.168.10.2
ping 192.168.10.130
ping 192.168.10.194
```

The tests confirmed communication with the relevant gateways and between devices on different LANs. 

