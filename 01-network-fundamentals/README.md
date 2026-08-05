# Network Fundamentals

## Network types and topology
- **LAN** - single broadcast domain, typically one building/campus.
- **WAN** - interconnects sites over long distance (leased lines, MPLS, VPN over internet).
- **MAN** - metropolitan area, larger than a LAN, smaller than a WAN.
- **Internet** - global network of interconnected networks (network of networks).

Topologies: bus, star, ring, mesh, hub-and-spoke, point-to-point.

## Devices
- **Router** - forwards between networks, builds the routing table, connects LAN to WAN.
- **Switch** - forwards Ethernet frames within a LAN, learns MAC addresses (MAC table), breaks up collision domains.
- **Firewall** - filters traffic by policy between trust zones.
- **Access Point (AP)** - bridges wireless clients onto the wired network.

## OSI model (7 layers)
| Layer | Name | Function | PDU |
|-------|------|----------|-----|
| 7 | Application | user-facing services (HTTP, DNS, SMTP) | data |
| 6 | Presentation | encoding, encryption, compression | data |
| 5 | Session | establishes/manages sessions | data |
| 4 | Transport | end-to-end delivery, TCP/UDP, port numbers | segment |
| 3 | Network | logical addressing (IP), routing, fragmentation | packet |
| 2 | Data Link | physical addressing (MAC), framing, switching | frame |
| 1 | Physical | bits, signalling, cabling | bits |

Memory aid: **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing.

## TCP/IP model (4 layers)
| Layer | Equivalent OSI layers |
|-------|----------------------|
| Application | 5-7 |
| Transport | 4 |
| Internet | 3 |
| Network Access | 1-2 |

## IPv4 addressing
- 32-bit address, dotted-decimal, e.g. `192.168.10.1`.
- Two parts: **network** + **host** (split by subnet mask).
- Default classes:
  - A: `1.0.0.0` - `126.255.255.255` (/8)
  - B: `128.0.0.0` - `191.255.255.255` (/16)
  - C: `192.0.0.0` - `223.255.255.255` (/24)
  - D (multicast): `224.0.0.0/4`
  - E (reserved): `240.0.0.0/4`
- Special addresses:
  - Loopback: `127.0.0.0/8`
  - Private ranges: `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`
  - APIPA/link-local: `169.254.0.0/16`
  - Network address = all host bits 0, broadcast = all host bits 1.

## Subnetting
- Hosts per subnet = `2^(32 - prefix) - 2` (minus network + broadcast).
- Borrow bits from the host portion to create more subnets: `2^borrowed` subnets.
- Examples:
  - `/24` = 254 hosts
  - `/25` = 126 hosts (2 subnets from a /24)
  - `/26` = 62 hosts (4 subnets from a /24)
  - `/30` = 2 hosts (point-to-point links)

## Binary and decimal conversion
- Bits are powers of 2: 128 64 32 16 8 4 2 1.
- `11000000` = 192, `10101000` = 168, `00001010` = 10.

## IPv6 addressing
- 128-bit, 8 groups of 4 hex digits, e.g. `2001:db8::1`.
- `::` compresses consecutive zero groups (only once).
- Global unicast: `2000::/3`, link-local: `fe80::/10`, unique local (ULA): `fc00::/7`, multicast: `ff00::/8`.
- No broadcast; uses multicast (solicited-node) and anycast.
- SLAAC (Stateless Address Autoconfiguration) uses ICMPv6 RA/RS + EUI-64.
- Config (see `03-ip-connectivity` notes):
  ```
  interface GigabitEthernet0/0
   ipv6 enable
   ipv6 address 2001:db8:1::1/64
  ipv6 unicast-routing
  ```

## Ethernet and MAC
- MAC = 48-bit hardware address, first 24 bits are the OUI (vendor).
- Unicast/ multicast / broadcast destination MACs; `ff:ff:ff:ff:ff:ff` = broadcast.
- Ethernet frame: Preamble | Dest MAC | Src MAC | EtherType/Length | Payload | FCS.
- Switch floods unknown unicast frames out all ports in the VLAN, drops if learned, forwards based on MAC table.

## ARP
- ARP resolves IPv4 -> MAC on a local segment.
- ARP request = broadcast; ARP reply = unicast. Entries cached in the ARP table.
- `arp -a` / `show arp`.

## Cabling
- Copper: UTP/STP, straight-through (switch<->host), crossover (same device types; modern ports auto-MDIX).
- Fiber: single-mode (long distance, laser), multi-mode (short distance, LED).
- PoE delivers power over Ethernet for APs/IP cameras.
