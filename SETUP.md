# Install into a project

Written for the agent doing the install. "Scaffold" is this folder; "project" is the
repo being set up. Stage and commit nothing; report at the end.

## 1. Copy

1. Copy everything in `kit/` to the project root: `AGENTS.md`, `CLAUDE.md`, `agent-docs/`.
   If `AGENTS.md` or `CLAUDE.md` already exists, stop and ask the owner before replacing it.
2. Append the lines of `gitignore.snippet` that the project `.gitignore` does not already
   have. Create `.gitignore` if missing.
3. Copy each matching stack file from `stacks/` to `agent-docs/guidelines/stacks/`:

   | Project has | Copy |
   |---|---|
   | `*.sln`, `*.slnx`, or `*.csproj` | `dotnet.md` |

   No match: create no `stacks/` folder.

## 2. Fill in

Inspect the project, then replace the `<placeholders>`:

1. `AGENTS.md`: project name and one-line description.
2. `agent-docs/guidelines/project/stack.md` and `coding.md`: only facts found in the
   code, configs, or README. Delete rows and sections that do not apply.
3. Leave `project/workflow.md` as is.

Never guess hard limits, forbidden zones, environments, or hosts. Leave those
placeholders in place and list them as questions for the owner.

## 3. Check and report

- `agent-docs/guidelines/universal/` has 4 files, unedited.
- `git status` does not list `agent-docs/`, `AGENTS.md`, or `CLAUDE.md`.
- If the scaffold was cloned inside the project, say so and ask before removing it.

Report: what was copied, which stack files, what was filled in, and the open questions.

## Upgrade a project

When the project's `agent-docs/README.md` shows an older scaffold version, replace
`guidelines/universal/`, `agent-docs/README.md`, and the stack files already in
`guidelines/stacks/`. Never touch `project/`, `specs/`, `guides/`, or `memos/`.

## Optional: Plain Teacher output style

Copy `extras/output-styles/plain-teacher.md` to `~/.claude/output-styles/`, then pick
"Plain Teacher" as the output style in Claude Code. It changes only how replies are
written, not what the agent does.
