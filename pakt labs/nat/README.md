# 🌐 Static NAT Configuration Lab

## 📌 Overview

This Cisco Packet Tracer lab demonstrates the configuration of **Static Network Address Translation (Static NAT)** on a Cisco router.

The internal network uses private IPv4 addresses from `172.16.0.0/24`, while R1 connects to an external network through the `203.0.113.0/30` WAN network.

Static NAT is used to create a permanent **one-to-one mapping** between an inside local address and an inside global address.

---

## 🖥️ Network Topology

The topology consists of:

- 3 PCs
- 1 Cisco 2960 switch (SW1)
- 1 Cisco 2911 router (R1)
- Internet/WAN router
- External server (`8.8.8.8`)

### IP Addressing

| Device | IP Address | Purpose |
|---|---|---|
| PC1 | `172.16.0.1` | Internal Host |
| PC2 | `172.16.0.2` | Internal Host |
| PC3 | `172.16.0.3` | Internal Host |
| R1 G0/1 | `172.16.0.254` | LAN Default Gateway |
| R1 G0/0 | `203.0.113.1` | WAN Interface |
| Internet Router | `203.0.113.2` | External Router |
| Server | `8.8.8.8` | External Server |

---

## 🎯 Objectives

- Configure IPv4 addressing on network devices
- Configure inside and outside NAT interfaces
- Configure Static NAT
- Understand inside local and inside global addresses
- Translate a private IPv4 address to a public/global address
- Test connectivity with an external server
- Verify NAT translations using Cisco IOS commands

---

## 🔐 Static NAT

Static NAT creates a permanent **one-to-one translation** between two IPv4 addresses.

For example:

```text
Inside Local Address  →  Inside Global Address
172.16.0.x            →  Public/Global IPv4 Address
```

The **inside local** address represents the internal host's address on the private network.

The **inside global** address represents that internal host to the outside network.

---

## ⚙️ NAT Interface Configuration

The LAN-facing interface on R1 is configured as the NAT **inside** interface:

```bash
interface g0/1
ip nat inside
```

The WAN-facing interface is configured as the NAT **outside** interface:

```bash
interface g0/0
ip nat outside
```

---

## 🔄 Static NAT Configuration

A static translation is configured using:

```bash
ip nat inside source static <inside-local-ip> <inside-global-ip>
```

This creates a permanent mapping between an internal private address and an address used to represent that host on the external network.

---

## 🔍 Verification

NAT translations can be checked using:

```bash
show ip nat translations
```

NAT statistics can be viewed using:

```bash
show ip nat statistics
```

Interface configuration can be verified using:

```bash
show ip interface brief
show running-config
```

---

## 🧪 Connectivity Testing

Connectivity to the external server can be tested using:

```bash
ping 8.8.8.8
```

Packet Tracer's **Simulation Mode** can also be used to observe how R1 translates the source IPv4 address as traffic moves between the inside and outside networks.

---

## 🧠 What I Learned

Through this lab, I practiced configuring **Static NAT** on a Cisco router and learned how private IPv4 addresses can be translated when communicating with an external network.

I learned the difference between **inside local** and **inside global** addresses and how to identify the NAT inside and outside interfaces.

I also practiced verifying NAT translations and testing communication between an internal LAN and an external server.

---

## 🛠️ Technologies & Concepts Used

- Cisco Packet Tracer
- Cisco IOS
- Static NAT
- IPv4
- Private and Global IP Addressing
- Inside Local Address
- Inside Global Address
- LAN/WAN Connectivity
- Routing
- ICMP
- Network Troubleshooting

---

## 📁 Lab File

`Static-NAT.pkt`
