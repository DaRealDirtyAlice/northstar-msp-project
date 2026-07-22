# Current Project Status

Last updated: **2026-07-21**

Overall status: **Phase 1 - In Progress**

## Completed and validated

- VMware Workstation 17.6.4 selected as the hypervisor.
- Isolated `VMnet3` lab network designed on `10.50.10.0/24`.
- VMware DHCP disabled for VMnet3 so DC01 is the intended DHCP authority.
- Windows Server 2022 Standard Evaluation with Desktop Experience installed.
- Server renamed to `DC01`.
- Static configuration applied: `10.50.10.10/24`, no Phase 1 default gateway, DNS set to `10.50.10.10`.
- AD DS, DNS, and DHCP roles installed.
- New Forest and root Domain created: `corp.northstar.test`.
- DC01 promoted to a Domain Controller.
- Domain identity, Forest, Domain, NTDS, DNS, KDC, and Netlogon checks reported successful.
- DNS host lookup and Domain Controller SRV lookup reported successful.
- DHCP authorized in Active Directory.
- Active DHCP scope configured for `10.50.10.100-10.50.10.199`.
- Scope options configured for internal DNS and the `corp.northstar.test` suffix; no Phase 1 router option.
- Custom Northstar OU hierarchy created and visually validated.
- Ten designed groups created and command-validated as Global Security groups.
- Separate named administrative account `ns-admin` created, added to Domain Admins, and validated with both filtered and elevated sign-in tokens.
- Pre-import user dataset, target OUs, security groups, name conflicts, and `New-ADUser -WhatIf` results validated; a powered-off VM snapshot was taken before the real import.
- Twenty fictional AD user objects created in the correct department OUs, repaired after a disabled-account password issue, and freshly validated as 20 enabled accounts with first-logon password change required.
- Sixteen employee-to-manager relationships assigned and freshly validated, leaving four department managers as the intended top-level users.
- Forty-seven security-group memberships applied across 10 groups and independently validated with zero missing or unexpected assignments.
- Windows 11 Pro client `WIN11-HR01` deployed on VMnet3 with 4 GB RAM, two vCPUs, a 64 GB disk, UEFI, Secure Boot, and virtual TPM.
- `WIN11-HR01` received DHCP lease `10.50.10.100/24`, DNS server `10.50.10.10`, and the `corp.northstar.test` suffix with no Phase 1 default gateway.
- DC01 host resolution and Domain Controller discovery validated from `WIN11-HR01` before Domain Join.
- `WIN11-HR01` joined directly into the Northstar Workstations OU and reported `PartOfDomain = True` with a healthy computer secure channel.
- Fictional HR user `CORP\\ewilson` completed the first Domain sign-in on `WIN11-HR01`; the session reported the expected UPN, `C:\\Users\\ewilson` profile, `\\DC01` logon server, and Northstar DNS domain.
- Emma Wilson's login token contained the intended HR Managers, HR Users, and Printer Users security groups.
- User Group Policy refreshed successfully and `gpresult` confirmed processing from `DC01.corp.northstar.test`; no user-side GPO settings are currently configured, so the applied-object result correctly reported `N/A`.
- DC01 validation confirmed `WIN11-HR01` is enabled, has the expected domain DNS hostname and recent logon timestamp, and resides in `OU=Workstations,OU=Computers,OU=Northstar`.
- Windows 11 Pro client `WIN11-SALES01` installed with distinct local recovery and computer identities.
- `WIN11-SALES01` received independent DHCP lease `10.50.10.101/24` with DHCP/DNS server `10.50.10.10`, suffix `corp.northstar.test`, no default gateway, and successful DC01 forward resolution.
- `WIN11-SALES01` joined `corp.northstar.test` and reported `PartOfDomain = True`.
- Fictional Sales user `CORP\\spatel` completed Domain sign-in with the expected UPN, profile, and `\\DC01` logon server.
- Sarah Patel's effective token contained only the intended `GG_Sales_Users` and `GG_Printer_Users` Northstar groups.
- Sales-user Group Policy refreshed successfully and RSOP confirmed processing from DC01; no user-side custom GPO settings are currently configured.
- DC01 validation confirmed `WIN11-SALES01` is enabled, uses `WIN11-SALES01.corp.northstar.test`, has a recent logon timestamp, and resides in `OU=Workstations,OU=Computers,OU=Northstar`.

## Completed with evidence still needed

- A clean final screenshot of VMnet3 after VMware DHCP was disabled.
- A sanitized Server Manager view showing DC01 and installed roles.
- A sanitized PowerShell validation view for Forest, Domain, and critical services.
- A DHCP console view showing the active scope and options 006/015.

User confirmation and command results support the current status. Reviewed public-ready screenshots for the accepted HR and Sales clients are stored under `portfolio-updates/screenshots/approved-github` and `portfolio-updates/screenshots/approved-linkedin`.

## Next milestone

Deploy and validate the remote-worker client:

```text
WIN11-REMOTE01 -> DHCP and DNS -> Domain Join -> Remote user sign-in
```

## Remaining Phase 1 work

- Add and validate `WIN11-REMOTE01`.
- Perform the formal least-privilege negative test.
- Complete all Phase 1 acceptance tests.

## Evidence rule

Only mark an item `Validated` when a repeatable test was performed. A screenshot is publication evidence, not a substitute for technical validation.
