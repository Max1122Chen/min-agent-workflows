# Bootstrap Digest

Last updated: 2026-08-07
Purpose: recover collaboration context in under 2 minutes.

## Read order for a new session

1. `WORKFLOW_PROFILE.md` — collaboration posture (if `unconfigured`, ask meta-question once)
2. `PROJECT_CONTEXT.md`
3. `PROGRESS_LOG.md` (recent entries only)
4. `ACTIVE_WORK.md`
5. `FEATURE_REGISTRY.md` (In Progress / Planned)
6. `TECH_DEBT.md` (Open)
7. Task-specific design doc (if linked by ACTIVE_WORK or explicitly named by user)

## Workflow profile gate

- Catalog: `templates/WORKFLOW_PRESETS.md`
- If status `unconfigured`: ask configure now / skip / later (once)
- If status `deferred`: do not re-ask unless user says `reconfigure workflow`
- If status `configured` or `default-applied`: follow Effective behavior

## Non-negotiable collaboration rules

- Plan from trusted sources only; do not infer backlog from old roadmap snapshots.
- New Feature/Refactor: register ID, define design/plan, then implement.
- A `Draft` design does not authorize large-scale coding.
- End of meaningful batch: update docs and propose "prepare commit" before unrelated next work.
- Prepare commit is draft-and-review only; execute commit only with explicit user instruction.
- Profile may tune strictness/autonomy/role/language; it cannot disable the rules above.

## ID scheme

- Feature: `<DOMAIN>-F<nn>`
- Slice: `<FeatureID>-S<nn>`
- Bug: `BUG-<DOMAIN>-<nnn>`
- ADR: `ADR-<yyyyMMdd>-<nn>`
- Design/Implementation docs: ALL CAPS under `docs/ai/<DOMAIN>/` as `<FEATURE_ID>_<SLUG>_DESIGN.md` (or `_IMPLEMENTATION` / `_ROADMAP` / `_REFACTOR_PLAN`)

## Verification baseline

- Verify command: `<replace-with-verify-command>`
- Smoke test command: `<replace-with-smoke-test-command>`
- Enforce bar from profile `verification_bar`

## Handoff trigger cues

When user indicates handoff/session switch:
- Write session note from template
- Append one progress entry
- Mark incomplete slice as Blocked/Deferred with reason and unblock condition
