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
12. Built and validated the custom Northstar OU hierarchy and 10 Global Security groups.
13. Created the named `ns-admin` administrative account and validated effective Domain Admins privileges through an elevated token.
14. Validated a 20-record fictional user dataset, including zero duplicate usernames, zero existing-account conflicts, and valid manager references.
15. Rehearsed the user import with `New-ADUser -WhatIf` before making directory changes.
16. Created 20 fictional AD users across HR, Finance, Sales, and Operations.
17. Diagnosed and repaired a disabled-account condition by applying a compliant temporary password, enabling all accounts, and preserving the first-logon password-change requirement.
18. Assigned and validated 16 employee-to-manager relationships, leaving four department managers as top-level users.
19. Applied 47 memberships across 10 Global Security groups and validated 47 expected versus 47 actual memberships with zero missing or unexpected assignments.
20. Exported a sanitized 20-row user-to-group validation report for repository evidence.

## Concepts learned

- A server role installs capability; it does not create the business configuration by itself.
- DNS and DHCP do not route all client traffic through DC01.
- A host-only virtual network can provide full internal AD functionality without Internet access.
- A Forest is the highest AD configuration and security boundary; it contains Domains, not child Forests.
- A Domain is the identity and authentication namespace.
- An OU is a container and a management scope for Group Policy and delegated administration.
- A security group controls resource access; OU placement alone does not grant file permissions.
- An AD client locates Domain Controllers through DNS SRV records rather than a manually entered DC address.
- A safe automation workflow uses source-data validation, collision checks, `-WhatIf`, controlled writes, and fresh post-change queries.
- A successful command message is not sufficient evidence; the final directory state must be queried independently.
- Manager attributes represent reporting relationships, while security groups carry access intent.
- Idempotent checks make a bulk script safe to rerun without creating duplicate accounts or memberships.

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

### Bulk-created accounts were disabled

- Symptom: all 20 user objects existed with correct profile fields, but `EnabledUsers` returned zero.
- Working cause: the password supplied during creation was unavailable or did not satisfy the domain password policy, so Active Directory retained the objects in a disabled state.
- Action: entered a compliant temporary password as a SecureString, reset each account password, enabled each account, and reapplied the first-logon password-change requirement.
- Result: fresh AD queries returned 20 total users, 20 enabled users, zero disabled users, and 20 users required to change their password at next sign-in.

## Current limitations

- No Windows 11 client has been deployed, so DHCP DORA and Domain Join are not yet proven end to end.
- No Windows 11 endpoint has joined the domain, so user sign-in and Group Policy processing are not yet proven from a client.
- Internet-dependent activation, updates and Microsoft 365 work remain deferred.

## Next session

Create `WIN11-HR01` on VMnet3 and observe whether it receives the intended DHCP address, DNS server and domain suffix before attempting Domain Join.
