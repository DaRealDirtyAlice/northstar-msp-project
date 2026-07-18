# IP Address Plan

| Item | Value |
|---|---|
| Proposed subnet | `10.50.10.0/24` |
| Phase 1 gateway | None (isolated host-only network) |
| Future FW01 gateway | `10.50.10.254` (only after FW01 is deployed) |
| DC01 / DNS | `10.50.10.10` |
| FS01 | `10.50.10.20` |
| HELPDESK01 | `10.50.10.30` |
| WAZUH01 | `10.50.10.40` |
| DHCP scope | `10.50.10.100–10.50.10.199` |
| Addresses reserved outside the dynamic pool | `10.50.10.1–10.50.10.99` and `10.50.10.200–10.50.10.254` |
| Initial DHCP exclusions | None; reserved addresses are already outside the scope range |
| DNS suffix | `corp.northstar.test` |
| Lease duration | 8 days initially |

Before implementation, record the host LAN and VPN subnets below and confirm no overlap.

| Network | Observed subnet | Conflict? | Checked date |
|---|---|---|---|
| Host LAN | `10.0.0.0/24` | No | 2026-07-15 |
| VMware VMnet1 | `192.168.233.0/24` | No | 2026-07-15 |
| VMware VMnet8 | `192.168.116.0/24` | No | 2026-07-15 |
| Existing VMware VMnet2 / HomeLab candidate | `10.10.10.0/24` | No | 2026-07-15 |
| Hyper-V Default Switch | `172.23.224.0/20` | No | 2026-07-15 |
| Active VPN | None observed during check | No observed conflict | 2026-07-15 |

Current check supports retaining `10.50.10.0/24`. Recheck this table whenever a VPN is active or the host network changes.
