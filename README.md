#  Cisco Packet Tracer Labs

Hands-on Cisco Packet Tracer labs covering **CCNA networking concepts, routing, switching, network configuration, troubleshooting, and network security**.

This repository documents my practical networking experience using Cisco Packet Tracer. Each lab contains the `.pkt` file along with documentation explaining the objectives, configuration, verification, and concepts practiced.

---

# Purpose

The purpose of this repository is to develop and demonstrate practical networking skills through hands-on Cisco labs.

These labs focus on configuring, testing, verifying, and troubleshooting network environments rather than only studying networking theory.

---

## Labs

### 🔹 Static LAN
Building and configuring a basic Local Area Network.

**Concepts practiced:**
- IPv4 addressing
- Subnet masks
- Default gateways
- Switch configuration
- Router interfaces
- End-device configuration
- Ping and connectivity testing

---

### 🔹 VLANs
Configuration of VLANs to logically segment networks into separate broadcast domains.

**Concepts practiced:**
- VLAN creation
- VLAN naming
- Access ports
- Network segmentation
- Broadcast domains
- Inter-VLAN connectivity
- Connectivity testing

---

### 🔹 Trunking & Router-on-a-Stick (ROAS)
Configuration of VLAN trunk links and inter-VLAN routing using Router-on-a-Stick.

**Concepts practiced:**
- 802.1Q trunking
- Access vs trunk ports
- Native VLAN
- Router subinterfaces
- `encapsulation dot1Q`
- Inter-VLAN routing
- VLAN traffic across trunk links

---

### 🔹 OSPF & Loopback Interfaces
Configuration of dynamic routing using OSPF and logical loopback interfaces.

**Concepts practiced:**
- OSPF configuration
- OSPF neighbors
- Router ID
- Network advertisements
- Wildcard masks
- Loopback interfaces
- Routing tables
- Dynamic route learning
- OSPF verification

---

### 🔹 NAT
Configuration of Network Address Translation to translate private IPv4 addresses.

**Concepts practiced:**
- Inside and outside NAT interfaces
- Private and public IPv4 addressing
- Static NAT
- Dynamic NAT
- PAT / NAT Overload
- NAT translation tables
- NAT verification

---

### 🔹 Standard ACLs
Implementation of Standard Access Control Lists to control network communication based primarily on source IPv4 addresses.

**Concepts practiced:**
- Numbered Standard ACLs
- Named Standard ACLs
- Permit and deny statements
- Wildcard masks
- ACL placement
- Inbound and outbound filtering
- ACL verification

---

### 🔹 Extended ACLs
Implementation of granular network traffic filtering using Extended Access Control Lists.

**Concepts practiced:**
- Source and destination filtering
- TCP and UDP filtering
- DNS traffic control
- HTTP/HTTPS traffic control
- Port-based filtering
- ACL placement
- ACL troubleshooting

---

### 🔹 Switch Port Security
Configuration of Layer 2 security mechanisms to control which devices can communicate through switch interfaces.

**Concepts practiced:**
- Port Security
- Maximum MAC address limits
- Sticky MAC learning
- MAC address aging
- Shutdown violation mode
- Restrict violation mode
- Port-security verification
- Security violation testing

---

## 🛠️ Technologies & Skills

- Cisco Packet Tracer
- Cisco IOS
- IPv4
- Subnetting
- LAN Configuration
- VLANs
- 802.1Q Trunking
- Router-on-a-Stick
- Static Routing
- OSPF
- Loopback Interfaces
- NAT / PAT
- Standard ACLs
- Extended ACLs
- Port Security
- Layer 2 Switching
- Layer 3 Routing
- Network Troubleshooting
- Network Security

---

## 🔍 Verification & Troubleshooting

Throughout the labs, Cisco IOS verification and troubleshooting commands are used, including:

```bash
show ip interface brief
show running-config
show vlan brief
show interfaces trunk
show interfaces switchport
show ip route
show ip ospf neighbor
show ip protocols
show access-lists
show ip nat translations
show port-security
```

Connectivity is tested using tools such as:

```bash
ping
traceroute
```

Cisco Packet Tracer's **Simulation Mode** is also used to visualize packet flow and understand how switches and routers process network traffic.

---

## 📂 Repository Structure

```text
packet-tracer/
│
├── README.md
│
└── pakt-labs/
    │
    ├── 01-static-lan/
    │   ├── README.md
    │   └── Static-LAN.pkt
    │
    ├── 02-vlans/
    │   ├── README.md
    │   └── VLANs.pkt
    │
    ├── 03-trunking-roas/
    │   ├── README.md
    │   └── Trunking-ROAS.pkt
    │
    ├── 04-ospf-loopback/
    │   ├── README.md
    │   └── OSPF-Loopback.pkt
    │
    ├── 05-nat/
    │   ├── README.md
    │   └── NAT.pkt
    │
    ├── 06-acls/
    │   ├── standard-acl/
    │   │   ├── README.md
    │   │   └── Standard-ACL.pkt
    │   │
    │   └── extended-acl/
    │       ├── README.md
    │       └── Extended-ACL.pkt
    │
    └── 07-port-security/
        ├── README.md
        └── Port-Security.pkt
```

Each lab folder contains the **Packet Tracer lab file** and a dedicated **README** documenting what was configured and learned.

---

##  Learning Goals

Through these labs, I aim to strengthen my practical understanding of:

- Network design and implementation
- Cisco router and switch configuration
- Routing and switching
- VLAN segmentation
- Inter-VLAN routing
- Dynamic routing with OSPF
- Network Address Translation
- Traffic filtering and access control
- Layer 2 network security
- Network troubleshooting

---

##  Certification Focus

These labs are primarily based on concepts covered in the **Cisco CCNA (200-301)** curriculum and are intended to strengthen networking fundamentals relevant to **cybersecurity and cloud security**.

---

##  Author

**Mohammed Zaid Baig**

B.Tech Computer Science Engineering  
Cybersecurity & Cloud Security Enthusiast

This repository represents my ongoing hands-on networking practice and will continue to be updated with additional labs.
