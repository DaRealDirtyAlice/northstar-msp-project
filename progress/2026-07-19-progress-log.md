# Progress Log - 2026-07-19

## Completed and validated

- Deployed Windows 11 Pro workstation `WIN11-HR01` on the isolated VMnet3 network.
- Configured 4 GB RAM, two virtual processors, a 64 GB disk, UEFI, Secure Boot, and a virtual TPM.
- Completed Windows OOBE using a separate local recovery administrator.
- Renamed the Windows computer from its generated name to `WIN11-HR01`.
- Received DHCP lease `10.50.10.100/24` from DC01 with DNS server `10.50.10.10`, suffix `corp.northstar.test`, and no default gateway.
- Resolved `dc01.corp.northstar.test` and successfully discovered the Domain Controller before Domain Join.
- Joined `WIN11-HR01` to `corp.northstar.test` in the Northstar Workstations OU.
- Validated `PartOfDomain = True` and a healthy computer secure channel.
- Completed the first fictional HR-user domain sign-in as `CORP\\ewilson`.
- Confirmed UPN `ewilson@corp.northstar.test`, profile `C:\\Users\\ewilson`, logon server `\\DC01`, and DNS domain `CORP.NORTHSTAR.TEST`.
- Confirmed Emma Wilson's effective token includes `GG_HR_Managers`, `GG_HR_Users`, and `GG_Printer_Users`.
- Refreshed user Group Policy successfully and confirmed that policy processing used `DC01.corp.northstar.test`.
- Confirmed that no user-side GPO settings are currently configured; `Applied Group Policy Objects: N/A` is therefore the expected Phase 1 result.

## Troubleshooting lessons

- Corrected an initially attached Windows Server 2022 ISO before client installation.
- Used Windows 11 Pro because Home editions do not support Active Directory Domain Join.
- Distinguished expected no-internet behavior on the isolated network from internal network failure.
- Corrected an attempted PowerShell-only `Rename-Computer` command entered in CMD.
- Treated `Server: Unknown` in `nslookup` as a missing reverse-DNS label rather than a failed forward or SRV lookup.

## Current focus

- Validate the AD computer object location for `WIN11-HR01`.
- Begin deployment of `WIN11-SALES01`.
