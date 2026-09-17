# 🔀 VLAN Trunking & Router-on-a-Stick (ROAS) Lab

## 📌 Overview

This Cisco Packet Tracer lab demonstrates the configuration of **VLANs, 802.1Q trunking, and Router-on-a-Stick (ROAS)** to provide communication between devices located in different VLANs.

The switches are connected using a trunk link, while the connection between SW2 and R1 uses Router-on-a-Stick to perform inter-VLAN routing.

---

## 🎯 Objectives

- Create the necessary VLANs on both switches
- Configure PC-facing switch interfaces as access ports
- Assign access ports to the correct VLANs
- Configure an 802.1Q trunk between SW1 and SW2
- Allow only the required VLANs across the trunk
- Configure an unused VLAN as the native VLAN
- Configure Router-on-a-Stick between SW2 and R1
- Create router subinterfaces for each VLAN
- Configure 802.1Q encapsulation
- Use the last usable address of each subnet as the default gateway
- Verify inter-VLAN connectivity using ping

---

## 🔌 Access Port Configuration

Interfaces connected to PCs are configured as **access ports** and assigned to their appropriate VLAN.

Example:

```bash
interface f0/1
switchport mode access
switchport access vlan <VLAN-ID>
```

The required VLANs must exist on the switch before interfaces are assigned to them.

Example:

```bash
vlan 10
name <VLAN-NAME>

vlan 20
name <VLAN-NAME>
```

---

## 🔀 SW1 ↔ SW2 Trunk

The connection between **SW1 and SW2** is configured as an 802.1Q trunk.

Example:

```bash
interface <interface>
switchport mode trunk
```

Only the VLANs required by the network are allowed across the trunk:

```bash
switchport trunk allowed vlan <VLAN-LIST>
```

An unused VLAN is configured as the **native VLAN**:

```bash
switchport trunk native vlan <UNUSED-VLAN-ID>
```

The native VLAN configuration should match on both ends of the trunk.

---

## 🌐 Router-on-a-Stick

The connection between **SW2 and R1** is used for Router-on-a-Stick.

A single physical router interface carries traffic for multiple VLANs using **802.1Q tagging**.

The switch interface connected to R1 is configured as a trunk:

```bash
interface <interface>
switchport mode trunk
switchport trunk allowed vlan <VLAN-LIST>
```

---

## ⚙️ Router Subinterfaces

R1 uses a separate logical subinterface for each VLAN.

Example:

```bash
interface g0/0.10
encapsulation dot1Q 10
ip address <LAST-USABLE-IP> <SUBNET-MASK>

interface g0/0.20
encapsulation dot1Q 20
ip address <LAST-USABLE-IP> <SUBNET-MASK>
```

Each subinterface is associated with its VLAN using:

```bash
encapsulation dot1Q <VLAN-ID>
```

The **last usable IPv4 address of each subnet** is assigned to the corresponding router subinterface.

This address is also configured as the **default gateway** for PCs belonging to that VLAN.

---

## 🔍 Verification

VLAN configuration can be checked using:

```bash
show vlan brief
```

Trunk links can be verified using:

```bash
show interfaces trunk
```

Switchport configuration can be checked using:

```bash
show interfaces switchport
```

R1 interfaces and subinterfaces can be verified using:

```bash
show ip interface brief
```

The router's routing table can be checked using:

```bash
show ip route
```

---

## 🧪 Connectivity Testing

After completing the configuration, connectivity is tested by pinging between PCs in different VLANs.

```bash
ping <destination-ip>
```

All PCs should be able to communicate with each other.

Successful communication between different VLANs confirms that:

- Access ports are assigned correctly
- VLANs exist on the required switches
- The SW1–SW2 trunk is operational
- Required VLANs are allowed across the trunk
- Router-on-a-Stick is configured correctly
- R1's subinterfaces are functioning as the VLAN default gateways

---

## 🧠 What I Learned

Through this lab, I practiced configuring **VLAN access ports, 802.1Q trunk links, native VLANs, and Router-on-a-Stick**.

I learned how trunk links allow traffic from multiple VLANs to travel between switches and how allowed VLAN lists can restrict which VLANs are carried across a trunk.

I also learned how Router-on-a-Stick uses multiple router subinterfaces on a single physical interface to provide **inter-VLAN routing**.

This lab reinforced my understanding of VLAN segmentation, trunking, 802.1Q tagging, native VLANs, default gateways, router subinterfaces, and inter-VLAN communication.

---

## 🛠️ Technologies & Concepts Used

- Cisco Packet Tracer
- Cisco IOS
- VLANs
- Access Ports
- 802.1Q Trunking
- Native VLAN
- Allowed VLANs
- Router-on-a-Stick (ROAS)
- Router Subinterfaces
- Inter-VLAN Routing
- IPv4 Addressing
- Subnetting
- Default Gateways
- ICMP
- Network Troubleshooting

---

