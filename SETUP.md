# Install into a project

1. Copy `docs/` to the project root.
2. Copy `AGENTS.md` and `CLAUDE.md` to the project root.
3. Append `.gitignore.snippet` to the project's `.gitignore` (skip if you want docs tracked).
4. Fill in `AGENTS.md`: project name, one-line description, the `Never` hard limits, the commands.
5. Fill in `docs/guidelines/project/stack.md` and `project/coding.md`. Leave
   `project/workflow.md` empty unless the project really deviates.
6. Delete this file and the scaffold `README.md` from the project copy.

One PowerShell copy, from the scaffold folder:

```powershell
$target = "D:\path\to\your\repo"
Copy-Item -Recurse docs $target
Copy-Item AGENTS.md, CLAUDE.md $target
Get-Content .gitignore.snippet | Add-Content "$target\.gitignore"
```

## Check it worked

- `docs/guidelines/universal/` has 4 files, unedited.
- `docs/guidelines/project/` has no `<placeholder>` left in `stack.md` and `coding.md`.
- `AGENTS.md` has no `<PROJECT NAME>` left.
- `git status` does not list `docs/`, `AGENTS.md`, or `CLAUDE.md` (when gitignored).
