# CCNA-topologie-projetc-of-ospf-in-cisco-ipv4
# README - OSPF Network Topology

## Description
This project represents a network topology configured with the **OSPF (Open Shortest Path First)** routing protocol. The topology consists of two distinct LANs, each connected to a router, with a serial link between them for inter-network communication.

## Network Components
### **Devices Used:**
- **2 Cisco 2911 Routers** (Router0 & Router1)
- **2 Cisco 2960 Switches** (Switch0 & Switch1)
- **4 PC Hosts** (PC0, PC1, PC2, PC3)

### **IP Addressing Scheme:**
- **LAN 1 (Yellow Area)**
  - Network: `192.168.1.0/24`
  - Router0 Interface (Gig0/0): `192.168.1.1`
  - PCs in LAN: `192.168.1.X`
- **LAN 2 (Blue Area)**
  - Network: `192.168.2.0/24`
  - Router1 Interface (Gig0/0): `192.168.2.1`
  - PCs in LAN: `192.168.2.X`
- **WAN Link (Between Routers)**
  - Network: `10.0.0.0/30`
  - Router0 Serial0/0/0: `10.0.0.2`
  - Router1 Serial0/0/0: `10.0.0.1`

## Routing Protocol: OSPF
The network is using **OSPF** for dynamic routing, allowing routers to exchange route information efficiently. The routers are configured to advertise their directly connected networks so that the two LANs can communicate seamlessly.

### **OSPF Configuration Overview:**
- **Router0:**
  - `router ospf 1`
  - `network 192.168.1.0 0.0.0.255 area 0`
  - `network 10.0.0.0 0.0.0.3 area 0`
- **Router1:**
  - `router ospf 1`
  - `network 192.168.2.0 0.0.0.255 area 0`
  - `network 10.0.0.0 0.0.0.3 area 0`

## Functionality & Connectivity
- PCs within each LAN can communicate using their respective subnet.
- OSPF ensures that packets from **192.168.1.0/24** can reach **192.168.2.0/24** via Router0 and Router1.
- The serial link (`10.0.0.0/30`) provides the connection between both routers for inter-network routing.

## How to Use
1. **Configure IP addresses** on each router's interfaces.
2. **Set up OSPF** on both routers as per the configuration above.
3. **Verify connectivity** using commands like:
   - `ping <destination IP>`
   - `show ip route` (to check OSPF-learned routes)
   - `show ip ospf neighbor` (to verify OSPF adjacency)

## Conclusion
This topology demonstrates a **basic OSPF setup** that allows two LANs to communicate dynamically without static routes. It can be extended with more routers or advanced OSPF features such as cost metrics and multiple areas.

