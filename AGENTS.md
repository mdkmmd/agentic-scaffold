# <PROJECT NAME>

<One or two lines: what this app is, stack, and the solution or entry file.>

## Agent communication

- Communicate with the user in English by default, unless the user explicitly
  requests another language.

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

## Build output and dependency restore (where applicable*)

These rules apply only when the project uses the corresponding build or package
tooling; do not create these paths for unrelated stacks.

- Keep custom or isolated build output in the repository-root `TEMP/` directory,
  outside all project directories. For .NET, for example:
  `dotnet build <solution> --artifacts-path .\TEMP\codex-build`.
- Never place custom build output under a project directory. Some build systems
  can copy it back into their own output and create recursive artifact trees.
- Reuse the fixed `TEMP/codex-build` path for agent .NET verification; do not
  create a new output directory for each run.

\* These rules are guidance for applicable tooling; project-specific rules may
add stricter requirements.

## NuGet restore and package cache

- Use the NuGet cache already configured in the execution environment. Its
  location or account name (including `CodexSandboxOffline`) alone is not a
  reason to block a build. Normal restore of the existing dependencies is allowed.
- Do not remove dependencies, change package versions, edit NuGet configuration,
  clear or relocate package caches, or overwrite the IDE's normal build/restore
  metadata as a workaround for verification. Such changes require a separate
  user request.
- Do not redirect package caches into `TEMP/`, the repository, or a per-task
  directory. Build-output isolation applies to compiled and intermediate output,
  not to downloaded dependencies.
- Keep agent build and restore intermediate files under the same fixed
  `TEMP/codex-build` path; do not clean or reuse the IDE's normal `bin/obj`
  directories for agent verification.
- Attempt the build within the permitted environment. Report a blocked check
  only when an actual access, restore, or network failure prevents it; include
  the concrete error. Do not change security settings or bypass sandbox limits.
