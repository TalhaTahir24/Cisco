# IP Connectivity

Theory for routing, then per-protocol IOS configs.

## Routing fundamentals
- Routers use the **routing table** to forward packets toward a destination network.
- Connected routes (directly attached), static routes, dynamic routes (RIP/OSPF/BGP).
- **Route selection:**
  1. **Longest prefix match** - the most specific route wins.
  2. **Administrative distance (AD)** - lower is preferred:
     - Connected = 0, Static = 1, eBGP = 20, OSPF = 110, RIP = 120, iBGP = 200.
  3. If AD ties, **metric** decides (RIP = hop count, OSPF = cost).
- **Static routing**: manually configured; a floating static route (higher AD) acts as a backup.
- **Default route** `0.0.0.0/0` catches everything not matched elsewhere.

## RIP
- Distance-vector, hop-count metric, max 15 hops.
- v2 sends multicasts (`224.0.0.9`), supports VLSM, authentication, no auto-summary.
- Slow convergence; fine for small labs.

## OSPF
- Link-state, SPF (Dijkstra) algorithm, cost metric (10^8 / bandwidth).
- Single-area (`area 0`) is the CCNA scope; neighbor adjacency via hello packets.
- Deterministic **router-id** (highest loopback, else highest active interface IP).
- **passive-interface** stops OSPF hellos on access links.
- Neighbor states: down -> init -> 2-Way -> Exstart -> Exchange -> Loading -> Full.

## First-hop redundancy (FHRP)
- **HSRP** (Cisco, active/standby, virtual IP), **VRRP** (open standard, master/backup), **GLBP** (Cisco, load-balancing).
- End hosts point at the virtual IP; one router is elected to forward.

## Configs
- [static-routing.config](static-routing.config)
- [rip.config](rip.config)
- [ospf-single-area.config](ospf-single-area.config)
- [first-hop-redundancy.config](first-hop-redundancy.config)
- [bgp.config](bgp.config) - reference (beyond CCNA syllabus)
