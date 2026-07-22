# Phase 1 Validation Record

Status: **In progress - two of three client acceptance paths validated**

| Test ID | Test | Expected | Actual | Evidence | Result |
|---|---|---|---|---|---|
| P1-01 | DC01 services | AD DS, DNS, DHCP, and authentication services running | NTDS, DNS, KDC, Netlogon, and DHCP checks reported successfully | Server-side validation record | Pass |
| P1-02 | DNS forward lookup and DC discovery | DC01 A record and AD SRV records resolve correctly | Forward lookup and Domain Controller discovery succeeded from both accepted clients | Client PowerShell evidence | Pass |
| P1-03 | DHCP lease | Each client receives a unique lab-scope address | `WIN11-HR01` received `10.50.10.100/24`; `WIN11-SALES01` received `10.50.10.101/24`; remote client pending | Sanitized network-validation screenshots | In progress (2/3) |
| P1-04 | Client DNS | Each client uses DC01 for DNS and receives the domain suffix | Both accepted clients used `10.50.10.10` and `corp.northstar.test`; no Phase 1 gateway was assigned | Sanitized network-validation screenshots | In progress (2/3) |
| P1-05 | HR Domain Join and login | Successful | `WIN11-HR01` joined the Domain, reported a healthy secure channel, and accepted `CORP\\ewilson` | Domain Join, sign-in, group, and RSOP screenshots | Pass |
| P1-06 | Sales Domain Join and login | Successful | `WIN11-SALES01` joined the Domain and accepted `CORP\\spatel` with the expected DC01 logon server | Sign-in, group, RSOP, and AD-object screenshots | Pass |
| P1-07 | Remote Domain Join and login | Successful | Not tested | None | Pending |
| P1-08 | OU placement | All computer objects reside in the designed OU | HR and Sales computer objects are enabled in `OU=Workstations,OU=Computers,OU=Northstar`; remote laptop pending | DC01 `Get-ADComputer` validation | In progress (2/3) |
| P1-09 | Group membership | Department and VPN membership matches the approved dataset | HR and Sales user tokens matched their approved department and printer groups; remote VPN membership pending | `whoami /groups` and RSOP evidence | In progress |
| P1-10 | Least privilege | Daily user lacks administrative privileges | Formal negative test not yet performed | None | Pending |

## Defects discovered

| Defect ID | Symptom | Root cause | Fix | Retest | Ticket ID |
|---|---|---|---|---|---|
| P1-D01 | The first client booted into Windows Server Setup | The Server 2022 ISO was attached to the client VM | Powered off the VM and attached the correct Windows 11 media | Windows 11 Pro installed successfully | Bootstrap record; ticket backfill pending |
| P1-D02 | The intended Sales workstation name appeared as the local username | The hostname was entered in the OOBE account-name field | Created a distinct `LocalAdmin` recovery account, corrected the hostname, and verified both identities | `whoami` returned `win11-sales01\\localadmin` before Domain Join | Bootstrap record; ticket backfill pending |

## Sign-off

- Implemented by: ZhiBo Chen
- Validation date: 2026-07-20 (two-client checkpoint)
- Phase status: In progress
- Notes: DC01 and two department workstations are validated. `WIN11-REMOTE01`, VPN-group validation, the formal least-privilege test, and the final Phase 1 acceptance record remain open.
