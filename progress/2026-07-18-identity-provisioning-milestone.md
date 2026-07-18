# Identity Provisioning Milestone - 2026-07-18

## Outcome

The Northstar MSP lab now has a validated 20-user Active Directory identity environment for the fictional MapleWorks Professional Services client.

## Completed work

- Created 20 fictional users from `data/users.csv` using a documented first-initial-plus-last-name convention.
- Placed users in the HR, Finance, Sales, and Operations OUs with a validated 4/4/6/6 distribution.
- Populated Employee ID, department, title, UPN, enabled state, and first-logon password-change settings.
- Assigned 16 employee-to-manager relationships and retained four department managers as top-level users.
- Applied 47 memberships across 10 Global Security groups.
- Limited VPN membership to the three approved remote workers.
- Added all 20 users to the shared-printer eligibility group.
- Exported a sanitized 20-row user-to-group validation report.

## Change-safety controls

The provisioning workflow used:

1. CSV row-count and department-distribution checks.
2. Manager-reference validation.
3. Generated-username duplicate detection.
4. Existing-account collision checks.
5. Target OU and group existence checks.
6. A `New-ADUser -WhatIf` dry run.
7. A powered-off pre-change VM snapshot.
8. Idempotent account and group-membership checks.
9. Fresh post-change AD queries rather than relying only on script success messages.

## Troubleshooting result

The initial user objects were present but disabled. The issue was isolated to the password and enablement stage rather than OU placement or profile attributes. A compliant temporary password was supplied through a SecureString, all 20 accounts were enabled, and the first-logon password-change requirement was reapplied.

Final account validation:

- Total users: 20
- Enabled users: 20
- Disabled users: 0
- Must change password at next sign-in: 20

## Authorization validation

Final group validation returned:

- Expected memberships: 47
- Actual memberships: 47
- Missing memberships: 0
- Unexpected memberships: 0

The groups currently express access intent. Resource permissions will be connected through an AGDLP-style model during the file-services phase.

## Evidence

- `../evidence/phase-1/2026-07-18_Northstar-User-Group-Validation.csv`
- `../portfolio-updates/screenshots/approved-github/2026-07-18_PHASE-1-20-users-enabled-final-validation.png`
- `../portfolio-updates/screenshots/approved-github/2026-07-18_PHASE-1-manager-relationships-validated.png`
- `../portfolio-updates/screenshots/approved-github/2026-07-18_PHASE-1-group-memberships-per-group-validated.png`
- `../portfolio-updates/screenshots/approved-github/2026-07-18_PHASE-1-group-memberships-47-47-final.png`

## Next milestone

Deploy `WIN11-HR01` on VMnet3 and validate the end-to-end client workflow:

`DHCP lease -> internal DNS -> Domain Controller discovery -> Domain Join -> domain sign-in -> Group Policy`
