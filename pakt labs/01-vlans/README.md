# VLAN Configuration Lab

## 📌 Overview

This Cisco Packet Tracer lab demonstrates how VLANs can be used to logically separate devices into different broadcast domains while using the same switching infrastructure.

The lab consists of three VLANs representing different departments:

- Engineering
- HR
- Sales

## 🎯 Objectives

- Configure IPv4 addresses and subnet masks on PCs
- Configure the default gateway using the last usable IP address of each subnet
- Create three connections between the router and switch
- Configure a separate router interface for each VLAN
- Create and name VLANs on the switch
- Assign switch interfaces to the correct VLANs
- Configure interfaces connecting the switch to the router
- Test communication between different VLANs
- Observe broadcast traffic using Packet Tracer Simulation Mode

## ⚙️ Lab Tasks

### 1. Configure the PCs

Configure the correct:

- IP address
- Subnet mask
- Default gateway

The **last usable IP address of each subnet** is used as the default gateway.

### 2. Configure R1

Create three physical connections between **R1** and **SW1**.

Configure one router interface for each VLAN.

Each router interface should use the same gateway IP address that was configured as the default gateway on the PCs in that VLAN.

### 3. Configure VLANs on SW1

Create and name the following VLANs:

- Engineering
- HR
- Sales

Assign the appropriate switch interfaces to their respective VLANs.

The switch interfaces connecting to R1 must also be placed in the appropriate VLAN.

### 4. Test Connectivity

Use `ping` to verify connectivity between PCs.

Example:

```bash
ping <destination-ip>
