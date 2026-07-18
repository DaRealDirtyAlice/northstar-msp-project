# Case Documentation Workflow

Each troubleshooting Case receives its own folder only when a fault is intentionally introduced or reported as a service-desk issue.

Recommended naming:

```text
cases/
└── CASE-001-locked-ad-account/
    ├── README.md
    └── screenshot-selection.md
```

## Required Case contents

- Case ID, date, user and business impact
- Initial report written without revealing the root cause
- Troubleshooting timeline and tested hypotheses
- Confirmed root cause
- Safe resolution and rollback considerations
- Technical validation and user confirmation
- Preventive action and related knowledge-base article
- Screenshot candidates received during the Case
- Final selected internal and LinkedIn-safe screenshots
- Optional LinkedIn update draft

Use [CASE-TEMPLATE.md](CASE-TEMPLATE.md) for every new Case.

## Screenshot workflow

When a screenshot is sent in the project conversation, evaluate it as one of:

- `Selected — public`: safe and useful for LinkedIn
- `Selected — internal`: useful technical evidence but not safe or clear enough for public posting
- `Conditional`: usable after cropping or redaction
- `Rejected`: incorrect configuration, duplicated evidence, weak proof or sensitive content

Never treat a configuration screenshot as proof of success when a command or functional test is required.

