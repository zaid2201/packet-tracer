# Extended ACL Configuration Lab

## 📌 Overview

This Cisco Packet Tracer lab demonstrates the configuration of **Extended Access Control Lists (ACLs)** to enforce specific network security policies.

Unlike Standard ACLs, Extended ACLs can filter traffic based on the **source address, destination address, protocol, and port number**, allowing more precise control over network communication.

## 🎯 Objectives

- Configure Extended ACLs
- Filter traffic based on source and destination IPv4 addresses
- Restrict access to specific network services
- Control DNS, HTTP, and HTTPS traffic
- Apply ACLs to the appropriate router interfaces
- Understand inbound and outbound ACL placement
- Verify ACL operation using connectivity and service testing

## 🔐 Network Security Policies

The Extended ACLs must enforce the following requirements:

- Hosts in `172.16.2.0/24` cannot communicate with **PC1**.
- Hosts in `172.16.1.0/24` cannot access the **DNS service on SRV1**.
- Hosts in `172.16.2.0/24` cannot access the **HTTP or HTTPS services on SRV2**.

Other traffic should be permitted unless explicitly restricted by the ACL policies.

## 🌐 Services Controlled

### DNS

DNS uses:

- UDP port `53`
- TCP port `53`

Extended ACLs can be used to prevent selected networks from accessing the DNS service while allowing other traffic.

### HTTP

HTTP web traffic uses:

`TCP port 80`

### HTTPS

HTTPS web traffic uses:

`TCP port 443`

The ACL can therefore block HTTP and HTTPS access to SRV2 without necessarily preventing access to other services.

## ⚙️ Extended ACL Syntax

Example extended ACL syntax:

```bash
access-list 100 deny ip <source> <source-wildcard> host <destination>
```

To block a particular TCP service:

```bash
access-list 100 deny tcp <source> <source-wildcard> host <destination> eq <port>
```

For example, HTTP uses:

```bash
eq 80
```

and HTTPS uses:

```bash
eq 443
```

After the required deny statements, permitted traffic must be considered because ACLs contain an **implicit deny** at the end.

Example:

```bash
access-list 100 permit ip any any
```

## 🔌 Applying the ACL

The ACL is applied to the appropriate router interface using:

```bash
interface <interface>
ip access-group 100 in
```

or:

```bash
interface <interface>
ip access-group 100 out
```

Extended ACLs are generally placed **close to the source** of the traffic being filtered.

## 🔍 Verification

Useful commands for checking the ACL configuration:

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

DNS, HTTP, and HTTPS services can also be tested from the PCs to verify that the ACL blocks only the required traffic.

## 🧠 What I Learned

Through this lab, I practiced using Extended ACLs to implement more granular network security policies.

I learned how Extended ACLs can filter traffic using source and destination addresses, protocols, and TCP/UDP port numbers.

I also practiced restricting specific services such as **DNS, HTTP, and HTTPS** while allowing other legitimate network traffic.

This lab reinforced my understanding of ACL ordering, wildcard masks, service port numbers, ACL placement, and the implicit deny rule.

## 🛠️ Technologies & Concepts Used

- Cisco Packet Tracer
- Cisco IOS
- Extended ACLs
- IPv4
- TCP
- UDP
- DNS
- HTTP
- HTTPS
- Wildcard Masks
- Network Traffic Filtering
- Access Control
