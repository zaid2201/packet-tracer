# Standard ACL Lab

##  Overview

This Cisco Packet Tracer lab demonstrates the configuration and use of Standard Access Control Lists (ACLs).

Standard ACLs filter IPv4 traffic primarily based on the **source IP address**.

## Objectives

- Configure a Standard ACL
- Use permit and deny statements
- Work with wildcard masks
- Apply an ACL to a router interface
- Understand inbound and outbound ACL placement
- Verify ACL operation
- Test network connectivity

##  Example Configuration
interface gigabitEthernet0/0
ip access-group 10 out
##  Verification
show access-lists
show ip interface
show running-config

