# Network Access

Theory for switching, then per-topic IOS configs.

## VLANs
- Logically segment a switch into separate broadcast domains (layer 2).
- VLAN 1 is the default; 1002-1005 are reserved.
- **Trunking (802.1Q)** tags frames between switches so VLANs span multiple switches.
- **Inter-VLAN routing** = a router or L3 switch routes between VLANs using SVIs.
- **DTP** (Dynamic Trunking Protocol) negotiates trunking: modes `dynamic auto`, `dynamic desirable`, `trunk`, `access` (default is `dynamic auto` on most platforms).
- **VTP** propagates VLAN database across trunks: server/client/transparent. VTP pruning limits flooded traffic to switches that need it.

## STP / RSTP
- **STP (802.1D)** prevents loops: one root bridge, blocked ports form a loop-free tree.
- Root election by lowest bridge ID (priority + MAC). Port roles: root, designated, alternate/blocked.
- Path cost depends on bandwidth (100Mbps=19, 1Gbps=4, 10Gbps=2).
- **RSTP (802.1w)** = fast convergence, replaces blocking with discarding, adds edge ports.
- Per-VLAN: PVST/PVST+ (Cisco), RPVST+.

## EtherChannel
- Bundles 2-8 physical links into one logical link (load balancing, redundancy, no STP blocking).
- Protocols: **PAgP** (Cisco proprietary, modes desirable/auto) and **LACP (802.3ad)**, modes active/passive.
- Link parameters must match (speed, duplex, VLAN/trunk config).

## Port security
- Restricts which MACs may connect to a port.
- Modes: `protect` (drops), `restrict` (drops + SNMP trap), `shutdown` (err-disables the port).

## Wireless
- SSID identifies the WLAN; clients associate via the AP.
- Security: **WPA2** (CCMP/AES), **WPA3** (SAE, protects against offline dictionary attacks), WPA2-Enterprise (802.1X/RADIUS).
- Client association process: probe request -> probe response -> authentication -> association.

## Configs
- [vlan.config](vlan.config)
- [trunking.config](trunking.config)
- [inter-vlan-routing.config](inter-vlan-routing.config)
- [etherchannel.config](etherchannel.config)
- [port-security.config](port-security.config)
