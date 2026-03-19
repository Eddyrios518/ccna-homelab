## Lab 02 – Inter-VLAN Routing (Router-on-a-Stick)

---

##  Objective

Configure VLAN segmentation on a switch and enable communication between VLANs using a router (Router-on-a-Stick).

---

##  Topology

- 1x Switch (2960-24TT)
- 1x Router (2911)
- 4x PCs
- VLAN 10 → SALES
- VLAN 20 → ENGINEERING

---

## ⚙️ Configuration

### Switch – VLAN Creation


vlan 10
name SALES

vlan 20
name ENGINEERING

interface range fa0/1 - 2
switchport mode access
switchport access vlan 10

interface range fa0/3 - 4
switchport mode access
switchport access vlan 20
interface fa0/5
switchport mode trunk

interface gig0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0

interface gig0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0

| Device | VLAN | IP Address    | Subnet Mask   | Default Gateway |
| ------ | ---- | ------------- | ------------- | --------------- |
| PC0    | 10   | 192.168.10.10 | 255.255.255.0 | 192.168.10.1    |
| PC1    | 10   | 192.168.10.11 | 255.255.255.0 | 192.168.10.1    |
| PC2    | 20   | 192.168.20.10 | 255.255.255.0 | 192.168.20.1    |
| PC3    | 20   | 192.168.20.11 | 255.255.255.0 | 192.168.20.1    |

 Verification
 Same VLAN Test

PC0 → PC1 = worked

PC2 → PC3 = worked

 Inter-VLAN Test
ping 192.168.20.10

Result:

First ping may fail (ARP)

Subsequent pings succeed 
Key Concepts Learned

VLANs isolate traffic at Layer 2

Switches cannot route between VLANs

Trunk ports carry multiple VLANs (802.1Q tagging)

Router-on-a-Stick enables inter-VLAN communication

Subinterfaces allow one physical interface to serve multiple VLANs

Default gateways are required for cross-network communication

ARP occurs before successful ping

TTL decreases when traffic passes through a router
