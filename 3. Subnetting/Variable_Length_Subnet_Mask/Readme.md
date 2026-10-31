# **Overview** 

This project demonstrates Variable Length Subnet Masking (VLSM) using Cisco Packet Tracer. The network is designed by dividing a `192.168.1.0/24` network into multiple subnets according to the host requirements of different departments. 

The project uses two Cisco 2911 routers, four Cisco 2960 switches, and twelve PCs to establish communication between four different LANs. 

# **Objectives** 

- Understand and implement VLSM. 

- Allocate IP addresses according to departmental host requirements. 

- Configure router interfaces and default gateways. 

- Configure static routing between routers. 

- Establish communication between different subnets. 

- Troubleshoot subnetting and routing issues. 

# **Network Topology** 

The network consists of: 

- 2 Cisco 2911 Routers (R1 and R2) 

- 4 Cisco 2960 Switches (SW1, SW2, SW3, SW4) 

- 12 PCs (3 PCs in each LAN) 

## **Department Allocation** 

**LAN Department Required Hosts** 

LAN1 Computer Lab 100 LAN2 Administration 50 LAN3 Teachers 25 LAN4 Management 10 

# **VLSM Addressing Table** 

Starting Network: `192.168.1.0/24` 

|**LAN Network Addre**|**ss Prefix**|**Subnet Mask**<br>**Usable IP Ra**|**nge Broadcast**|
|---|---|---|---|
|LAN1 192.168.1.0|/25|255.255.255.128 .1 – .126|.127|
|LAN2 192.168.1.128|/26|255.255.255.192 .129 – .190|.191|
|LAN3 192.168.1.192|/27|255.255.255.224 .193 – .222|.223|
|LAN4 192.168.1.224|/28|255.255.255.240 .225 – .238|.239|



## **Router-to-Router Network** 

**Network IP Address Subnet Mask** Transit Network 10.0.0.0/30 255.255.255.252 R1 G0/2 10.0.0.1 255.255.255.252 R2 G0/2 10.0.0.2 255.255.255.252 

# **Router Configuration** 

## **R1** 

- G0/0: 192.168.1.1/25 

- G0/1: 192.168.1.129/26 

- G0/2: 10.0.0.1/30 

## **R2** 

- G0/0: 192.168.1.193/27 

- G0/1: 192.168.1.225/28 

- G0/2: 10.0.0.2/30 

# **Static Routing** 

R1 contains static routes to LAN3 and LAN4 through R2. 

R2 contains static routes to LAN1 and LAN2 through R1. 

# **Testing and Verification** 

Connectivity was tested using the `ping` command between PCs belonging to different LANs. 

The successful communication between different subnets verified: 

- Correct VLSM subnet allocation. 

- Correct IP addressing and default gateways. 

- Proper router interface configuration. 

- Correct static routing configuration. 

# **Conclusion** 

This project demonstrates how VLSM allows efficient utilization of IP address space by assigning different subnet sizes according to the host requirements of each department. Static routing enables communication between the different LANs connected through two routers. 

