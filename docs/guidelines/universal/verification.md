# Verification (universal)

Verification is mandatory, but proportional. The concrete commands live in
`../project/stack.md`.

## How much

- Text and caption edits: resource check, diff review, and applicable visual review.
- Behavior changes: check the new behavior and the nearest regressions.
- Data or schema changes: check the migration path forward and the rollback story.
- Repeat or broaden checks only after changes, failures, or unresolved concerns justify it.

## Build and tests

- Run the project's build after a coherent implementation task that touches compiled code.
- For very small caption, resource, comment, or documentation edits, skip the build and app run; use targeted checks instead.
- Run relevant tests where they give meaningful evidence. Do not add tests that merely repeat trivial implementation.

## Honesty

- Report failures honestly. Fix failures caused by the task.
- Distinguish failures caused by the task, pre-existing failures, and blocked checks.
- Never claim a green check without evidence.
- Never tick an acceptance check that was not performed. Owner confirmation counts as evidence and is recorded as such.
