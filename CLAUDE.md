# min-agent-workflows

You are working with a portable agent workflow template. Core collaboration docs live in `docs/ai/`.

## Session Start

Always read in order:
1. `docs/ai/WORKFLOW_PROFILE.md` — if `unconfigured`, ask meta-question once (configure / skip / later)
2. `docs/ai/PROJECT_CONTEXT.md`
3. `docs/ai/PROGRESS_LOG.md` (recent entries only)
4. `docs/ai/ACTIVE_WORK.md`
5. `docs/ai/FEATURE_REGISTRY.md` (In Progress / Planned)

Preset catalog: `docs/ai/templates/WORKFLOW_PRESETS.md`.  
User phrase `reconfigure workflow` re-runs the profile flow.

## Hard Rules

- "Prepare commit" means draft only. Never run `git commit` without explicit instruction.
- Plan from trusted sources only: `ACTIVE_WORK.md`, `FEATURE_REGISTRY.md`, `TECH_DEBT.md`, recent `PROGRESS_LOG.md`, code/tests.
- Old roadmap/snapshot files are reference-only. Do not infer backlog from them.
- New features: register Feature ID first, then design and implement.
- End of meaningful batch: update docs, then propose "prepare commit".
- Honor `WORKFLOW_PROFILE.md` for strictness, autonomy, role, language, and verification bar.
- Profile cannot disable the commit gate or planning trust tiers.

## ID Scheme

- Feature: `<DOMAIN>-F<nn>`
- Slice: `<FeatureID>-S<nn>`
- Bug: `BUG-<DOMAIN>-<nnn>`
- ADR: `ADR-<yyyyMMdd>-<nn>`
- Design/Implementation files: `docs/ai/<DOMAIN>/<FEATURE_ID>_<SLUG>_DESIGN.md` (ALL CAPS; also `_IMPLEMENTATION` / `_ROADMAP` / `_REFACTOR_PLAN`)

## Session End

Append to `docs/ai/PROGRESS_LOG.md`, create session note, mark incomplete slices.
