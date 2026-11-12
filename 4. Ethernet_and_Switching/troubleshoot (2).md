# Troubleshooting - Ethernet Switching and Frame Forwarding 

During this lab, I performed different forwarding experiments using Cisco Packet Tracer. I also encountered a few situations that required checking the MAC address table and understanding how packets were being processed. 

## 1. Ping Was Not Progressing in Simulation Mode 

**Problem:** 

When I started the ping command in Simulation Mode, the packet appeared to remain at PC0 and did not seem to move forward. 

**Solution:** 

I used the Capture/Forward button to manually advance the simulation events. 

After advancing the events, the packet moved through the switch and the ping completed successfully. 

## 2. PC1's MAC Address Was Missing from the Switch 

**Problem:** 

Before performing known unicast forwarding, PC1's MAC address was not visible in the switch's MAC address table. 

**Solution:** 

I generated traffic from PC1 by pinging PC0. 

This allowed the switch to learn PC1's source MAC address and associate it with Fa0/2. 

I verified the entry using: 

```bash 

show mac address-table ``` 

## 3. Unknown Unicast Was Not Being Demonstrated 

**Problem:** 

When using a normal ping, ARP resolution could occur before the actual ICMP frame was sent. This could cause the switch to learn the destination MAC address before the forwarding test. 

**Solution:** 

I cleared the dynamically learned MAC addresses from the switch: 

```bash 

clear mac address-table dynamic 

I kept the existing ARP entry on PC0 so that it could send the frame directly to PC1 without generating another ARP request. 

This allowed me to observe unknown unicast flooding. 

## 4. Other PCs Received the Frame but Did Not Reply 

**Problem:** 

During unknown unicast flooding, the frame was forwarded to PC1, PC2, and PC3, but only PC1 sent a reply. 

**Explanation:** 

This was expected behavior. 

The switch flooded the Ethernet frame because it did not know the destination MAC address. 

However, PC2 and PC3 discarded the packet because its destination IP address belonged to PC1. 

## 5. No Reply During Broadcast Forwarding 

**Problem:** 

During the broadcast experiment, PC0 sent an ARP request for 192.168.1.99. The switch forwarded the frame to all other PCs, but no reply was received. 

**Explanation:** 

This was not a network problem. 

The IP address 192.168.1.99 was not assigned to any connected PC. 

Therefore, none of the PCs could respond to the ARP request. 

The purpose of the experiment was to observe how the switch forwarded broadcast frames. 

## 6. Unsupported IGMP Snooping Command 

**Problem:** 

The command `show ip igmp snooping` was rejected by the Packet Tracer switch. 

**Explanation:** 

The simulated Cisco Catalyst 2960 does not necessarily support every command or feature available on a physical switch. 

I checked the switch model and IOS version using: 

```bash 

show version 

This helped identify the device and its software version. 

## Conclusion 

Most of the issues encountered during this lab were related to understanding packet movement, ARP resolution, and MAC address learning. 

By using Simulation Mode and checking the MAC address table, I was able to identify what was happening and successfully complete the known unicast, unknown unicast, and broadcast forwarding experiments. 

