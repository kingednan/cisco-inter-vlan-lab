Multi-VLAN Residential Network Lab
Tool: Cisco Packet Tracer
Overview
This lab simulates a small residential network divided into three isolated VLANs representing separate apartment units. Inter-VLAN routing is configured to allow controlled communication between segments using a router-on-a-stick topology.
Network Topology
VLANNameSubnet10Apartment1192.168.1.0/2420Apartment2192.168.2.0/2430Apartment3192.168.3.0/24
Devices used:

1 Router (inter-VLAN routing via subinterfaces)
3 Managed Switches (one per VLAN)
6 PCs (2 per switch, static IP assignment)

What Was Configured

Created and named VLANs on each switch
Assigned access ports to the correct VLAN per PC
Configured trunk links between switches and the router
Set up router subinterfaces for each VLAN (router-on-a-stick)
Assigned static IP addresses to all end devices
Verified connectivity between VLANs using ping tests

Skills Demonstrated

VLAN creation and segmentation
Trunk and access port configuration
Inter-VLAN routing (router-on-a-stick)
Subnetting and static IP addressing
Network troubleshooting and connectivity verification
