# Agentic coding scaffold

A drop-in agent workspace for any code project. Universal rules are written and
final. Project rules are empty templates you fill in once per project.

## Layout

```
agentic-scaffold/
├── README.md                   this file (do not copy into a project)
├── SETUP.md                    the 6-step install checklist
├── AGENTS.md                   agent entry point — copy to the repo root, fill in
├── CLAUDE.md                   one line: @AGENTS.md
├── .gitignore.snippet          lines to append to the project .gitignore
└── docs/
    ├── README.md               map of the docs folder
    ├── guidelines/
    │   ├── universal/          same in every project — copy as-is, do not edit
    │   │   ├── workflow.md     task levels, spec lifecycle, statuses
    │   │   ├── coding.md       code, architecture, compatibility, secrets
    │   │   ├── verification.md how much to check, and honesty rules
    │   │   └── git.md          staging, commits, handoff
    │   └── project/            per project — fill in
    │       ├── stack.md        layout, commands, environments, data
    │       ├── coding.md       layering, localization, forbidden zones
    │       └── workflow.md     deviations from the universal workflow
    ├── specs/
    │   ├── README.md           folder convention
    │   └── _template.md        copy per feature
    └── guides/
        └── README.md           what belongs in a guide
```

## The split

- **Universal** = true for any codebase. Never edit per project. If you need a change,
  change it here in the scaffold, then re-copy.
- **Project** = stack, paths, commands, environments, hard limits. Always fill in.
  An empty project file means "the universal rule applies as written".

Read `SETUP.md` to install it into a repo.
