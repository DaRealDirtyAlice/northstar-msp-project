# Codex Project Instructions

This repository is an IT Support Home Lab and job-portfolio project. ChatGPT is the primary tutor; Codex is the repository and computer operator.

## Before working

Read these files first:

1. `progress/CURRENT-STATUS.md` — current state and next milestone
2. `PROJECT-TODO.md` — roadmap and completion state
3. The newest dated file in `progress/` — latest session history

Read other files only when the task requires them.

## Learning and evidence rules

- Explain troubleshooting logic before making lab changes unless the user asks for direct execution.
- Do not complete learning exercises automatically unless explicitly asked.
- Never mark work complete without user confirmation and technical evidence.
- Preserve existing documentation and distinguish planned, built, validated, and troubleshot work.
- Never publish secrets, personal information, real credentials, or unsanitized screenshots.

## ChatGPT handoff workflow

When the user pastes a ChatGPT session handoff:

1. Treat it as a summary to verify, not proof by itself.
2. Update `progress/CURRENT-STATUS.md` with the current state and next milestone.
3. Append the session to the matching dated progress log, or create `progress/YYYY-MM-DD-progress-log.md` if none exists.
4. Update `PROJECT-TODO.md` only for work the user confirms and the evidence supports.
5. Update other affected project files only when the handoff identifies them.
6. Show the user a concise summary of the resulting diff.
7. Commit and push only when the user explicitly asks; use a short descriptive commit message.

Do not create duplicate state, log, or task files. The three files above are the repository's shared memory between ChatGPT and Codex.
