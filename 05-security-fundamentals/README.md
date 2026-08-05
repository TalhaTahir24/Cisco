# Security Fundamentals

## AAA
- **Authentication** - who are you (username/password, RADIUS/TACACS+).
- **Authorization** - what you may do (privilege levels, commands).
- **Accounting** - what you did (logging of commands/access).
- RADIUS (UDP, encrypts only the password, 1812/1813) vs TACACS+ (TCP, encrypts whole body).

## ACLs
- **Standard** (1-99) - filter by source IP only; place closest to destination.
- **Extended** (100-199) - source + destination + protocol + port; place closest to source.
- **Named ACLs**; implicit deny-all at the end; evaluated top-down, first match wins.
- Also used to select traffic for NAT, route maps, QoS classification.

## VPN
- Site-to-site (IPsec between gateways), remote-access (client to gateway).
- IPsec: IKE for key exchange, ESP for encryption/authentication.
- GRE tunnels (unencrypted, often wrapped in IPsec).

## Firewalls / IDS / IPS
- Firewall = filters at the border (stateful = tracks connections).
- IDS = monitors, alerts on signatures; IPS = inline, blocks.

## Password / device hardening
- `service password-encryption`, `enable secret` (MD5) not `enable password` (plaintext).
- Login banner, timeout, exec-timeout, SSH not telnet, disable unneeded services.

## Wireless security
- WPA2 (CCMP/AES), WPA3 (SAE), WPA2/WPA3-Enterprise (802.1X + RADIUS).

## Configs
- [password-hardening.config](password-hardening.config)
- [acl.config](acl.config)
- [aaa.config](aaa.config)
