# Automation and Programmability

## SDN
- Decouples control plane from data plane.
- Controller-based (centralized): Cisco DNA Center, APIC-EM.
- Northbound APIs (to apps), southbound APIs (to devices: NETCONF, RESTCONF, OpenFlow).

## REST APIs
- HTTP-based; methods: GET (read), POST (create), PUT (replace), PATCH (modify), DELETE.
- Stateless, JSON/XML payloads, status codes (200 OK, 201 Created, 4xx client error, 5xx server error).
- Example: GET `https://api.example.com/v1/devices` returns a JSON list of devices.

## JSON
```json
{
  "hostname": "R1",
  "interfaces": [
    { "name": "GigabitEthernet0/0", "ip": "192.168.10.1/24" },
    { "name": "GigabitEthernet0/2", "ip": "172.168.10.1/24" }
  ]
}
```

## YAML
```yaml
hostname: R1
interfaces:
  - name: GigabitEthernet0/0
    ip: 192.168.10.1/24
  - name: GigabitEthernet0/2
    ip: 172.168.10.1/24
```
YAML = superset of JSON, indentation-sensitive, used by Ansible.

## Controllers / DNA Center
- DNA Center: intent-based networking, policy, assurance (telemetry), software image management.
- Controllers centralize config, visibility, and automation instead of CLI-per-device.

## Configuration management
- Tools: Ansible (agentless, push), Puppet/Chef (pull), SaltStack.
- Device-native: NETCONF (XML, standardized), RESTCONF (HTTP+JSON), gNMI (streaming telemetry).
- Model-driven telemetry pushes structured data instead of poll-based SNMP.

## Cloud networking basics
- Public/private/hybrid cloud, virtualization, VPCs, virtual routers/firewalls (FWaaS), load balancers.
- Connectivity: VPN, Direct Connect, overlay networks (VXLAN), SD-WAN.

## This repo's Ansible usage
See the [`ansible/`](../ansible/) directory - playbooks that push VLAN, interface, and routing config to the lab via `network_cli`, driven by the YAML inventory.
