# Progress Log - 2026-07-20

## Completed and validated

- Queried the `WIN11-HR01` computer object directly from Active Directory.
- Confirmed the computer account is enabled.
- Confirmed DNS hostname `WIN11-HR01.corp.northstar.test`.
- Confirmed a recent domain logon timestamp.
- Confirmed the object resides in `OU=Workstations,OU=Computers,OU=Northstar`.
- Completed the first-client Phase 1 acceptance checks for DHCP, DNS, Domain Controller discovery, Domain Join, secure channel, domain-user sign-in, security-group token, and Group Policy processing.

## Current focus

- Installed Windows 11 Pro on `WIN11-SALES01` and corrected the local-account/computer-name separation.
- Validated independent lease `10.50.10.101/24`, DC01 DHCP/DNS, the Northstar suffix, no gateway, and DC01 forward resolution.
- Complete Domain Controller discovery, snapshot, Domain Join, and fictional Sales-user validation.
- Joined `WIN11-SALES01` to `corp.northstar.test` and confirmed domain membership from the client.
- Completed first domain sign-in as `CORP\\spatel` with the expected UPN, profile, and DC01 logon server.
- Validated the effective Sales Users and Printer Users groups with no unintended Northstar role groups.
- Refreshed user policy successfully and confirmed RSOP processing from DC01.
- Queried the `WIN11-SALES01` computer object directly from DC01 and confirmed the expected DNS hostname, enabled state, recent logon timestamp, and Workstations OU placement.
- Completed all second-client acceptance checks for DHCP, DNS, Domain Join, Sales-user sign-in, group-token validation, Group Policy processing, and server-side AD object validation.

## Next milestone

- Build and validate `WIN11-REMOTE01` as the third Phase 1 workstation.
