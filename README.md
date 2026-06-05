## Multi-VLAN Residential Network Lab

This repository documents a Cisco Packet Tracer inter-VLAN lab that simulates a small residential network with three isolated VLANs representing separate apartment units. Inter-VLAN routing is configured using a router-on-a-stick topology.

### Network Topology

- VLAN 10: Apartment 1 - 192.168.1.0/24
- VLAN 20: Apartment 2 - 192.168.2.0/24
- VLAN 30: Apartment 3 - 192.168.3.0/24

Devices:

- 1 Cisco 2811 router with a WIC-1ENET module for additional Ethernet connectivity
- 3 Cisco 2960 managed switches (one per VLAN)
- 6 PCs (2 per switch) with static IP assignments

### Lab Objectives

- Create and name VLANs on each switch
- Assign switch ports as access ports for the correct VLANs
- Configure trunk links between switches and the router
- Set up router subinterfaces for each VLAN (router-on-a-stick)
- Assign static IP addresses to all PCs
- Verify connectivity across VLANs with ping tests

### VLAN Configuration Example

#### Switch configuration (for each managed switch)

```text
configure terminal
vlan 10
 name Apartment1
vlan 20
 name Apartment2
vlan 30
 name Apartment3
!
interface range fa0/1-24
 switchport mode access
 switchport access vlan 10
!
interface range fa0/1-24
 switchport mode access
 switchport access vlan 20
!
interface range fa0/1-24
 switchport mode access
 switchport access vlan 30
!

```
> Note: Adjust interface ranges and VLAN assignments for each switch according to the actual lab topology.

### Router-on-a-Stick Configuration

```text
configure terminal
interface fastEthernet0/0
 ip address 192.168.1.100 255.255.255.0
!
interface fastEthernet0/1
 ip address 192.168.2.100 255.255.255.0
!
interface Ethernet0/3/0
 ip address 192.168.3.100 255.255.255.0
!
interface fastEthernet0/0
 no shutdown
```

> Note: On a Cisco 2811 router with WIC-1ENET installed, physical Ethernet interfaces may use `fastEthernet` naming and the additional WIC port can provide a third Ethernet connection if needed.

### Static IP Addressing


- PC1 (Apartment 1): 192.168.1.100 /24, gateway 192.168.1.1
- PC2 (Apartment 1): 192.168.1.100 /24, gateway 192.168.1.1
- PC3 (Apartment 2): 192.168.2.100 /24, gateway 192.168.2.1
- PC4 (Apartment 2): 192.168.2.100 /24, gateway 192.168.2.1
- PC5 (Apartment 3): 192.168.3.100 /24, gateway 192.168.3.1
- PC6 (Apartment 3): 192.168.3.100 /24, gateway 192.168.3.1

### Verification

- Use `ping` from one PC to another host in the same VLAN to verify local connectivity.
- Use `ping` across VLANs to confirm inter-VLAN routing is functioning.
- Verify switch trunk status with `show interfaces trunk` and router subinterface status with `show ip interface brief`.

### Skills Demonstrated

- VLAN creation and segmentation
- Trunk and access port configuration
- Inter-VLAN routing (router-on-a-stick)
- Subnetting and static IP addressing
- Network troubleshooting and connectivity verification
