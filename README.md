# Agentic coding scaffold

A personal, drop-in agent workspace for any code project. Lean on purpose: short
rules that agents actually read.

To install, ask an agent to follow `SETUP.md` for the target project.

## Layout

```
agentic-scaffold/
├── README.md                 this file
├── SETUP.md                  install and upgrade steps
├── gitignore.snippet         lines to append to the project .gitignore
├── kit/                      copied whole into the project root
│   ├── AGENTS.md             agent entry point; fill in
│   ├── CLAUDE.md             one line: @AGENTS.md
│   └── agent-docs/
│       ├── README.md         folder map and scaffold version
│       ├── guidelines/
│       │   ├── universal/    same in every project; do not edit in a project
│       │   │   ├── workflow.md      task levels, spec lifecycle, statuses
│       │   │   ├── coding.md        code, architecture, compatibility, secrets
│       │   │   ├── verification.md  how much to check, honesty rules
│       │   │   └── git.md           staging, commits, handoff
│       │   └── project/      per project; fill in
│       │       ├── stack.md         layout, commands, environments, data
│       │       ├── coding.md        layering, localization, forbidden zones
│       │       └── workflow.md      deviations from the universal workflow
│       ├── specs/            one folder per feature, from _template.md
│       ├── guides/           how existing things work
│       └── memos/            short notes to revisit
├── stacks/                   optional; copy only the stacks a project uses
│   └── dotnet.md             build output, NuGet restore and cache
└── extras/
    └── output-styles/
        └── plain-teacher.md  optional reply tone for Claude Code
```

## Three layers

- **Universal**: true for any codebase.
- **Stack**: true for every project on one stack, e.g. .NET.
- **Project**: facts and limits of one project. Always fill in. An empty project file
  means the universal rule applies as written.

Universal and stack files are never edited inside a project. Change them here, bump
the version in `kit/agent-docs/README.md`, then upgrade projects as `SETUP.md` says.
