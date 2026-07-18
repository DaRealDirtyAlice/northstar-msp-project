# Screenshot Publication Decisions

Last reviewed: **2026-07-18**

## Decision Summary

- Received screenshots: **38**
- Approved for direct GitHub upload: **16**
- Approved for direct LinkedIn upload: **14**
- Conditional after redaction or recapture: **6**
- Internal setup or troubleshooting evidence: **14**
- Rejected because of low evidentiary value or incorrect state: **6**

## Register

| Local filename | Context | GitHub decision | LinkedIn decision | Reason and required action |
|---|---|---|---|---|
| `2026-07-15_SETUP_VMnet3-before-final-correction.png` | VMnet3 before final correction | Internal only | Reject | VMware DHCP was still enabled. Recapture the final isolated configuration. |
| `2026-07-15_SETUP_Easy-Install-edition-selection.png` | VMware Easy Install selection | Internal only | Reject | Useful for bootstrap history but does not prove a completed result. |
| `2026-07-15_SETUP_host-only-network-selection.png` | Generic host-only selection | Internal only | Reject | Does not prove the VM was connected to the final VMnet3 network. |
| `2026-07-15_SETUP_virtual-disk-name.png` | Virtual disk filename | Reject | Reject | Low technical and portfolio value. |
| `2026-07-15_SETUP_license-terms-error.png` | Windows setup license error | Internal only | Internal only | Useful symptom evidence for a troubleshooting retrospective, not a milestone lead image. |
| `2026-07-15_SETUP_manual-custom-install.png` | Manual custom-install screen | Internal only | Internal only | Supports the corrective workflow but not final validation. |
| `2026-07-15_SETUP_incorrect-Server-Core-install.png` | Incorrect Server Core installation | Internal only | Internal only | Proves the symptom in the installation lesson; do not present it as final architecture. |
| `2026-07-15_SETUP_UEFI-boot-manager.png` | UEFI boot menu | Reject | Reject | Transitional screen with little outcome value. |
| `2026-07-18_PHASE-1_DC01-hostname-static-IP.png` | DC01 hostname and static IP | Conditional | Conditional | Technically useful, but the virtual MAC address must be removed or obscured before publication. |
| `2026-07-18_PHASE-1_AD-OU-structure-validated.png` | Completed custom OU hierarchy in ADUC | Approved | Approved as a secondary image | Cleanly proves the 12-OU Northstar structure. No password, personal data, MAC address, or public IP is visible. |
| `2026-07-18_PHASE-1_AD-security-groups-validated.png` | Groups OU plus command validation for 10 groups | Approved | Approved | Proves that all designed groups exist and report `Global / Security`. The visible Administrator path is generic lab context and no secret is exposed. |
| `2026-07-18_PHASE-1_ns-admin-membership-not-yet-validated.png` | `ns-admin` properties and Domain Admins validation mismatch | Internal only | Reject | `Member Of` shows Domain Admins, but PowerShell lists only the built-in Administrator. Apply or refresh the change, then recapture successful validation. |
| `2026-07-18_PHASE-1_domain-admins-membership-concept.png` | Repeated view used to explain privileged-group membership | Internal only | Reject | Useful as teaching context, but it repeats the same unvalidated state and does not yet prove that `ns-admin` is an effective Domain Admins member. |
| `2026-07-18_PHASE-1_ns-admin-domain-admins-validated.png` | Named administrative account and Domain Admins membership validation | Approved | Approved | The repeated command now lists both the built-in Administrator and `Northstar Administrator (ns-admin)`, proving successful privileged-group membership without exposing a password or personal information. |
| `2026-07-18_PHASE-1_ns-admin-filtered-token-validation.png` | Interactive `ns-admin` sign-in and UAC-filtered token validation | Internal only | Conditional after recapture | `whoami` confirms `corp\\ns-admin` and the token contains Domain Admins, but `Group used for deny only` shows this PowerShell window is not elevated. Recapture from an Administrator PowerShell window for clean effective-privilege evidence. |
| `2026-07-18_PHASE-1_ns-admin-elevated-token-validated.png` | Elevated token confirms effective Domain Admins privileges | Conditional | Conditional | Technically valid: the elevated window reports Domain Admins as mandatory and enabled. Recapture or crop without the red Server Manager status tiles for stronger public presentation. |
| `2026-07-18_PHASE-1_user-csv-validation-in-progress.png` | CSV count, department distribution, and user preview | Conditional | Conditional after recapture | Confirms 20 fictional records and the expected 4/4/6/6 department distribution, but the manager-reference check still shows the continuation prompt and no returned PowerShell prompt. Complete the command and recapture the final validation summary. |
| `2026-07-18_PHASE-1_user-csv-preflight-validated.png` | Fictional user dataset and manager-reference preflight validation | Approved | Approved as a secondary image | Displays all 20 fictional employee records, the expected department distribution, and a manager-reference check that returns no invalid records before returning to the PowerShell prompt. No credentials or real personal data are exposed. |
| `2026-07-18_PHASE-1_existing-user-check-noisy-errors.png` | Identity-based collision query returns expected not-found exceptions | Internal only | Reject | The users do not exist, which is the desired pre-import state, but `Get-ADUser -Identity` produces noisy `ADIdentityNotFoundException` output. Replace it with a filter-based query and recapture a concise pass result. |
| `2026-07-18_PHASE-1_target-ou-groups-preflight-validated.png` | Target OU and department-role group preflight | Approved | Approved as a secondary image | Cleanly proves all four target department OUs and eight department/manager Global Security groups exist before user creation. |
| `2026-07-18_PHASE-1_username-mapping-preview.png` | Preview of 20 generated usernames and department-group mappings | Conditional | Conditional after recapture | The mapping is correct and the duplicate-name check returns no matches, but the image ends during the noisy existing-account query. Recapture with an explicit zero-conflict summary. |
| `2026-07-18_PHASE-1_user-import-zero-conflict-preflight.png` | Final zero-conflict user-import preflight | Approved | Approved | Provides a concise change-control checkpoint: 20 planned users, zero generated-name duplicates, zero existing AD conflicts, all eight department-role groups, and both shared groups validated as Global Security groups. |
| `2026-07-18_PHASE-1_user-import-whatif-validated.png` | Twenty-user AD import dry run | Approved | Approved | Shows 20 correctly targeted `New-ADUser -WhatIf` operations, a planned count of 20, and a post-run AD count of zero, proving the automation was rehearsed without changing directory state. |
| `2026-07-18_PHASE-1-user-import-rerun-skipped-existing-detail.png` | Import rerun reports all accounts as existing | Internal only | Reject | Demonstrates the duplicate-protection branch, but the all-`SkippedExisting` result does not identify the earlier successful creation pass and is not suitable as the main completion evidence. |
| `2026-07-18_PHASE-1-user-import-idempotency-validation.png` | Idempotent rerun plus current AD count | Internal only | Internal only | Useful engineering evidence that rerunning the import did not create duplicates; retain for documentation, but use the clean count/distribution image publicly. |
| `2026-07-18_PHASE-1-20-users-department-distribution.png` | Twenty created AD users distributed across department OUs | Approved | Approved | Cleanly verifies 20 existing users with the intended HR 4, Finance 4, Sales 6, and Operations 6 distribution. |
| `2026-07-18_PHASE-1-user-validation-all-disabled-summary.png` | Post-import validation shows all 20 accounts disabled | Internal troubleshooting evidence | Reject | Employee IDs, departments, titles, and first-logon flags are populated, but `EnabledUsers` is zero. Reset a compliant temporary password, enable the accounts, and recapture the corrected summary. |
| `2026-07-18_PHASE-1-user-validation-disabled-detail.png` | Detailed list of 20 disabled imported accounts | Internal troubleshooting evidence | Reject | Confirms every imported account currently reports `Enabled = False`; useful for root-cause documentation but not as completion evidence. |
| `2026-07-18_PHASE-1-password-policy-command-typing-error.png` | Password-policy query mistyped with an extra leading character | Internal troubleshooting evidence | Reject | `aGet-ADDefaultDomainPasswordPolicy` is not a valid command. This is a harmless input error and made no directory changes; rerun the correct read-only command. |
| `2026-07-18_PHASE-1-disabled-user-repair-20-enabled.png` | Password reset and account-enable repair for all 20 users | Approved | Conditional after recapture | Strong remediation evidence: all 20 accounts report `Enabled` with no failures. The stray unexecuted `a` at the prompt reduces LinkedIn polish; use the clean post-repair query as the public completion image. |
| `2026-07-18_PHASE-1-20-users-enabled-final-validation.png` | Final post-repair AD account validation | Approved | Approved | Fresh directory queries prove 20 total users, 20 enabled users, zero disabled users, and 20 accounts requiring a password change at first sign-in. This is the preferred public completion image for the account-creation stage. |
| `2026-07-18_PHASE-1-manager-relationships-validated.png` | Employee-to-manager relationship assignment and validation | Approved | Approved | Shows all 16 planned relationships assigned successfully and confirms the final directory state of 20 users, 16 with managers, and four top-level department managers. |
| `2026-07-18_PHASE-1-group-membership-preflight-validated.png` | Security-group membership assignment preflight | Approved | Approved | Proves 47 planned assignments across 20 users and 10 groups, with zero duplicate assignments and zero missing user or group targets before the write operation. |
| `2026-07-18_PHASE-1-group-memberships-applied-detail.png` | Per-group membership write results | Approved | Approved as a secondary image | Shows every group reached its planned final count with `Success`, including 20 printer users and three VPN users. |
| `2026-07-18_PHASE-1-group-memberships-applied-summary.png` | Group membership write summary | Approved | Internal supporting evidence | Concisely reports 10 groups processed, 47 memberships added, and zero failed groups; useful in the repository but redundant for a LinkedIn carousel. |
| `2026-07-18_PHASE-1-group-memberships-per-group-validated.png` | Fresh per-group expected-versus-actual validation | Approved | Approved | Strong public evidence that all 10 group counts match their expected values with zero missing or unexpected users. |
| `2026-07-18_PHASE-1-group-memberships-47-47-final.png` | Final aggregate group-membership validation | Approved | Approved | Clean completion checkpoint showing 47 expected memberships, 47 actual memberships, zero missing, and zero unexpected assignments. |
| `2026-07-18_PHASE-1-user-group-report-exported-validation-blank.png` | Exported audit CSV opened while validation summary is blank | Conditional after recapture | Conditional after recapture | The file visibly contains the expected fictional user records and exists at the intended path, but the five validation values are blank and the Notepad window obscures the commands. Re-import into a correctly named array variable and capture a clean 20/20/20/16/4 summary. |

## Current Capture List

Capture these clean final-state images before publishing the Phase 1 milestone:

1. VMnet3 showing host-only `10.50.10.0/24` with VMware DHCP disabled.
2. Server Manager showing DC01 with AD DS, DNS, and DHCP healthy.
3. Sanitized PowerShell output for Forest, Domain, and critical-service validation.
4. DHCP console showing the active scope and options 006/015.

## Automatic Review Rule

Whenever a new screenshot is received, immediately save a local copy to `inbox/`, identify the active phase or Case, update this register, and make separate GitHub and LinkedIn decisions before recommending the next technical step.
