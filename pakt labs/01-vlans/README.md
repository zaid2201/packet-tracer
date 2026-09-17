# VLAN Configuration Lab

## Overview

This Cisco Packet Tracer lab demonstrates the configuration and use of VLANs (Virtual Local Area Networks) on Cisco switches.

The purpose of the lab is to understand how VLANs can logically separate devices into different broadcast domains even when they are connected to the same physical switch infrastructure.

## Objectives

- Create and configure VLANs
- Assign switch ports to specific VLANs
- Configure access ports
- Understand VLAN-based network segmentation
- Verify VLAN configuration
- Test connectivity between devices
- Practice basic Cisco IOS commands

##  Technologies Used

- Cisco Packet Tracer
- Cisco IOS
- Ethernet Switching
- VLANs
- IPv4 Networking

##  Basic VLAN Configuration

Example VLAN creation:

```bash
enable
configure terminal

vlan 10
name VLAN10

vlan 20
name VLAN20
