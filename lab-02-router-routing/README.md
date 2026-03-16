# Lab 02 – Inter-Network Routing

## Topology

PC0 → Switch → Router → Switch → PC1

## Networks

Network A  
192.168.1.0/24

Network B  
192.168.2.0/24

## Router Interfaces

Gig0/0  
192.168.1.1

Gig0/1  
192.168.2.1

## Testing

PC0 ping → 192.168.2.10  
Result: Success

PC1 ping → 192.168.1.10  
Result: Success

## Concepts Learned

- Routing between networks
- Default gateway usage
- Router interface configuration
- Layer 3 communication
