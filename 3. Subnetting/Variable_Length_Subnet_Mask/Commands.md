This document contains the commands used to configure the routers and verify connectivity in the VLSM network. 

# **1. R1 Configuration** 

Enter privileged EXEC mode and global configuration mode: 

```
enable
configure terminal
```

## **Configure GigabitEthernet 0/0 – LAN1** 

```
interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.128
no shutdown
exit
```

## **Configure GigabitEthernet 0/1 – LAN2** 

```
interface gigabitEthernet 0/1
ip address 192.168.1.129 255.255.255.192
no shutdown
exit
```

## **Configure GigabitEthernet 0/2 – Router-to-Router Link** 

```
interface gigabitEthernet 0/2
ip address 10.0.0.1 255.255.255.252
no shutdown
exit
```

## **Configure Static Routes** 

```
ip route 192.168.1.192 255.255.255.224 10.0.0.2
ip route 192.168.1.224 255.255.255.240 10.0.0.2
```

These routes allow R1 to reach LAN3 and LAN4 through R2. 

# **2. R2 Configuration** 

```
enable
configure terminal
```

## **Configure GigabitEthernet 0/0 – LAN3** 

```
interface gigabitEthernet 0/0
ip address 192.168.1.193 255.255.255.224
no shutdown
exit
```

## **Configure GigabitEthernet 0/1 – LAN4** 

```
interface gigabitEthernet 0/1
ip address 192.168.1.225 255.255.255.240
no shutdown
exit
```

## **Configure GigabitEthernet 0/2 – Router-to-Router Link** 

```
interface gigabitEthernet 0/2
ip address 10.0.0.2 255.255.255.252
no shutdown
exit
```

## **Configure Static Routes** 

```
ip route 192.168.1.0 255.255.255.128 10.0.0.1
ip route 192.168.1.128 255.255.255.192 10.0.0.1
```

These routes allow R2 to reach LAN1 and LAN2 through R1. 

# **3. Useful Verification Commands** 

**Command Purpose** `show ip interface brief` Displays interface IP addresses and their status. `show ip route` Displays the routing table. `show running-config` Displays the current router configuration. `show interfaces` Displays detailed interface information. `ping <IP-address>` Tests connectivity to another device. `traceroute <IP-address>` Shows the path taken by packets. 

# **4. Connectivity Testing** 

From PC1, test the following addresses: 

```
ping 192.168.1.130
ping 192.168.1.194
ping 192.168.1.226
```

These commands test communication from LAN1 to LAN2, LAN3, and LAN4. 

Test the router-to-router connection: 

From R1: 

```
ping 10.0.0.2
```

From R2: 

```
ping 10.0.0.1
```

# **5. Save Router Configuration** 

```
end
copy running-config startup-config
```

This saves the current configuration so it remains available after restarting the router. 

