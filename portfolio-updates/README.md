# Portfolio Update Workspace

This folder is the single workspace for screenshot intake and date-ordered LinkedIn update documents.

## Required Structure

```text
portfolio-updates/
|-- screenshots/
|   |-- inbox/                Local-only copies of received screenshots
|   |-- approved-github/      Sanitized evidence approved for the repository
|   `-- approved-linkedin/    Sanitized images approved for public posting
`-- linkedin-updates/         Date-prefixed Word documents for milestones and Cases
```

The raw inbox is excluded from Git so that a screenshot is never uploaded merely because it was received. Only reviewed and sanitized files may be copied into an approved folder.

## Per-Screenshot Decision

Every received screenshot receives two independent decisions:

- **GitHub:** Approve, Conditional, Internal only, or Reject
- **LinkedIn:** Approve, Conditional, Internal only, or Reject

The decision must state what the image proves and any required crop or redaction.

## Per-Case Word Document

Use the filename pattern:

`YYYY-MM-DD_CASE-###_short-title_LinkedIn-Update.docx`

Each document contains the publication status, copy-ready LinkedIn post, approved image order, image captions, GitHub evidence decision, privacy review, and final posting checklist.
