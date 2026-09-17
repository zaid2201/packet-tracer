# Switch Port Security Lab

##  Overview

This Cisco Packet Tracer lab demonstrates the configuration of **switch port security** and compares different port-security violation modes.

Port security is used to control which MAC addresses are allowed to communicate through a switch interface.

##  Objectives

- Configure port security on Cisco switches
- Set maximum allowed MAC addresses
- Configure Shutdown and Restrict violation modes
- Configure sticky MAC address learning
- Configure MAC address aging
- Trigger port-security violations
- Observe how switches respond to different violations
- Verify port-security status using Cisco IOS commands

##  SW1 Port Security Configuration

Port security is configured on:

- `F0/1`
- `F0/2`
- `F0/3`

### Requirements

| Setting | Configuration |
|---|---|
| Violation Mode | Shutdown |
| Maximum MAC Addresses | 1 |
| Sticky Learning | Disabled |
| Aging Time | 1 hour |

Example configuration:

```bash
enable
configure terminal

interface range f0/1 - 3
switchport mode access
switchport port-security
switchport port-security maximum 1
switchport port-security violation shutdown
switchport port-security aging time 60
```

With **Shutdown** mode, a security violation causes the interface to enter an error-disabled state.

## 🔐 SW2 Port Security Configuration

Port security is configured on:

`G0/1`

### Requirements

| Setting | Configuration |
|---|---|
| Violation Mode | Restrict |
| Maximum MAC Addresses | 4 |
| Sticky Learning | Enabled |

Example configuration:

```bash
enable
configure terminal

interface g0/1
switchport mode access
switchport port-security
switchport port-security maximum 4
switchport port-security violation restrict
switchport port-security mac-address sticky
```

With **Restrict** mode, frames from unauthorized MAC addresses are dropped and the violation counter increases, but the interface remains operational.

## 🚨 Triggering Port Security Violations

After configuring port security, violations are intentionally triggered by connecting additional devices to the secured interfaces.

This allows the behavior of the two violation modes to be observed.

### SW1 — Shutdown Mode

When an unauthorized MAC address causes a violation:

- The port is shut down
- The interface enters an error-disabled state
- Traffic through that interface is stopped

### SW2 — Restrict Mode

When an unauthorized MAC address causes a violation:

- Unauthorized traffic is dropped
- The violation counter increases
- The interface remains operational
- Valid traffic can continue to pass

## 🔍 Verification

Port-security configuration can be checked using:

```bash
show port-security
```

To inspect a particular interface:

```bash
show port-security interface f0/1
```

or:

```bash
show port-security interface g0/1
```

The learned secure MAC addresses can be checked using:

```bash
show port-security address
```

Interface status can also be verified with:

```bash
show interfaces status
```

## 🧠 What I Learned

Through this lab, I practiced configuring Cisco switch port security to control which devices can access the network based on their MAC addresses.

I learned the difference between **Shutdown** and **Restrict** violation modes and observed how each mode responds when an unauthorized device is connected.

I also practiced configuring maximum MAC address limits, sticky MAC learning, MAC address aging, and verifying port-security violations using Cisco IOS commands.

## 🛠️ Technologies & Concepts Used

- Cisco Packet Tracer
- Cisco IOS
- Layer 2 Switching
- Port Security
- MAC Addresses
- Sticky MAC Learning
- MAC Address Aging
- Shutdown Violation Mode
- Restrict Violation Mode
- Network Access Control
