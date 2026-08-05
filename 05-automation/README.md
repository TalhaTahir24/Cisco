# Automation

Config as code with Ansible: playbooks push routing, high-availability, and security config to the fleet instead of one-off CLI sessions.

## Playbooks

| File | What it pushes |
|------|----------------|
| [site1.yml](ansible/site1.yml) | OSPF multi-area, VRRP + tracking, IP SLA, CoPP; then collects neighbor/VRRP state |
| [site2.yml](ansible/site2.yml) | BGP multihoming + IKEv2 IPsec profile on branch routers |
| [site3.yml](ansible/site3.yml) | Security hardening: AAA/TACACS+, SSH-only management lines, insecure services off |

## Usage

```bash
cd ansible
cp hosts.example hosts   # fill in device IPs + credentials
ansible-playbook site1.yml
```

`hosts` is gitignored and never committed; `hosts.example` contains placeholders only.

## Inventory groups

`edge_routers`, `core_routers`, `branch_routers`, `switches`, and an `all` group `network_devices` — the playbooks target groups so a change rolls out where it belongs.
