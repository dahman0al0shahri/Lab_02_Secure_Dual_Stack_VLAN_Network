# Lab 02 - Secure Dual-Stack VLAN Network

A Cisco Packet Tracer lab that demonstrates a secure dual-stack VLAN network using Router-on-a-Stick, IPv4 VLSM, IPv6 routing, DHCPv4, DNS/HTTP services, SSH management, Port Security, and unused port protection.

## Lab Overview

This lab builds a segmented enterprise-style network using VLANs and inter-VLAN routing. The design separates users, staff, services, and management traffic while applying basic Layer 2 and management security controls.

## Topology

| Device | Role |
|---|---|
| R1 | Router-on-a-Stick inter-VLAN router |
| SW1 | Cisco 2960 access switch |
| PC-A | User client - VLAN 10 |
| PC-B | Staff client - VLAN 20 |
| SRV1 | DNS and HTTP server - VLAN 30 |
| MGMT-PC | Management host - VLAN 99 |

## VLAN Plan

| VLAN | Name | Purpose | IPv4 Network | IPv6 Network |
|---|---|---|---|---|
| 10 | LAN_A_USERS | Users | 172.16.50.0/26 | 2001:DB8:ACAD:10::/64 |
| 20 | LAN_B_STAFF | Staff | 172.16.50.64/27 | 2001:DB8:ACAD:20::/64 |
| 30 | SERVERS | Services | 172.16.50.96/28 | 2001:DB8:ACAD:30::/64 |
| 99 | MANAGEMENT | Management | 172.16.50.112/29 | 2001:DB8:ACAD:99::/64 |
| 999 | NATIVE_UNUSED | Native and unused ports | No IP assigned | No IP assigned |

## Key Features Implemented

- Router-on-a-Stick inter-VLAN routing
- IPv4 VLSM addressing
- IPv6 dual-stack routing
- DHCPv4 pools for client VLANs
- DNS record for `lab.dahman.local`
- HTTP service test from client devices
- SSH-only management access
- Local username authentication
- Port Security with sticky MAC addresses
- Restrict violation mode
- Unused ports isolated in VLAN 999 and shut down
- Native VLAN changed to VLAN 999
- VLAN 1 disabled where applicable

## Lab Access Credentials

These credentials are included only for educational verification inside the Packet Tracer lab. They are not real production credentials.

| Access Type | Username | Password | Notes |
|---|---:|---:|---|
| Console access | N/A | `Console@123` | Used for local console login on R1 and SW1 |
| Privileged EXEC mode | N/A | `CTE@12345` | Used with the `enable` command |
| SSH access | `admin` | `Admin@12345` | Used for SSH management access to R1 and SW1 |

### SSH Verification Commands

From MGMT-PC Command Prompt:

```text
ssh -l admin 172.16.50.113
ssh -l admin 172.16.50.114
```

| Device | Management IP | Protocol |
|---|---:|---|
| R1 | 172.16.50.113 | SSH |
| SW1 | 172.16.50.114 | SSH |

## Verification Summary

The lab was verified with these checks:

- VLAN assignment on SW1
- 802.1Q trunk status between SW1 and R1
- R1 IPv4 and IPv6 subinterfaces
- DHCPv4 bindings for client devices
- DNS and HTTP service resolution through `lab.dahman.local`
- SSH access from MGMT-PC to R1 and SW1
- Port Security status and sticky MAC table
- Unused ports in VLAN 999 with shutdown state
- IPv4 end-to-end connectivity
- IPv6 end-to-end connectivity

## Project File

The Packet Tracer file should be uploaded with this name:

`Lab_02_Secure_Dual_Stack_VLAN_Network_Dahman_AlShehri.pkt`

## Notes

This lab is part of a practical networking portfolio focused on building real troubleshooting, documentation, and network design skills.

The published credentials above are intentionally included to allow reviewers, students, and instructors to verify the lab configuration inside Cisco Packet Tracer.

## Author

**Dahman Fayez Al-Shehri**  
Networking and Telecommunications Student  
GitHub: [dahman0al0shahri](https://github.com/dahman0al0shahri)
