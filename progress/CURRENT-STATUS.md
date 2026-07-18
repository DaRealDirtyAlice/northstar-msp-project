# Current Project Status

Last updated: **2026-07-18**

Overall status: **Phase 1 — In Progress**

## Completed and validated

- VMware Workstation 17.6.4 selected as the hypervisor.
- Isolated `VMnet3` lab network designed on `10.50.10.0/24`.
- VMware DHCP disabled for VMnet3 so DC01 is the intended DHCP authority.
- Windows Server 2022 Standard Evaluation with Desktop Experience installed.
- Server renamed to `DC01`.
- Static configuration applied: `10.50.10.10/24`, no Phase 1 default gateway, DNS set to `10.50.10.10`.
- AD DS, DNS and DHCP roles installed.
- New Forest and root Domain created: `corp.northstar.test`.
- DC01 promoted to a Domain Controller.
- Domain identity, Forest, Domain, NTDS, DNS, KDC and Netlogon checks reported successful.
- DNS host lookup and Domain Controller SRV lookup reported successful.
- DHCP authorized in Active Directory.
- Active DHCP scope configured for `10.50.10.100–10.50.10.199`.
- Scope options configured for internal DNS and the `corp.northstar.test` suffix; no Phase 1 router option.

## Completed with evidence still needed

- A clean final screenshot of VMnet3 after VMware DHCP was disabled.
- A sanitized Server Manager view showing DC01 and installed roles.
- A sanitized PowerShell validation view for Forest, Domain and critical services.
- A DHCP console view showing the active scope and options 006/015.

User confirmation and command results support the current status. Public-ready screenshots have not yet been stored in this repository.

## Next milestone

Deploy `WIN11-HR01` using Windows 11 Enterprise Evaluation and validate the complete service chain:

```text
DHCP lease -> internal DNS -> Domain Controller discovery -> Domain Join -> Domain sign-in
```

## Remaining Phase 1 work

- Obtain the Windows 11 Enterprise ISO.
- Create `WIN11-HR01` on VMnet3.
- Validate DHCP lease, DNS server and AD SRV discovery from the client.
- Join `WIN11-HR01` to `corp.northstar.test`.
- Create the designed OU and security-group structure.
- Import the 20 fictional users.
- Add `WIN11-SALES01` and `WIN11-REMOTE01`.
- Complete all Phase 1 acceptance tests.

## Evidence rule

Only mark an item `Validated` when a repeatable test was performed. A screenshot is publication evidence, not a substitute for technical validation.

