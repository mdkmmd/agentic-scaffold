# <PROJECT NAME>

<One or two lines: what this app is, stack, and the solution or entry file.>

## Before you touch code

1. Read `docs/guidelines/universal/workflow.md` (how we work).
2. Read `docs/guidelines/universal/coding.md` (how we code).
3. Read `docs/guidelines/project/stack.md`, `project/coding.md`, and `project/workflow.md` (this project's specifics).
4. Classify the task using the workflow. Small changes need no spec; otherwise read the
   active spec in `docs/specs/NNN-*/spec.md` and implement only its approved scope.
   Read any existing spec governing affected behavior.

Verification rules: `docs/guidelines/universal/verification.md`.
Git rules: `docs/guidelines/universal/git.md`.

## Never

- Never stage or commit unless the user explicitly requests it. Do not push without an
  explicit request. Include only the requested changes; never discard work or rewrite
  history. By default, leave changes unstaged and report.
- Never stage ignored files. `docs/`, `CLAUDE.md` and `AGENTS.md` are in `.gitignore`
  on purpose. Never use `git add -f`. Ticking a task in `spec.md` is a local edit,
  not something to stage.
- <Project hard limit, e.g. "Never connect to 10.0.0.5. Local instance only.">

## Commands

```
<build command>
<run command>
```
