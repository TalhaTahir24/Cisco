# Cisco Configuration Playbook

Production-grade IOS/IOS-XE configuration patterns from real network work: multi-area OSPF, dual-homed BGP, redundant gateways, site-to-site IPsec, zone-based firewalls, and monitoring. Each file is a self-contained reference with the config and the verify commands that prove it works.

## What's here

| Area | Files | What you'd use it for |
|------|-------|------------------------|
| [Routing](01-routing/) | Multi-area OSPF + summarization, redistribution, BGP multihoming, VRF-lite | Scaling routing past a flat single-area lab; isolating tenants/environments |
| [High availability](02-high-availability/) | VRRP/HSRP with uplink tracking, LACP EtherChannel, STP hardening | Redundant default gateways and loop-free, resilient switching |
| [Security](03-security/) | Site-to-site IPsec (IKEv2), zone-based firewall, AAA/TACACS+, CoPP | Edge VPNs, zone segmentation, device hardening |
| [Services & monitoring](04-services-monitoring/) | Dual-ISP NAT + IP SLA, QoS, NetFlow, NTP/SNMPv3/Syslog | Reliable egress, visibility, and audit trail |
| [Automation](05-automation/) | Ansible playbooks pushing routing/security config | Config-as-code instead of one-off CLI |

## Config philosophy

- **Route with filters, not defaults.** Redistribution is always gated by route-maps and tags; eBGP only ever advertises your own prefix and filters bogons inbound.
- **Redundancy that actually fails over.** VRRP/HSRP track the uplink, so the standby takes over when the primary WAN dies — not when the box crashes.
- **Security in layers.** CoPP protects the control plane, AAA centralizes access with a local fallback, and zone-based policies replace blanket ACLs.
- **Verify, don't assume.** Every file ends with the `show` commands that confirm the feature is working before you walk away.

## Design context

These patterns reflect work on real edge/network builds:

- **Dual ISP with VIP failover** — `vrrp-hsrp.config` + `nat-dual-isp.config` match the [external network design](https://github.com/TalhaTahir24/network-designs/blob/main/docs/external-network-lab.md): two upstreams, virtual gateway, active-passive firewall pair, DMZ/Internal/Management zoning.
- **Zone segmentation** — `zone-based-firewall.config` implements the same zone model (DMZ / INTERNAL / MGMT / WAN) used in production environments.
- **Site-to-site connectivity** — `ipsec-site-to-site.config` is the IKEv2/AES-GCM tunnel pattern used for branch and inter-site links.

## Ansible usage

```bash
cd 05-automation/ansible
cp hosts.example hosts   # fill in device IPs + credentials
ansible-playbook site1.yml
```

`hosts` is gitignored — never commit credentials. `hosts.example` holds placeholders only.

## Layout

```
Cisco/
  01-routing/              OSPF multi-area, redistribution, BGP, VRF-lite
  02-high-availability/    VRRP/HSRP, EtherChannel, STP hardening
  03-security/             IPsec, zone-based firewall, AAA, CoPP
  04-services-monitoring/  NAT, QoS, NetFlow, NTP/SNMP/Syslog
  05-automation/ansible/   playbooks + inventory
```
