# Project Execution Plan

## Core Principles

- Target effort allocation: 70% users and tickets, 20% infrastructure, and 10% security monitoring.
- Build the smallest usable environment before adding features.
- Begin every fault with a ticket instead of fixing an observed problem without documenting it.
- Every outcome must include an implementation record, validation result, and sanitized evidence.
- Use Wazuh only for endpoint visibility and escalation evidence; do not turn this project into a penetration-testing lab.

## Resource Tiers

### Minimum Starting Configuration

- `DC01`: 2 vCPU, 4 GB RAM, 60 GB disk
- `WIN11-HR01`: 2 vCPU, 4 GB RAM, 64 GB disk
- Use these two virtual machines to validate AD, DNS, DHCP, and domain join first.

### Full Phase 1 Acceptance Configuration

- Add `WIN11-SALES01` and `WIN11-REMOTE01`.
- If memory is limited, do not run all four VMs simultaneously. Join and validate each client individually.

### Later Phases

- `FS01`: 2 vCPU, 4 GB RAM, at least 80 GB disk
- `HELPDESK01`: Adjust resources for the selected ticketing platform
- `WAZUH01`: Reuse the existing environment where practical
- `FW01`: Add only after the foundational ticket workflow is mature

## Phases and Gates

### Phase 0: Preparation (Major Preparation Complete)

- [x] Create the portfolio directory.
- [x] Define the business scenario and naming conventions.
- [x] Design the IP plan, OUs, groups, and users.
- [x] Create evidence and ticket templates.
- [x] Confirm VMware Workstation and Windows Server 2022 installation media.
- [ ] Confirm available RAM and Windows 11 Enterprise installation media.
- [x] Select `10.50.10.0/24` for the virtual network.

### Phase 1: Identity and Foundational Networking

- [x] Create the isolated VMnet3 lab network.
- [x] Deploy and rename `DC01`.
- [x] Configure the static IP address `10.50.10.10/24`.
- [x] Install AD DS, DNS, and DHCP.
- [x] Create the `corp.northstar.test` Forest and Domain.
- [x] Validate AD, Kerberos, Netlogon, and DNS A/SRV records.
- [x] Authorize DHCP and activate the `10.50.10.100-10.50.10.199` address pool.
- [x] Create OUs and security groups.
- [x] Import 20 fictional users.
- [ ] Successfully join at least one Windows 11 client to the domain.
- [ ] Complete final acceptance testing on three Windows 11 clients.

Gate: DNS and DHCP operate correctly, three clients can sign in with domain accounts, and objects are located in the correct OUs.

### Phase 2: Files, GPOs, and Endpoints

- [ ] Deploy `FS01`.
- [ ] Create departmental and Public shares.
- [ ] Assign permissions through security groups instead of directly to individual users.
- [ ] Configure drive mapping and foundational GPOs.
- [ ] Complete the Windows 11 standardization baseline.
- [ ] Complete permissions, GPO, printer, and recovery tickets.

Gate: Cross-department access is blocked, authorized users have the correct read/write access, drives map automatically, and standard users have no local administrator rights.

### Phase 3: Service Desk

- [ ] Select and deploy osTicket, GLPI, or an equivalent platform.
- [ ] Configure categories, priorities, SLA targets, and the escalation matrix.
- [ ] Publish 10 knowledge base articles.
- [ ] Route every fault through a ticket.

Gate: Before closure, every ticket contains diagnosis, root cause, resolution, validation, preventive action, and user confirmation.

### Phase 4: Microsoft 365 and Remote Support

- [ ] Use a legally available test environment or clearly label the work as a process simulation.
- [ ] Complete one cloud-user onboarding and offboarding workflow.
- [ ] Complete at least five Microsoft 365 support tickets.
- [ ] Explain the differences among AD, Entra Registered, Entra Joined, and Hybrid Joined devices.

Gate: Independently explain the complete account, licensing, MFA, session-revocation, and remote-access support workflow.

### Phase 5: Blind Fault Injection

- [ ] Have another person or a randomized list introduce unknown root causes.
- [ ] Troubleshoot without viewing the answer.
- [ ] Complete 30 simulated support tickets.
- [ ] Select the five strongest representative cases.

Gate: Every ticket includes evidence, impact scope, and user confirmation, while high-risk events are escalated correctly.

### Phase 6: Automation and Portfolio Packaging

- [ ] `New-Employee.ps1`
- [ ] `Disable-Employee.ps1`
- [ ] `Endpoint-HealthCheck.ps1`
- [ ] Ticket metrics, architecture diagram, final report, and demonstration video
- [ ] Complete a final repository review for sensitive information

## Recommended Working Rhythm

Complete one testable objective per lab session: 45-90 minutes for implementation, 15 minutes for validation, and 20-30 minutes for ticket and evidence preparation. A configuration is not complete until its evidence has been organized.
