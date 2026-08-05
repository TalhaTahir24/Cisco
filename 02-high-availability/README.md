# High availability

Redundant default gateways and resilient switching. The common thread: failure is detected and acted on, not just survived.

## Files

| File | What it demonstrates |
|------|----------------------|
| [vrrp-hsrp.config](vrrp-hsrp.config) | VRRP (and HSRP) virtual gateway with interface tracking + preempt |
| [etherchannel.config](etherchannel.config) | LACP bundle for bandwidth and link redundancy |
| [stp-hardening.config](stp-hardening.config) | Root guard, BPDU guard, UDLD, storm control — edge protection against loops |
