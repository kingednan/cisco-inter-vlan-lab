## Multi-VLAN Residential Network Lab

This repository documents a Cisco Packet Tracer lab that simulates a small residential network with three isolated VLANs representing separate apartment units. Inter-VLAN routing is configured using a router-on-a-stick topology.

### Network Topology

- VLAN 10: Apartment 1 - 192.168.1.0/24
- VLAN 20: Apartment 2 - 192.168.2.0/24
- VLAN 30: Apartment 3 - 192.168.3.0/24

Devices:

- 1 Router for inter-VLAN routing via subinterfaces
- 3 Managed switches (one per VLAN)
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
interface range fa0/1-2
 switchport mode access
 switchport access vlan 10
!
interface range fa0/3-4
 switchport mode access
 switchport access vlan 20
!
interface range fa0/5-6
 switchport mode access
 switchport access vlan 30
!
interface fa0/24
 switchport trunk encapsulation dot1q
 switchport mode trunk
```

> Note: Adjust interface ranges and VLAN assignments for each switch according to the actual lab topology.

### Router-on-a-Stick Configuration

```text
configure terminal
interface gigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.1.1 255.255.255.0
!
interface gigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.2.1 255.255.255.0
!
interface gigabitEthernet0/0.30
 encapsulation dot1Q 30
 ip address 192.168.3.1 255.255.255.0
!
interface gigabitEthernet0/0
 no shutdown
```

### Static IP Addressing


- PC1 (Apartment 1): 192.168.1.100 /24, gateway 192.168.1.1
- PC2 (Apartment 1): 192.168.1.100 /24, gateway 192.168.1.2
- PC3 (Apartment 2): 192.168.2.100 /24, gateway 192.168.2.1
- PC4 (Apartment 2): 192.168.2.100 /24, gateway 192.168.2.2
- PC5 (Apartment 3): 192.168.3.100 /24, gateway 192.168.3.1
- PC6 (Apartment 3): 192.168.3.100 /24, gateway 192.168.3.2

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
