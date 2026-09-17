# 🔄 OSPF, Loopback & Default Route Lab

## 📌 Overview

This Cisco Packet Tracer lab demonstrates the configuration of **OSPF (Open Shortest Path First)** across multiple routers.

The lab includes loopback interfaces, passive OSPF interfaces, default-route advertisement, and the configuration of R1 as an **Autonomous System Boundary Router (ASBR)**.

R1 provides the OSPF domain with a default route toward the external/Internet network.

---

## 🎯 Objectives

- Configure router hostnames
- Configure IPv4 addresses on router interfaces
- Enable router interfaces
- Create loopback interfaces on each router
- Configure OSPF
- Advertise router interfaces and loopbacks through OSPF
- Configure appropriate OSPF passive interfaces
- Prevent OSPF from running on R1's Internet-facing link
- Configure a default route on R1
- Configure R1 as an OSPF ASBR
- Advertise the default route into the OSPF domain
- Verify OSPF neighbors and learned routes
- Examine the default routes installed on R2, R3, and R4

---

## 🌐 Router Configuration

Each router is configured with the appropriate:

- Hostname
- IPv4 addresses
- Subnet masks
- Enabled interfaces

Example:

```bash
enable
configure terminal

hostname R1

interface g0/0
ip address <IP-ADDRESS> <SUBNET-MASK>
no shutdown
```

The ISP router does not require configuration for this lab.

---

## 🔁 Loopback Interfaces

A loopback interface is configured on each router.

### R1

```bash
interface loopback0
ip address 1.1.1.1 255.255.255.255
```

### R2

```bash
interface loopback0
ip address 2.2.2.2 255.255.255.255
```

### R3

```bash
interface loopback0
ip address 3.3.3.3 255.255.255.255
```

### R4

```bash
interface loopback0
ip address 4.4.4.4 255.255.255.255
```

Each loopback uses a `/32` subnet mask.

---

## 🔄 OSPF Configuration

OSPF is configured on each router so routes can be dynamically exchanged throughout the network.

Example:

```bash
router ospf 1
```

OSPF is enabled for the appropriate router interfaces, including the loopback interfaces.

R1's Internet-facing interface is **not included in OSPF**.

---

## 🔇 Passive Interfaces

Interfaces that should advertise their network through OSPF but do not need to form OSPF neighbor relationships are configured as passive.

Example:

```bash
router ospf 1
passive-interface loopback0
```

Loopback interfaces are configured as passive because there is no OSPF router on the other end with which to form an adjacency.

Other interfaces connected only to end-device LANs can also be configured as passive where appropriate.

---

## 🌍 Default Route on R1

R1 acts as the edge router between the internal OSPF network and the external/Internet network.

A default route is configured pointing toward the ISP:

```bash
ip route 0.0.0.0 0.0.0.0 <NEXT-HOP-IP>
```

This tells R1 where to forward packets when no more specific route exists in its routing table.

---

## 🚪 R1 as an OSPF ASBR

R1 is configured to advertise its default route into the OSPF domain.

Under the OSPF configuration:

```bash
router ospf 1
default-information originate
```

Because R1 redistributes/advertises external routing information into the OSPF domain, it operates as an **ASBR (Autonomous System Boundary Router)**.

Other OSPF routers can then learn that R1 is the path toward networks outside the OSPF domain.

---

## 🗺️ Routing Table Verification

The routing tables on R2, R3, and R4 can be examined using:

```bash
show ip route
```

OSPF-learned routes are identified by:

```text
O
```

An OSPF external Type 2 route is identified by:

```text
O E2
```

The OSPF-learned default route will typically appear in a form similar to:

```text
O*E2 0.0.0.0/0
```

Where:

- `O` = Learned through OSPF
- `*` = Candidate default route
- `E2` = OSPF External Type 2 route
- `0.0.0.0/0` = Default route

---

## 🔍 OSPF Verification

Check OSPF neighbors:

```bash
show ip ospf neighbor
```

Check OSPF-enabled interfaces:

```bash
show ip ospf interface brief
```

Check OSPF information:

```bash
show ip protocols
```

Check the routing table:

```bash
show ip route
```

View only OSPF-learned routes:

```bash
show ip route ospf
```

---

## 🧪 Connectivity Testing

Connectivity between routers and loopback interfaces can be tested using:

```bash
ping <destination-ip>
```

For example:

```bash
ping 2.2.2.2
ping 3.3.3.3
ping 4.4.4.4
```

Successful pings help confirm that OSPF routes are being learned correctly throughout the network.

---

## 🧠 What I Learned

Through this lab, I practiced configuring **multi-router OSPF networks** and verifying OSPF neighbor relationships and dynamically learned routes.

I learned how loopback interfaces can participate in OSPF while being configured as passive interfaces.

I also learned how an edge router can use `default-information originate` to advertise a default route into an OSPF domain.

The lab helped me understand the role of an **ASBR**, OSPF external routes, passive interfaces, default routing, and how downstream routers learn a path toward networks outside the OSPF domain.

---

## 🛠️ Technologies & Concepts Used

- Cisco Packet Tracer
- Cisco IOS
- OSPF
- Dynamic Routing
- Loopback Interfaces
- Passive Interfaces
- Default Routes
- ASBR
- OSPF External Routes
- OSPF E2 Routes
- IPv4 Addressing
- Routing Tables
- Network Troubleshooting

---

