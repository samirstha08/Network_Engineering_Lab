# **Troubleshooting Notes** 

During the configuration of this network, a few issues needed to be checked before connectivity worked correctly. These are the main troubleshooting steps relevant to the lab. 

## **1. Incorrect Gateway IP Address** 

**Problem:** A ping to the LAN 2 gateway failed. 

**Cause:** The gateway address was entered incorrectly as `192.168.10.165` instead of `192.168.10.65` . 

**Solution:** The correct gateway address was used. 

```
ping 192.168.10.65
```

After correcting the address, the gateway test succeeded. 

## **2. Checking Router Interfaces** 

**Problem:** Connectivity problems can occur if a router interface is disabled or its link is down. 

**Solution:** The following command was used to check the interface status on R1: 

```
show ip interface brief
```

The three configured GigabitEthernet interfaces showed `up/up` , confirming that their links were active. 

The `no shutdown` command was used in interface configuration mode to enable the router interfaces. 

## **3. Checking Switch Connections** 

**Problem:** A device may fail to reach its gateway if its switch is connected to the wrong router interface. 

**Solution:** The physical connections were checked against the intended topology: 

- LAN 1 switch connects to R1 G0/0. 

- LAN 2 switch connects to R1 G0/1. 

- LAN 3 switch connects to R2 G0/0. 

- LAN 4 switch connects to R2 G0/1. 

- R1 G0/2 connects to R2 G0/2. 

The switch port status was checked using: 

```
show interfaces status
```

The MAC address table was also checked to see which ports had learned device addresses: 

```
show mac address-table dynamic
```

## **4. Verifying Static Routes** 

**Problem:** Devices on different LANs may not communicate if the routers do not have routes to remote networks. 

**Solution:** The routing tables were inspected on both routers. 

```
show ip route
```

R1 needs routes to `192.168.10.128/26` and `192.168.10.192/26` through `10.0.0.2` . 

R2 needs routes to `192.168.10.0/26` and `192.168.10.64/26` through `10.0.0.1` . 

The static routes were configured and verified before testing communication between the LANs. 

## **5. Testing Connectivity** 

Connectivity was checked in stages instead of testing every device at once. 

1. Ping the local default gateway. 

2. Ping the other router's transit IP address. 

3. Ping a PC on another LAN. 

4. Repeat the test in the opposite direction if needed. 

For example: 

```
ping 192.168.10.65
ping 10.0.0.2
ping 192.168.10.2
```

This approach helps identify whether a problem is related to the local LAN, the router-torouter connection, or the static routes. 

## **Conclusion** 

The main lesson from troubleshooting this lab was to verify the IP addresses and physical connections before changing the routing configuration. Checking the interface status, routing table, and ping results made it easier to narrow down the cause of connectivity problems. 

