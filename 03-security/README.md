# Security

Edge and device security: encrypted site-to-site tunnels, zone-based policy enforcement, centralized AAA, and control-plane protection.

## Files

| File | What it demonstrates |
|------|----------------------|
| [ipsec-site-to-site.config](ipsec-site-to-site.config) | IKEv2 + AES-GCM site-to-site VPN with dead peer detection |
| [zone-based-firewall.config](zone-based-firewall.config) | Stateful zone-pair policies matching the DMZ/INTERNAL/MGMT/WAN zoning model |
| [aaa-tacacs.config](aaa-tacacs.config) | AAA with TACACS+/RADIUS, command authorization, accounting, local fallback |
| [control-plane-policing.config](control-plane-policing.config) | CoPP: rate-limit control-plane traffic so protocol sessions survive DDoS |
