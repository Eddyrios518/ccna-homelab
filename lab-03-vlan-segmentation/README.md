# Lab 03 – VLAN Segmentation

## Objective

Learn how VLANs segment a switch into multiple logical networks.

## Topology

4 PCs connected to a Cisco 2960 switch.

PC0 → Fa0/1  
PC1 → Fa0/2  
PC2 → Fa0/3  
PC3 → Fa0/4  

## IP Addressing

PC0 – 192.168.10.10  
PC1 – 192.168.10.11  

PC2 – 192.168.20.10  
PC3 – 192.168.20.11  

Subnet Mask: 255.255.255.0

## VLAN Configuration
enable
configure terminal

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

## Verification

show vlan brief

VLAN 10 – Fa0/1, Fa0/2  
VLAN 20 – Fa0/3, Fa0/4  

## Testing

Successful:
PC0 → PC1
PC2 → PC3

Failed (expected):
PC0 → PC2

Devices in different VLANs cannot communicate without Layer 3 routing.
