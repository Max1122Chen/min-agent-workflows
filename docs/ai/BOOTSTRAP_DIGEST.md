# Bootstrap Digest

Last updated: YYYY-MM-DD
Purpose: recover collaboration context in under 2 minutes.

## Read order for a new session

1. `PROJECT_CONTEXT.md`
2. `PROGRESS_LOG.md` (recent entries only)
3. `ACTIVE_WORK.md`
4. `FEATURE_REGISTRY.md` (In Progress / Planned)
5. `TECH_DEBT.md` (Open)
6. Task-specific design doc (if linked by ACTIVE_WORK or explicitly named by user)

## Non-negotiable collaboration rules

- Plan from trusted sources only; do not infer backlog from old roadmap snapshots.
- New Feature/Refactor: register ID, define design/plan, then implement.
- A `Draft` design does not authorize large-scale coding.
- End of meaningful batch: update docs and propose "prepare commit" before unrelated next work.
- Prepare commit is draft-and-review only; execute commit only with explicit user instruction.

## ID scheme

- Feature: `<DOMAIN>-F<nn>`
- Slice: `<FeatureID>-S<nn>`
- Bug: `BUG-<DOMAIN>-<nnn>`
- ADR: `ADR-<yyyyMMdd>-<nn>`

## Verification baseline

- Verify command: `<replace-with-verify-command>`
- Smoke test command: `<replace-with-smoke-test-command>`

## Handoff trigger cues

When user indicates handoff/session switch:
- Write session note from template
- Append one progress entry
- Mark incomplete slice as Blocked/Deferred with reason and unblock condition
