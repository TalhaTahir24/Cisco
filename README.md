# Cisco Network Lab

Network automation and IOS configuration practice on a real device lab.

## Contents

| Path | What's inside |
|------|----------------|
| `ansible/` | Ansible playbooks that push config to lab routers/switches (R1-R4, SW1-SW4) via `network_cli` |
| `configs/` | IOS configuration examples: routing protocols, switching, VLANs |

## Topology

```
        R1 --- R2
        |        |
        SW1      SW2
        |        |
        R3 --- R4   (site-to-site)
```

VLANs 10 / 20 / 30 are used for the switching labs. See each config for the addressing used.

## Ansible usage

```bash
ansible-playbook -i hosts ansible/site1.yml
```

Copy `ansible/hosts.example` to `ansible/hosts` and fill in your device IPs and credentials.
Never commit the real `hosts` file — it is gitignored.

## Config reference

- Routing: [static-routing](configs/static-routing.txt), [RIP](configs/rip.txt), [OSPF](configs/ospf.txt), [BGP](configs/bgp.txt)
- Switching: [VLANs](configs/vlan.txt), [trunking](configs/trunking.txt), [VTP](configs/vtp.txt)
