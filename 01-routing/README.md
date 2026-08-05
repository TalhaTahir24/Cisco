# Routing

Scaling routing beyond a flat lab: multi-area OSPF with summarization, controlled redistribution, dual-homed BGP with path control, and VRF-lite for tenant isolation.

## Files

| File | What it demonstrates |
|------|----------------------|
| [ospf-multi-area.config](ospf-multi-area.config) | Multi-area OSPF: ABR summarization, stub areas, passive-interface defaults, area authentication, tuned timers |
| [redistribution.config](redistribution.config) | Route redistribution between OSPF/EIGRP/BGP using route-maps + tags to prevent loops |
| [bgp-multihoming.config](bgp-multihoming.config) | Dual-homed eBGP: AS-path prepend, local-preference, prefix-list filters, bogons inbound |
| [vrf-lite.config](vrf-lite.config) | Multiple routing tables on one box for isolated tenants/environments |
