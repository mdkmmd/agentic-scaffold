# Specs

One folder per feature: `NNN-short-name/spec.md`. Numbers are sequential and never reused.

```
agent-docs/specs/
├── _template.md              copy this to start a spec
├── 001-short-name/
│   ├── spec.md               the single source of truth for the feature
│   └── context/              optional: only when supporting material exists
│       ├── call_notes_*.md   what the owner said, any language
│       ├── code_map.md       where the affected code lives
│       ├── *_schema*.md      data snapshots
│       ├── *.sql             scripts written for this feature
│       └── screenshots/      images, with a screenshots_notes.md if unclear
└── 002-short-name/
```

Rules:

- The spec is the contract. Context is evidence, never the contract.
- Specs in English. Context material in any language.
- A closed (`done`) spec is never edited again. New work gets a new spec.
- Read older specs that govern the same behavior before writing a new one.
