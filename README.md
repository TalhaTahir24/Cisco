# CCNA 200-301 Lab

Hands-on network labs and IOS configuration practice mapped to the CCNA 200-301 syllabus. Built on a physical lab (routers R1-R4, switches SW1-SW4) with Ansible for push-config.

## Syllabus map

| Domain | Weight | Directory |
|--------|--------|-----------|
| 1. Network Fundamentals | 20% | [`01-network-fundamentals/`](01-network-fundamentals/) |
| 2. Network Access | 20% | [`02-network-access/`](02-network-access/) |
| 3. IP Connectivity | 25% | [`03-ip-connectivity/`](03-ip-connectivity/) |
| 4. IP Services | 10% | [`04-ip-services/`](04-ip-services/) |
| 5. Security Fundamentals | 15% | [`05-security-fundamentals/`](05-security-fundamentals/) |
| 6. Automation and Programmability | 10% | [`06-automation-programmability/`](06-automation-programmability/) |
| Ansible push-config | — | [`ansible/`](ansible/) |

## Topics covered

### 1. Network Fundamentals
LAN/WAN/MAN, network devices (router, switch, firewall, access point), OSI 7-layer and TCP/IP models, IPv4 addressing, IPv6 addressing, subnetting, binary/hex conversion, Ethernet, MAC addresses, ARP, cabling (copper/fiber), network topologies.

### 2. Network Access
VLANs, trunking (802.1Q), inter-VLAN routing, DTP, VTP, STP/RSTP, EtherChannel (LACP/PAgP), port security, switch hardening, wireless LAN and wireless security basics.

### 3. IP Connectivity
Routing fundamentals, static routing, default routing, dynamic routing, RIP, OSPF single-area, route selection (administrative distance, longest prefix match), routing table, first-hop redundancy.

### 4. IP Services
DHCP, DNS, NAT/PAT, NTP, SNMP, Syslog, QoS basics, SSH, TFTP/FTP, HTTP vs HTTPS.

### 5. Security Fundamentals
AAA, authentication/authorization/accounting, ACLs (standard and extended), VPN concepts, firewalls, IDS/IPS, password security, WPA2/WPA3, device hardening.

### 6. Automation and Programmability
SDN, REST APIs, JSON, YAML, Cisco DNA Center, controllers, configuration management, automation concepts, cloud networking basics.

## Config reference

| Topic | File |
|-------|------|
| VLANs | [`02-network-access/vlan.config`](02-network-access/vlan.config) |
| Trunking (802.1Q) | [`02-network-access/trunking.config`](02-network-access/trunking.config) |
| Inter-VLAN routing | [`02-network-access/inter-vlan-routing.config`](02-network-access/inter-vlan-routing.config) |
| EtherChannel (LACP/PAgP) | [`02-network-access/etherchannel.config`](02-network-access/etherchannel.config) |
| Port security | [`02-network-access/port-security.config`](02-network-access/port-security.config) |
| Static routing | [`03-ip-connectivity/static-routing.config`](03-ip-connectivity/static-routing.config) |
| RIP v2 | [`03-ip-connectivity/rip.config`](03-ip-connectivity/rip.config) |
| OSPF single-area | [`03-ip-connectivity/ospf-single-area.config`](03-ip-connectivity/ospf-single-area.config) |
| BGP (reference) | [`03-ip-connectivity/bgp.config`](03-ip-connectivity/bgp.config) |
| DHCP + DNS | [`04-ip-services/dhcp-dns.config`](04-ip-services/dhcp-dns.config) |
| NAT/PAT | [`04-ip-services/nat-pat.config`](04-ip-services/nat-pat.config) |
| NTP/SNMP/Syslog | [`04-ip-services/ntp-snmp-syslog.config`](04-ip-services/ntp-snmp-syslog.config) |
| SSH | [`04-ip-services/ssh.config`](04-ip-services/ssh.config) |
| ACLs | [`05-security-fundamentals/acl.config`](05-security-fundamentals/acl.config) |
| AAA | [`05-security-fundamentals/aaa.config`](05-security-fundamentals/aaa.config) |
| Device hardening | [`05-security-fundamentals/password-hardening.config`](05-security-fundamentals/password-hardening.config) |

## Ansible usage

```bash
ansible-playbook -i hosts ansible/site1.yml
```

Copy `ansible/hosts.example` to `ansible/hosts` and fill in your device IPs and credentials.
Never commit the real `hosts` file — it is gitignored.
