# Progress Log — 2026-07-18

## Session outcome

The Northstar MSP lab moved from project preparation into an operational Phase 1 server foundation. DC01 now provides the planned Active Directory, internal DNS and DHCP server-side services for the isolated lab.

## Work completed

1. Confirmed the distinction between internal network connectivity and Internet access.
2. Confirmed that AD DS, DNS and DHCP can be installed and configured on an isolated host-only network.
3. Installed the AD DS, DNS and DHCP server roles.
4. Created the `corp.northstar.test` Forest and root Domain.
5. Promoted DC01 to the first Domain Controller.
6. Logged on using the CORP domain identity context.
7. Validated the Forest, Domain and core authentication services.
8. Validated DNS host resolution and Domain Controller SRV discovery.
9. Authorized DHCP in Active Directory.
10. Created and activated the `Northstar-Employees` IPv4 scope.
11. Configured internal DNS and domain-suffix DHCP options without a default gateway.

## Concepts learned

- A server role installs capability; it does not create the business configuration by itself.
- DNS and DHCP do not route all client traffic through DC01.
- A host-only virtual network can provide full internal AD functionality without Internet access.
- A Forest is the highest AD configuration and security boundary; it contains Domains, not child Forests.
- A Domain is the identity and authentication namespace.
- An OU is a container and a management scope for Group Policy and delegated administration.
- A security group controls resource access; OU placement alone does not grant file permissions.
- An AD client locates Domain Controllers through DNS SRV records rather than a manually entered DC address.

## Troubleshooting lessons

### VMware Easy Install license-terms failure

- Symptom: Windows setup could not find the Microsoft Software License Terms.
- Working cause: VMware Easy Install answer media conflicted with the evaluation installation workflow.
- Action: disabled the unattended path and booted the Microsoft ISO manually.
- Result: manual installation proceeded.

### Incorrect Server Core installation

- Symptom: the installed server opened SConfig instead of the graphical desktop.
- Cause: the non-Desktop Experience image was installed.
- Action: performed a clean installation using Windows Server 2022 Standard Evaluation with Desktop Experience.
- Result: GUI server installation completed successfully.

These are bootstrap lessons, not yet counted among the planned 30 end-user service-desk cases.

## Current limitations

- No Windows 11 client has been deployed, so DHCP DORA and Domain Join are not yet proven end to end.
- OU, group and user designs exist in documentation but have not yet been implemented.
- Internet-dependent activation, updates and Microsoft 365 work remain deferred.

## Next session

Create `WIN11-HR01` on VMnet3 and observe whether it receives the intended DHCP address, DNS server and domain suffix before attempting Domain Join.

