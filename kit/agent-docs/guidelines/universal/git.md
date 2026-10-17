# Git and handoff (universal)

## Never

- Never stage or commit unless the user explicitly requests it.
- Never push without an explicit request.
- Never discard work or rewrite history.
- Never stage ignored files. Never use `git add -f`.

By default, leave changes unstaged and uncommitted for the owner, then report.

## When asked to commit

- Review the staged diff first.
- Include only the requested task's changes. Use partial staging when a file holds unrelated edits.
- Preserve existing work and already staged changes.
- For spec work, prefix the message with the spec number: `006: rename displayed app branding`.
- For small changes without a spec, use a concise descriptive message. Do not invent a spec number.

## Local-only files

`agent-docs/`, `CLAUDE.md`, `AGENTS.md`, and `.claude/` are always gitignored. The agent
workspace is personal and stays out of the shared history. Ticking a task in `spec.md`
is a local edit, not something to stage.

## Handoff message

At the end of a task report, in this order:

1. Result: what changed.
2. Verification: what was checked, what failed, what is still pending.
3. Commit status, when applicable.

Keep the detail proportional to the task.
