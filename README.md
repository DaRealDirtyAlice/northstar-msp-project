# Northstar MSP IT Support Lab

A hands-on portfolio project designed for Junior IT Support, Service Desk, and MSP roles. The lab simulates Northstar Managed IT Services providing identity, endpoint, file, Microsoft 365, remote support, ticketing, and foundational security services to MapleWorks Professional Services, a 20-user client.

## Current Status

**Phase 1 is in progress. DC01, the Forest and Domain, internal DNS, DHCP, the custom OU hierarchy, 10 Global Security groups, the separate named administrative account, and 20 fictional users have been completed and validated. Windows 11 clients are still pending. Last updated: 2026-07-18.**

This repository clearly separates planned work from verified results:

- `[Planned]`: Not yet implemented
- `[Built]`: Configured but not fully accepted
- `[Validated]`: Retested against acceptance steps with evidence retained
- `[Troubleshot]`: Reproduced, diagnosed, resolved, and user-confirmed through a ticket

Planned work is never presented as a resume achievement before it has been validated.

## Business Scenario

- MSP: Northstar Managed IT Services
- Client: MapleWorks Professional Services
- Users: 20 across HR, Finance, Sales, and Operations
- Work model: One office and three remote employees
- Core services: Windows Server AD DS, DNS, DHCP, file sharing, Windows 11, Microsoft 365, VPN, ticketing, and endpoint security
- Lab domain: `corp.northstar.test`

## Implementation Order

1. AD, DNS, DHCP, OUs, users, groups, and Windows 11 domain join
2. FS01, departmental shares, NTFS permissions, GPOs, and endpoint standardization
3. Ticketing system, SLA, escalation matrix, and knowledge base
4. Microsoft 365, Entra ID, MFA, Outlook, Teams, OneDrive, and remote work support
5. Random fault injection and 30 complete support tickets
6. PowerShell automation, metrics, final report, and demonstration

See [PROJECT-PLAN.md](PROJECT-PLAN.md) for the complete roadmap. The current implementation guide is [phase-1-runbook.md](active-directory/phase-1-runbook.md).

See [progress/CURRENT-STATUS.md](progress/CURRENT-STATUS.md) for the current state, [progress/2026-07-18-progress-log.md](progress/2026-07-18-progress-log.md) for the full dated record, and [progress/2026-07-18-identity-provisioning-milestone.md](progress/2026-07-18-identity-provisioning-milestone.md) for the validated 20-user identity milestone.

Use [PROJECT-TODO.md](PROJECT-TODO.md) as the primary progress monitor. It shows completed work with checked and struck-through items, the current focus, and all 30 planned support cases.

## Repository Structure

- `architecture/`: Logical architecture, IP plan, and asset inventory
- `active-directory/`: OU, group, GPO, and Phase 1 implementation records
- `data/`: Fictional user data
- `service-desk/`: SLA, ticket templates, escalation workflow, and sample tickets
- `knowledge-base/`: Knowledge base templates and completed articles
- `powershell/`: Validated automation scripts
- `incidents/`: Security events requiring escalation
- `evidence/`: Sanitized screenshots, command output, and acceptance evidence organized by phase
- `final-report/`: Final report source files and exported deliverables
- `progress/`: Current status and dated implementation logs
- `cases/`: Records, screenshot selections, and LinkedIn material for each troubleshooting case
- `portfolio-updates/`: Local screenshot intake, publication decisions, and date-ordered Word documents for GitHub and LinkedIn updates

## Security and Privacy

Do not commit real passwords, recovery keys, tokens, API keys, personal information, unsanitized screenshots, or real corporate configurations. All simulated users are fictional. Temporary passwords must never be stored in CSV files, tickets, or screenshots.
