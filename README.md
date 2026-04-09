## 📌 Overview
A documentation of intermediate-level networking concepts covering hierarchical network design, virtualization, cloud services, and core protocol operations. Based on the Cisco Networking. Devices course from Cisco Skills for All (NetAcad).

**Course:** Cisco Networking Devices
**Platform:** Cisco Skills for All (NetAcad)
**Status:** Ongoing

## 🎯 Learning Objectives
- Apply number system conversions across decimal, binary, and hexadecimal
- Understand hierarchical network design and how devices operate at each layer
- Analyze how Ethernet, ARP, DNS, and DHCP work within a network
- Configure basic Cisco devices using IOS CLI commands
- Explore transport layer protocols and how data flows end-to-end

## 📚 Topics Covered
| Module | Topic |
|--------|-------|
| 01 | Network Design & Hierarchy |
| 02 | Cloud and Virtualization |
| 03 | Number Systems (Decimal, Binary, Hex) |
| 04 | Ethernet Switching |
| 05 | Network Layer |
| 06 | IPv4 Address Structure |
| 07 | Address Resolution (ARP) |
| 08 | IP Addressing Services (DNS & DHCP) |
| 09 | Transport Layer (TCP & UDP) |
| 10 | Cisco IOS Command Line |
| 11 | Build a Small Cisco Network |
| 12 | ICMP & Network Testing |

---

## 🧪 Labs Covered
| Lab | Concepts Practiced |
|-----|--------------------|
| Basic Switch Config | VLAN setup, port assignment |
| IPv4 Addressing | Subnetting, static IP configuration |
| ARP & DNS | Address resolution, name lookup |
| DHCP Setup | Automatic IP assignment |
| Small Network Build | End-to-end device configuration |

---

## 🛠️ Tools Used
- **Cisco Packet Tracer** — network simulation and lab work
- **Cisco IOS CLI** — device configuration and verification commands

---

## 💡 Sample IOS Commands
```bash
# Basic switch configuration
Switch> enable
Switch# configure terminal
Switch(config)# hostname SW1
Switch(config)# interface vlan 1
Switch(config-if)# ip address 192.168.1.2 255.255.255.0
Switch(config-if)# no shutdown

# Verify ARP and connectivity
Switch# show arp
Switch# ping 192.168.1.1
```

---

## ⚠️ Disclaimer
This repository is for **educational purposes only**. All content is based on the
Cisco Networking Devices course curriculum from Cisco Skills for All (NetAcad).

