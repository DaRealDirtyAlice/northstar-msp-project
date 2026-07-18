# Northstar MSP Project To-Do Monitor

Last updated: **2026-07-18**

## Progress Snapshot

- Project phase: **Phase 1 - Identity and Foundational Networking**
- Current focus: **Build `WIN11-HR01` on VMnet3**
- Support Cases completed: **0 of 30**
- Support Cases remaining: **30**
- Current Case: **None - infrastructure build is still in progress**
- Next Case ID: **CASE-001**

Progress bar: `[------------------------------] 0%`

## Completion Rule

A Case is complete only after the issue has been reproduced, diagnosed, resolved, technically validated, confirmed by the user, documented in the Case folder, and reviewed for safe GitHub and LinkedIn evidence.

When a Case is complete, use this format:

`- [x] ~~CASE-001 - Example resolved issue~~`

## Phase 0 - Preparation

- [x] ~~Create the portfolio structure and business scenario.~~
- [x] ~~Define the IP plan, OU design, security groups, and fictional user dataset.~~
- [x] ~~Create evidence, ticket, Case, and knowledge-base templates.~~
- [x] ~~Select VMware Workstation and Windows Server 2022 installation media.~~
- [x] ~~Create the isolated `10.50.10.0/24` VMnet3 network.~~
- [ ] Confirm host RAM available for the complete lab.
- [ ] Obtain Windows 11 Enterprise installation media.

## Phase 1 - Identity and Foundational Networking

- [x] ~~Install Windows Server 2022 with Desktop Experience.~~
- [x] ~~Rename the server to `DC01`.~~
- [x] ~~Configure `10.50.10.10/24` with internal DNS and no Phase 1 gateway.~~
- [x] ~~Install AD DS, DNS, and DHCP.~~
- [x] ~~Create the `corp.northstar.test` Forest and Domain.~~
- [x] ~~Validate AD, Kerberos, Netlogon, DNS host records, and SRV records.~~
- [x] ~~Authorize DHCP and activate `10.50.10.100-10.50.10.199`.~~
- [x] ~~Create the designed OUs.~~
- [x] ~~Create the designed security groups.~~
- [x] ~~Create a separate administrative account.~~
- [x] ~~Import 20 fictional users.~~
- [ ] Build `WIN11-HR01` on VMnet3.
- [ ] Validate its DHCP lease, DNS server, and domain suffix.
- [ ] Join `WIN11-HR01` to the domain.
- [ ] Validate domain sign-in and Group Policy processing.
- [ ] Add and validate `WIN11-SALES01`.
- [ ] Add and validate `WIN11-REMOTE01`.
- [ ] Complete the Phase 1 acceptance record.

## Phase 2 - Files, GPOs, and Endpoints

- [ ] Deploy `FS01`.
- [ ] Create departmental and Public shares.
- [ ] Apply group-based NTFS and share permissions.
- [ ] Configure drive mapping and baseline GPOs.
- [ ] Complete the Windows 11 endpoint baseline.
- [ ] Validate authorized and unauthorized access paths.

## Phase 3 - Service Desk Platform

- [ ] Select and deploy the ticketing platform.
- [ ] Configure categories, priorities, SLA targets, and escalation paths.
- [ ] Publish 10 knowledge-base articles.
- [ ] Route all fault work through tickets.

## Phase 4 - Microsoft 365 and Remote Support

- [ ] Establish a valid test environment or clearly documented simulation.
- [ ] Complete one cloud onboarding workflow.
- [ ] Complete one cloud offboarding workflow.
- [ ] Complete at least five Microsoft 365 support scenarios.
- [ ] Document the AD and Entra device-state differences.

## Phase 5 - Thirty Support Cases

- [ ] CASE-001 - Not started
- [ ] CASE-002 - Not started
- [ ] CASE-003 - Not started
- [ ] CASE-004 - Not started
- [ ] CASE-005 - Not started
- [ ] CASE-006 - Not started
- [ ] CASE-007 - Not started
- [ ] CASE-008 - Not started
- [ ] CASE-009 - Not started
- [ ] CASE-010 - Not started
- [ ] CASE-011 - Not started
- [ ] CASE-012 - Not started
- [ ] CASE-013 - Not started
- [ ] CASE-014 - Not started
- [ ] CASE-015 - Not started
- [ ] CASE-016 - Not started
- [ ] CASE-017 - Not started
- [ ] CASE-018 - Not started
- [ ] CASE-019 - Not started
- [ ] CASE-020 - Not started
- [ ] CASE-021 - Not started
- [ ] CASE-022 - Not started
- [ ] CASE-023 - Not started
- [ ] CASE-024 - Not started
- [ ] CASE-025 - Not started
- [ ] CASE-026 - Not started
- [ ] CASE-027 - Not started
- [ ] CASE-028 - Not started
- [ ] CASE-029 - Not started
- [ ] CASE-030 - Not started

## Phase 6 - Automation and Portfolio Packaging

- [ ] Build and validate `New-Employee.ps1`.
- [ ] Build and validate `Disable-Employee.ps1`.
- [ ] Build and validate `Endpoint-HealthCheck.ps1`.
- [ ] Produce ticket metrics and the final architecture diagram.
- [ ] Select the five strongest representative Cases.
- [ ] Complete the final report and demonstration video.
- [ ] Complete the final privacy and secret review.

## Update Procedure

After every working session or Case:

1. Update the checkboxes, completed count, remaining count, current focus, and next Case ID.
2. Update `cases/case-register.csv` when a real Case is opened or closed.
3. Save every received screenshot to the local screenshot inbox.
4. Record separate GitHub and LinkedIn publication decisions in the screenshot decision register.
5. Create or update the date-prefixed Word document for that Case.
