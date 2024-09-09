# Cisco Packet Tracer Lab: VLSM Subnetting and Static Routing

## Overview

This project involves subnetting the `192.168.5.0/24` network using Variable Length Subnet Masking (VLSM) to provide the necessary IP addressing for multiple LANs. Additionally, static routes will be configured on the routers so that all PCs within the network can communicate.

### Key Objectives:
1. **Subnet the 192.168.5.0/24 network**  
   Use VLSM to create subnets that meet the host requirements for each LAN and the point-to-point connection between the two routers.

   - LAN 1: 45 hosts  
   - LAN 2: 64 hosts  
   - LAN 3: 14 hosts  
   - LAN 4: 9 hosts  
   - Point-to-point link between R1 and R2

2. **Assign IP addresses**  
   - Assign the first usable IP address to each PC in the respective LANs.  
   - Assign the last usable IP address to the router interface in each LAN.

3. **Configure static routes**  
   Configure static routes on R1 and R2 to ensure that all devices in the network can communicate. The routes must account for the network topology and ensure full connectivity between PCs across LANs.

---

## Network Diagram

![Network Diagram](https://github.com/ro-drick/VLSM-Subnetting/blob/main/VLSM-subnetting.PNG)

---

## Subnetting Plan

1. **LAN 1 (45 hosts)**  
   - Network Address: `192.168.5.128`
   - Subnet Mask: `/26`
   - Usable IP Range: `192.168.5.129` to `192.168.5.190`
   - Broadcast Address: `192.168.5.191`

2. **LAN 2 (64 hosts)**  
   - Network Address: `192.168.5.0`
   - Subnet Mask: `/25`
   - Usable IP Range: `192.168.5.1` to `192.168.5.126`
   - Broadcast Address: `192.168.5.127`

3. **LAN 3 (14 hosts)**  
   - Network Address: `192.168.5.192`
   - Subnet Mask: `/28`
   - Usable IP Range: `192.168.5.193` to `192.168.5.206`
   - Broadcast Address: `192.168.5.207`

4. **LAN 4 (9 hosts)**  
   - Network Address: `192.168.5.208`
   - Subnet Mask: `/28`
   - Usable IP Range: `192.168.5.209` to `192.168.5.222`
   - Broadcast Address: `192.168.5.223`

5. **Point-to-Point Link (R1-R2)**  
   - Network Address: `192.168.5.224`
   - Subnet Mask: `/30`
   - Usable IP Range: `192.168.5.225` to `192.168.5.226`
   - Broadcast Address: `192.168.5.227`

---

## IP Address Assignments

1. **LAN 1**  
   - PC1: `192.168.5.129` (First usable)  
   - R1 G0/0: `192.168.5.190` (Last usable)

2. **LAN 2**  
   - PC2: `192.168.5.1` (First usable)  
   - R1 G0/1: `192.168.5.126` (Last usable)

3. **LAN 3**  
   - PC3: `192.168.5.193` (First usable)  
   - R2 G0/0: `192.168.5.206` (Last usable)

4. **LAN 4**  
   - PC4: `192.168.5.209` (First usable)  
   - R2 G0/1: `192.168.5.222` (Last usable)

5. **Point-to-Point (R1-R2)**  
   - R1 G0/0/0: `192.168.5.225`  
   - R2 G0/0/0: `192.168.5.226`

---

## Static Route Configuration

1. **R1 Static Routes**  
   ```bash
   ip route 192.168.5.192 255.255.255.240 192.168.5.226
   ip route 192.168.5.208 255.255.255.240 192.168.5.226
   
1. **R2 Static Routes**  
   ```bash
   ip route 192.168.5.128 255.255.255.192 192.168.5.225
   ip route 192.168.5.0 255.255.255.128 192.168.5.225

## Testing
Verify that all PCs can ping each other using the following commands:
```bash
ping 192.168.5.1  
ping 192.168.5.193  
ping 192.168.5.209
```
## Conclusion

In this lab, I successfully implemented Variable Length Subnet Masking (VLSM) to optimize IP addressing for each LAN based on the specific host requirements. By carefully assigning subnets and configuring static routes, I enabled full communication between all PCs across different networks.

This exercise reinforced the importance of efficient IP address management in network design, particularly when working with networks of varying sizes. VLSM allowed me to allocate IP addresses effectively, reducing waste while ensuring that each subnet met the necessary capacity.

The static routing configuration ensured seamless communication between devices across subnets. This lab gave me practical experience in designing scalable, efficient networks that maintain connectivity between hosts in different segments.

Through this process, I gained a deeper understanding of subnetting and static routing, essential skills for network administrators looking to design optimized and interconnected networks.

## Acknowledgements


Special thanks to **Jeremy's IT Lab** for providing valuable resources and tutorials that greatly contributed to the completion of this exercise. His in-depth explanations and practical demonstrations have been instrumental in enhancing my understanding of Cisco networking concepts and the effective use of Packet Tracer.

For more information and additional resources, visit [Jeremy's IT Lab](https://jeremysitlab.com/) and check out his YouTube for the full course, [Jeremy's IT Lab Free CCNA 200-301 | Complete Course](https://www.youtube.com/playlist?list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ)
