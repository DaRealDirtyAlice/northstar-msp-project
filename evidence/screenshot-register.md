# Screenshot Register

Last reviewed: **2026-07-18**

The temporary attachment paths below are references only and may expire. No raw screenshot is considered preserved until a sanitized copy is deliberately stored in the appropriate Case or phase folder.

## Screenshots received so far

| Attachment | Subject | Decision | Intended use | Reason / required action |
|---|---|---|---|---|
| `codex-clipboard-4c5d4226-eb90-4180-9a95-fca9d91d1ea2.png` | VMnet3 configuration before final correction | Rejected for milestone post | Internal setup history only | VMware DHCP was still enabled; capture a fresh final-state image |
| `codex-clipboard-b996584c-21b9-4552-8af7-9a7f2b918c2f.png` | VMware Easy Install edition selection | Selected — internal | Bootstrap troubleshooting | Documents the unattended-install path; not a final-state result |
| `codex-clipboard-b02158ef-ebbc-4fda-8a2a-41afb0745338.png` | Generic host-only network selection | Rejected for milestone post | Setup history only | Does not prove the adapter was changed to VMnet3 |
| `codex-clipboard-bd6b35f5-5ce6-4651-85a4-cf4bbf1b5724.png` | Virtual disk filename | Rejected | None | Low evidentiary value |
| `codex-clipboard-a3c02169-3eb5-4265-98df-8c50f3606d60.png` | Microsoft license-terms setup error | Selected — internal | Bootstrap troubleshooting | Useful symptom evidence; unsuitable as the lead LinkedIn image |
| `codex-clipboard-9837b23a-b175-4bed-b637-b9ddb5b5dc4a.png` | Manual custom-install screen | Selected — internal | Bootstrap troubleshooting | Supports the corrective workflow but not final validation |
| `codex-clipboard-087e181d-2dd5-45d7-8d99-c453af582744.png` | Server Core SConfig | Selected — internal | Incorrect-edition troubleshooting | Proves the observed symptom; do not present it as final architecture |
| `codex-clipboard-5b1e6c28-5303-4575-86d5-23a87da3dd26.png` | UEFI boot manager | Rejected for milestone post | Setup history only | Transitional screen with little outcome value |
| `codex-clipboard-fe36c16f-7e63-48d3-b7af-46bf153f2cce.png` | DC01 hostname and static IP validation | Conditional | Phase 1 internal evidence; possible LinkedIn secondary image | Correct technical state, but crop or redact the virtual MAC address before public use |

## Current LinkedIn screenshot shortlist

No screenshot is yet approved as fully public-ready. Capture these fresh final-state views:

1. VMnet3 showing host-only `10.50.10.0/24` with VMware DHCP disabled.
2. Server Manager showing DC01 with AD DS, DNS and DHCP healthy.
3. Sanitized PowerShell output for Forest, Domain and critical-service validation.
4. DHCP console showing the active scope and options 006/015.

## Selection criteria

A LinkedIn screenshot must:

- Prove a completed or validated result.
- Be readable after LinkedIn image compression.
- Exclude passwords, DSRM/recovery keys, tokens and product keys.
- Exclude real personal data, public IPs, MAC addresses and unrelated notifications.
- Show enough surrounding context to establish what tool or service produced the result.
- Avoid exposing known-wrong configurations unless the post is explicitly a troubleshooting retrospective.

