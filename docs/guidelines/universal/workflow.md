# Workflow (universal)

Applies to every project. Project deviations live in `../project/workflow.md`.

Scale documentation and verification to risk and uncertainty, not lines changed.
Create a spec when it captures decisions, constraints, or acceptance criteria that
are not already clear from the request. Do not create one merely to record that work happened.

## Choose the task level

Read the coding guidelines and inspect relevant code before choosing a level. Read
any existing spec governing the affected behavior. State the level briefly; do not
ask for approval just to classify a task.

| Level | Use when | Documentation |
|---|---|---|
| Small change | Clear, localized, easy to reverse; no behavior or data changes | The request defines scope. No numbered spec. Report changes and verification at completion. |
| Focused spec | A bounded feature or behavior fix | Usually one page or less: problem, intended behavior, scope, acceptance checks, and compatibility constraints. |
| Detailed spec | Cross-cutting changes, migrations, sensitive workflows, or substantial uncertainty | A focused spec plus only the analysis needed: callers, dependencies, data flow, alternatives, rollout, and failure cases. |

A display rename is normally small. A shared theme change may need a focused spec.
A one-line authorization or money calculation change can require a detailed spec.
An investigation can finish with findings alone; it does not authorize implementation.

If inspection reveals wider impact or unresolved requirements, explain the change
in level and capture the needed decisions before implementing the affected work.
Ask about material choices affecting behavior, compatibility, data, or scope.
Resolve routine implementation details within authorized scope without extra approval.

## Small changes

1. Confirm the requested result is clear and inspect affected references.
2. Implement within the request's scope, preserving unrelated work.
3. Run proportional verification and review the diff.
4. Report changes, checks, and any pending verification. Commit only on explicit request.

No spec folder, task checklist, or separate approval ceremony is required.

## Work requiring a spec

Use one folder and one spec per feature: `docs/specs/NNN-short-name/spec.md`.
Create a `context/` subfolder only when supporting material needs it.

1. **Inspect.** Read relevant code, supplied context, and older specs for the same areas.
2. **Specify.** Use `docs/specs/_template.md` for a focused spec. Add analysis only when risk warrants it. Write acceptance checks before coding. The owner reviews and approves scope; creating a spec is not approval.
3. **Implement.** On authorization, complete the approved scope. Tick tasks only when implemented and their required checks pass. Record material decisions and amendments in the same spec.
4. **Review and verify.** Review the diff, run applicable checks, and report remaining manual checks. Record owner verification when confirmed; never tick unperformed checks.
5. **Close.** Mark done only when all tasks and required verification are complete and Outcome is filled. A closed spec is never edited again; subsequent work belongs to a new request or spec.

Changes to approved Goal, Rules, or Touch points require a documented owner-approved
amendment before affected implementation. Do not silently widen scope. Keep Open
points for unresolved material questions and Decisions for their resolutions.

## Owner maps

Long spec studies with many steps are hard to follow. Keep a plain-English `map.md`
beside `spec.md`, and update it after each step. Use
`docs/specs/NNN-short-name/map.md`, not `context/`.
Write `map.md` to explain, not to list. Use plain English in complete sentences, and
give the reason as well as the fact. Explain any technical term the first time you use it.
Use normal Markdown for structure: numbered `##` headings, real `-` lists (one level
only), and tables for comparisons and examples. Emoji sit on top of that structure,
never in place of it: put 🔸 at the start of each `##` heading, and ✅ / ⏳ in the status
column. Never use emoji as list bullets. Use → only in short examples ("empty cart →
checkout disabled"), not to chain fragments in place of sentences.
Include a status board (steps and status), sections from the basics up to the current
step, dated decisions, and open questions for the owner.
`spec.md` stays the contract; `map.md` is only a summary and never overrides it.
Small changes without a numbered spec do not need a map.

## Status labels

Spec statuses: `draft`, `approved`, `in progress`, `implemented — awaiting verification`, `done`.
Update the status when work reaches that stage.

Implementation, verification, and commit are separate facts. Record a commit
reference when applicable without reopening a closed spec. A commit does not prove
verification; verified work need not be committed to close a spec.

## Sessions and language

Specs are written in English; context material may use any language.
Prefer a fresh session per spec or batch, with sufficient recorded context to continue.
