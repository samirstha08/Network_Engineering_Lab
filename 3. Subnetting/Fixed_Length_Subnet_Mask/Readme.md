# **#IPv4 Subnetting Using FLSM** 

# ## Overview 

This project demonstrates how to divide a single IPv4 network into multiple equal-sized subnets using Fixed Length Subnet Masking (FLSM). The network was designed and configured in Cisco Packet Tracer using two routers, four switches, and twelve PCs. 

The main goal of this lab was to practice subnetting, configure IP addresses on routers and PCs, set up static routing, and test communication between different networks. 

# ## Objectives 

- Divide a `/24` network into four equal-sized subnets. 

- Configure IPv4 addresses and subnet masks on routers and PCs. 

- Configure router interfaces and enable them. 

- Connect two routers using a separate point-to-point network. 

- Configure static routes between the LANs. 

- Verify connectivity using ping commands. 

# ## Network Design 

The starting network is `192.168.10.0/24`. Using a `/26` subnet mask divides it into four equal-sized subnets. 

Each subnet contains 64 total addresses, of which 62 are usable for hosts. 

- | LAN | Network Address | Subnet Mask | Default Gateway | 

- |---|---|---|---| 

- | LAN 1 | 192.168.10.0/26 | 255.255.255.192 | 192.168.10.1 | 

- | LAN 2 | 192.168.10.64/26 | 255.255.255.192 | 192.168.10.65 | 

- | LAN 3 | 192.168.10.128/26 | 255.255.255.192 | 192.168.10.129 | 

- | LAN 4 | 192.168.10.192/26 | 255.255.255.192 | 192.168.10.193 | 

A separate `/30` network, `10.0.0.0/30`, is used for communication between the two routers. 

- | Device | Interface | IP Address | 

- |---|---|---| 

- | R1 | G0/0 | 192.168.10.1/26 | 

- | R1 | G0/1 | 192.168.10.65/26 | 

- | R1 | G0/2 | 10.0.0.1/30 | 

- | R2 | G0/0 | 192.168.10.129/26 | 

- | R2 | G0/1 | 192.168.10.193/26 | 

| R2 | G0/2 | 10.0.0.2/30 | 

# ## Tools and Technologies 

- Cisco Packet Tracer 

- IPv4 addressing 

- Fixed Length Subnet Masking (FLSM) 

- Static routing 

- Basic network troubleshooting 

# ## Implementation 

The network was built using two Cisco 2911 routers, four Cisco 2960 switches, and twelve PCs. Each LAN contains three PCs connected through a switch. 

The router interfaces were assigned the appropriate gateway addresses. A separate network was configured between R1 and R2, and static routes were added so that each router could reach the LANs connected to the other router. 

After configuring the devices, connectivity was tested using ping commands. 

# ## Testing and Results 

The following tests were completed successfully: 

- Each LAN could reach its default gateway. 

- R1 and R2 could communicate through the transit network. 

- PCs on different LANs could communicate with one another. 

- Static routes provided connectivity between the remote subnets. 

These results confirmed that the addressing and routing configuration worked as intended. 

# ## Conclusion 

This lab provided practical experience with IPv4 subnetting and static routing. It helped demonstrate how a single network can be divided into smaller subnets and how routers allow devices in different networks to communicate. Testing the connections also showed the importance of correct IP addressing, default gateways, and physical connections when troubleshooting a network. 

