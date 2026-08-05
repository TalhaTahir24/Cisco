# Services and monitoring

Reliable egress, traffic priority, and visibility: dual-ISP NAT with automatic failover, QoS for real-time traffic, NetFlow for flow analysis, and NTP/SNMPv3/Syslog for operations.

## Files

| File | What it demonstrates |
|------|----------------------|
| [nat-dual-isp.config](nat-dual-isp.config) | PAT on two uplinks with IP SLA + tracked default routes |
| [qos.config](qos.config) | Mark-at-edge, LLQ for voice/video, WRED for TCP |
| [netflow.config](netflow.config) | NetFlow v9 export + top-talkers for capacity planning |
| [ntp-snmp-syslog.config](ntp-snmp-syslog.config) | SNMPv3 (auth+priv), authenticated NTP, syslog to collector |
