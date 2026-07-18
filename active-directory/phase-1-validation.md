# Phase 1 Validation Record

Status: **In progress — server-side foundation validated; client-side tests pending**

| Test ID | Test | Expected | Actual | Evidence | Result |
|---|---|---|---|---|---|
| P1-01 | DC01 services | AD DS, DNS, DHCP and authentication services running | NTDS, DNS, KDC, Netlogon and DHCP validation reported successful | User-confirmed command validation; final screenshot pending | Pass |
| P1-02 | DNS forward lookup and DC discovery | DC01 A record and AD SRV records resolve correctly | Forward and SRV lookup validation reported successful | User-confirmed command validation; final screenshot pending | Pass |
| P1-03 | DHCP lease | Client receives lab-scope address | Not tested | — | Pending |
| P1-04 | Client DNS | Client uses DC01 | Not tested | — | Pending |
| P1-05 | HR domain join/login | Successful | Not tested | — | Pending |
| P1-06 | Sales domain join/login | Successful | Not tested | — | Pending |
| P1-07 | Remote domain join/login | Successful | Not tested | — | Pending |
| P1-08 | OU placement | All objects in designed OU | Not tested | — | Pending |
| P1-09 | Group membership | Department/VPN membership matches CSV | Not tested | — | Pending |
| P1-10 | Least privilege | Daily user lacks admin rights | Not tested | — | Pending |

## Defects discovered

Record every failure as a service-desk ticket once the ticket workflow is active. During initial bootstrap, record the issue here and later backfill it into the ticketing system.

| Defect ID | Symptom | Root cause | Fix | Retest | Ticket ID |
|---|---|---|---|---|---|

## Sign-off

- Implemented by: ZhiBo Chen
- Validation date: 2026-07-18 (server-side checkpoint)
- Phase status: In progress
- Notes: DC01, Forest/Domain, DNS and DHCP server configuration are validated. DHCP lease, client DNS, domain join, OU placement, group membership and least-privilege tests require Windows 11 endpoints.
