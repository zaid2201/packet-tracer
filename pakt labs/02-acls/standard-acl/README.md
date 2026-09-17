# Standard ACL Configuration Lab

## 📌 Overview

This Cisco Packet Tracer lab demonstrates the configuration of **OSPF routing** and **Standard Access Control Lists (ACLs)** to control communication between different IPv4 networks.

R1 uses **standard numbered ACLs**, while R2 uses **standard named ACLs**.

## 🎯 Objectives

- Configure OSPF on R1 and R2
- Establish full connectivity between PCs and servers before applying ACLs
- Configure standard numbered ACLs on R1
- Configure standard named ACLs on R2
- Permit or deny traffic based on source IPv4 addresses
- Apply ACLs to the appropriate router interfaces
- Verify ACL operation using ping and Cisco IOS commands

## 🌐 Network Policies

The ACLs must enforce the following requirements:

- Only **PC1 and PC3** can access the `192.168.1.0/24` network.
- Hosts in `172.16.2.0/24` cannot access `192.168.2.0/24`.
- Hosts in `172.16.1.0/24` cannot access `172.16.2.0/24`.
- Hosts in `172.16.2.0/24` cannot access `172.16.1.0/24`.

## 🔄 OSPF Configuration

OSPF is configured on **R1 and R2** so that all required networks are dynamically advertised between the routers.

Before applying the ACLs, connectivity should be tested to confirm that routing is functioning correctly.

Useful verification commands:

```bash
show ip ospf neighbor
show ip route ospf
show ip protocols
```

## 🔐 Standard Numbered ACLs — R1

R1 uses **standard numbered ACLs**.

Standard ACLs primarily examine the **source IPv4 address** when deciding whether traffic should be permitted or denied.

Example syntax:

```bash
access-list 10 permit <source> <wildcard-mask>
access-list 10 deny <source> <wildcard-mask>
```

The ACL can then be applied to an interface:

```bash
interface <interface>
ip access-group 10 in
```

or:

```bash
interface <interface>
ip access-group 10 out
```

## Standard Named ACLs — R2

R2 uses **standard named ACLs**.

Example syntax:

```bash
ip access-list standard <ACL-NAME>
 permit <source> <wildcard-mask>
 deny <source> <wildcard-mask>
```

The named ACL is then applied to the appropriate interface:

```bash
interface <interface>
ip access-group <ACL-NAME> in
```

or:

```bash
ip access-group <ACL-NAME> out
```

## 🔍 Verification & Testing

ACL configuration can be verified using:

```bash
show access-lists
show ip access-lists
show ip interface
show running-config
```

Connectivity can be tested using:

```bash
ping <destination-ip>
```

The results should confirm that permitted traffic succeeds while traffic prohibited by the network policies is blocked.

##  What I Learned

Through this lab, I practiced combining **dynamic routing with network traffic filtering**.

I configured OSPF to provide connectivity between multiple networks and then used Standard ACLs to restrict communication according to specific security policies.

I also practiced the difference between **numbered and named Standard ACLs**, wildcard masks, ACL ordering, interface placement, and inbound/outbound ACL direction.

This lab reinforced an important characteristic of Standard ACLs: because they primarily filter based on the **source address**, careful ACL placement is necessary to avoid unintentionally blocking traffic to other destinations.

##  Technologies & Concepts Used

- Cisco Packet Tracer
- Cisco IOS
- OSPF
- Standard ACLs
- Numbered ACLs
- Named ACLs
- IPv4
- Wildcard Masks
- ICMP
- Routing
- Traffic Filtering
