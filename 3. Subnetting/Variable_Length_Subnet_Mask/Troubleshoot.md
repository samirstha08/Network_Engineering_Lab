This document describes common networking issues encountered during the VLSM configuration and the steps used to identify and resolve them. 

# **1. Incorrect Subnet Mask** 

### **Problem:** 

A device may not communicate properly with other devices if it has an incorrect subnet mask. 

### **Possible Cause:** 

The subnet mask assigned to a PC or router interface does not match its allocated VLSM subnet. 

### **Solution:** 

Verify the correct subnet masks: 

**LAN Prefix Subnet Mask** LAN1 /25 255.255.255.128 LAN2 /26 255.255.255.192 LAN3 /27 255.255.255.224 LAN4 /28 255.255.255.240 

Make sure that all PCs and router interfaces use the correct subnet mask. 

# **2. Incorrect Default Gateway** 

### **Problem:** 

A PC can communicate with devices in its own LAN but cannot communicate with devices in other LANs. 

### **Possible Cause:** 

The PC has an incorrect default gateway. 

### **Solution:** 

Verify that each PC uses its router interface as its default gateway. 

**LAN Default Gateway** 

LAN1 192.168.1.1 LAN2 192.168.1.129 LAN3 192.168.1.193 LAN4 192.168.1.225 

# **3. Incorrect Static Route** 

### **Problem:** 

Communication between different LANs fails even though the router interfaces are configured correctly. 

### **Possible Cause:** 

An incorrect destination network or subnet mask is configured in the static routing table. 

### **Solution:** 

Use `show ip route` to inspect the routing table. 

The correct static routes are: 

### **On R1:** 

```
ip route 192.168.1.192 255.255.255.224 10.0.0.2
ip route 192.168.1.224 255.255.255.240 10.0.0.2
```

### **On R2:** 

```
ip route 192.168.1.0 255.255.255.128 10.0.0.1
ip route 192.168.1.128 255.255.255.192 10.0.0.1
```

## **Actual Issue Encountered During Configuration** 

During the lab, LAN2 had an incorrectly configured static route on R2. 

The incorrect route was: 

```
ip route 192.168.1.128 255.255.255.128 10.0.0.1
```

However, LAN2 was allocated a `/26` subnet, not `/25` . 

The incorrect route was removed using: 

```
no ip route 192.168.1.128 255.255.255.128 10.0.0.1
```

The correct route was then configured: 

```
ip route 192.168.1.128 255.255.255.192 10.0.0.1
```

This corrected the routing table and restored the expected connectivity. 

**Important:** Always ensure that the destination network and subnet mask in a static route match the actual VLSM allocation. 

# **4. Router Interface Is Down** 

### **Problem:** 

A router interface cannot communicate with connected devices. 

### **Possible Cause:** 

The interface may be administratively down. 

### **Solution:** 

Enter interface configuration mode and execute: 

```
no shutdown
```

Use the following command to verify interface status: 

```
show ip interface brief
```

The interface should show `up` and the line protocol should also show `up` . 

# **5. Router-to-Router Connectivity Failure** 

### **Problem:** 

The two routers cannot communicate with each other. 

### **Possible Cause:** 

- Incorrect IP address on the transit interfaces. 

- Incorrect subnet mask. 

- Interface is shut down. 

- Physical connection problem. 

### **Solution:** 

Verify the transit network configuration: 

### **Router Interface IP Address** 

R1 G0/2 10.0.0.1/30 R2 G0/2 10.0.0.2/30 

Test the connection using: 

```
ping 10.0.0.2
```

from R1, and: 

```
ping 10.0.0.1
```

from R2. 

# **6. Ping Request Timed Out** 

### **Problem:** 

The ping command displays `Request timed out` . 

### **Possible Causes:** 

- Incorrect IP configuration. 

- Incorrect default gateway. 

- Missing or incorrect static route. 

- Interface or cable problem. 

- ARP resolution during the first ping attempt. 

### **Solution:** 

1. Verify the PC's IP address and subnet mask. 2. Check the default gateway. 

3. Verify router interface status. 

4. Check the routing table using `show ip route` . 

5. Repeat the ping if the first attempt times out. 

# **Conclusion** 

Most of the issues encountered in this lab were related to incorrect subnet masks and static route configurations. Checking the routing table, verifying IP addressing, and testing connectivity helped identify and resolve the problems. This highlights the importance of accurate VLSM planning and proper routing configuration. 

