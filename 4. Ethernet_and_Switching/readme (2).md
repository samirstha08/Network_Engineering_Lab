# Lab 4A: Ethernet Switching and Frame Forwarding 

# ## Introduction 

In this lab, I explored how a Layer 2 switch handles different types of Ethernet frames. I used Cisco Packet Tracer to understand how a switch learns MAC addresses and decides where to forward incoming frames. 

The main purpose of this lab was to observe the actual forwarding behavior of a switch using Simulation Mode. 

# ## Objectives 

- Understand how a switch learns MAC addresses. 

- Observe known unicast forwarding. 

- Understand unknown unicast flooding. 

- Observe broadcast forwarding. 

- Examine the MAC address table. 

- Understand how a switch decides where to forward Ethernet frames. 

# ## Network Topology 

The topology consists of four PCs connected to a Cisco Catalyst 2960 switch. 

# ### Devices Used 

- 1 Cisco Catalyst 2960 Switch 

- 4 PCs 

- Copper Straight-Through Cables 

# ### IP Addressing Table 

| Device | IP Address | Subnet Mask | 

|---|---|---| | PC0 | 192.168.1.10 | 255.255.255.0 | | PC1 | 192.168.1.11 | 255.255.255.0 | | PC2 | 192.168.1.12 | 255.255.255.0 | | PC3 | 192.168.1.13 | 255.255.255.0 | 

### Switch Port Connections 

| Device | Switch Port | |---|---| | PC0 | Fa0/1 | | PC1 | Fa0/2 | | PC2 | Fa0/3 | | PC3 | Fa0/4 | 

All devices were connected to VLAN 1. 

## Experiments Performed 

### 1. Known Unicast Forwarding 

In this experiment, PC0 communicated with PC1 using a ping command. 

Before performing the test, I checked the switch's MAC address table to make sure that the switch had already learned the MAC addresses of both PCs. 

When PC0 sent a frame to PC1, the switch checked its MAC address table and found the destination MAC address associated with Fa0/2. 

The switch forwarded the frame only through Fa0/2 instead of sending it to every connected PC. 

**Observation:** The frame was forwarded only to the destination port. 

### 2. Unknown Unicast Flooding 

For this experiment, I cleared the dynamically learned MAC addresses from the switch using the following command: 

`clear mac address-table dynamic` 

I kept PC0's ARP entry for PC1 so that PC0 could send the Ethernet frame without generating another ARP request. 

When PC0 sent a frame to PC1, the switch did not have PC1's MAC address in its MAC address table. 

As a result, the switch flooded the frame through all other ports in the same VLAN except the incoming port. 

PC1, PC2, and PC3 received the frame, but only PC1 replied because the packet was intended for PC1. 

**Observation:** The unknown unicast frame was flooded through all other ports in the VLAN. 

### 3. Broadcast Forwarding 

In this experiment, I used an unused IP address (192.168.1.99) to generate an ARP request from PC0. 

Since PC0 did not know the MAC address associated with that IP address, it sent an ARP request using the broadcast destination MAC address: 

`FF:FF:FF:FF:FF:FF` 

The switch received the frame and forwarded it through all other ports in VLAN 1. 

All three other PCs received the broadcast frame. However, none of them replied because 192.168.1.99 was not assigned to any of them. 

**Observation:** The switch forwarded the broadcast frame to all other connected PCs in the same VLAN. 

# ## Results 

All three forwarding experiments were successfully performed using Cisco Packet Tracer. 

Simulation Mode helped me observe how frames moved through the switch and how the MAC address table influenced the forwarding decision. 

# ## Conclusion 

Through this lab, I gained a practical understanding of how a Layer 2 switch handles different Ethernet frames. I learned that a switch forwards known unicast frames to a specific port, floods unknown unicast frames when the destination MAC address is not available in its MAC address table, and forwards broadcast frames to all other ports within the same VLAN. 

This lab helped me understand MAC address learning and frame forwarding more clearly by observing the actual packet movement in Cisco Packet Tracer. 

