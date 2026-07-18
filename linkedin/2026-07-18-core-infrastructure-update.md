# LinkedIn Update — Core Infrastructure Milestone

Date drafted: **2026-07-18**  
Publication status: **Draft — screenshot set incomplete**

## Recommended screenshot order

1. Final VMnet3 isolated-network configuration
2. Server Manager showing DC01 and installed roles
3. Sanitized AD/DNS validation output
4. Active DHCP scope and options

Do not publish until each image is marked `Selected — public` in `evidence/screenshot-register.md`.

## Post copy

I’ve started building a hands-on MSP IT Support and Service Desk lab for a simulated 20-user professional services company.

The first server-side milestone is now complete:

- Built an isolated VMware host-only network
- Deployed Windows Server 2022 as DC01
- Configured static addressing and internal DNS
- Installed Active Directory Domain Services, DNS and DHCP
- Created and validated the `corp.northstar.test` Forest and Domain
- Promoted DC01 to the first Domain Controller
- Verified AD, Kerberos, Netlogon and DNS service-discovery records
- Authorized DHCP in Active Directory and configured an active client scope

An important lesson from this phase was separating the responsibilities of each service: DHCP provides network configuration, DNS enables name and service discovery, Active Directory manages identity and authentication, and none of these automatically makes the server a router.

The next milestone is deploying `WIN11-HR01` and validating the complete client workflow:

`DHCP lease -> DNS discovery -> Domain Join -> Domain account sign-in -> Group Policy`

This project is ongoing. I am recording implementation decisions, validation evidence, troubleshooting cases and user-facing documentation as I build it.

#ITSupport #HelpDesk #ActiveDirectory #WindowsServer #DNS #DHCP #VMware #ServiceDesk #HomeLab #LearningInPublic

