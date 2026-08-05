# IP Services

## DHCP
- Assigns IP, mask, default gateway, DNS to clients dynamically (DORA: Discover, Offer, Request, Ack).
- Pool, excluded addresses, lease. Static binding by MAC for servers.

## DNS
- Resolves hostnames to IPs. The router can act as a forwarder or host a static DNS table.

## NAT / PAT
- **Static NAT** - one-to-one inside->outside mapping.
- **Dynamic NAT** - pool of inside global addresses.
- **PAT** (NAT overload) - many inside hosts share one outside IP using port numbers (source port translation).
- Inside local/global, outside local/global terminology.

## NTP
- Clock synchronization for logs and authentication (Kerberos). Stratum = distance from the reference clock.

## SNMP
- Monitoring: agent (device) + manager (NMS). v2c uses community strings, v3 uses authentication/encryption.
- Traps/informs push notifications; polling pulls OIDs.

## Syslog
- Log messages to a server, severity levels 0-7 (emergency..debug). `logging trap`, `logging buffered`.

## QoS
- Marking (CoS/DSCP), queuing, policing vs shaping, trust boundaries.

## SSH / TFTP / FTP / HTTP
- SSH = encrypted remote management (port 22); TFTP = trivial file transfer (UDP 69) for IOS images/configs; FTP = file transfer (TCP 21); HTTP vs HTTPS for management/redirect.

## Configs
- [dhcp-dns.config](dhcp-dns.config)
- [nat-pat.config](nat-pat.config)
- [ntp-snmp-syslog.config](ntp-snmp-syslog.config)
- [ssh.config](ssh.config)
