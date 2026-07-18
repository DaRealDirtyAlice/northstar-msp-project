# Evidence Standard

Every completed ticket should include enough evidence to prove the diagnosis without exposing secrets.

## Minimum evidence

- Initial symptom or error
- Relevant configuration or log result
- Troubleshooting sequence
- Root-cause evidence
- Post-fix validation
- User confirmation

## File naming

Use: `TICKETID_step_description_YYYYMMDD.ext`

Example: `NS-INC-001_03_group-membership_20260720.png`

## Sanitization

- Crop unrelated windows and notifications.
- Blur or remove passwords, email addresses, recovery keys, tokens, serial numbers and public IP information.
- Prefer command output containing only the fields needed for the case.
- Do not use a screenshot as a substitute for explaining what the evidence proves.

