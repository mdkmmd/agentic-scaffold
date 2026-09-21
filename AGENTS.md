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
- For NuGet projects, never restore packages into the agent sandbox, `TEMP/`,
  the repository, or any per-task build folder. Build-output isolation does not
  apply to package caches.
- Before restoring NuGet packages, verify `dotnet nuget locals global-packages
  --list`. The resolved path must be the repository owner's normal user cache,
  not an agent-owned path such as `CodexSandboxOffline` or another task
  sandbox.
- Do not set `NUGET_PACKAGES`, `NUGET_HTTP_CACHE_PATH`, or
  `NUGET_PLUGINS_CACHE_PATH` to a sandbox, repository, or temporary task path;
  do not pass `--packages` with such a path.
- If the normal cache or package network is unavailable, request the required
  permission or report the blocked restore. Do not create or accept a private
  sandbox package cache as a workaround.

\* These rules are guidance for applicable tooling; project-specific rules may
add stricter requirements.
