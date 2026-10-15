# Agent Workflow Rules for GitHub Copilot

## Core Collaboration Docs

All collaboration artifacts live in `docs/ai/`. Always refer to these files for planning context:

### Required Reading Order

1. `docs/ai/WORKFLOW_PROFILE.md` - collaboration posture (if `unconfigured`, ask meta-question once)
2. `docs/ai/PROJECT_CONTEXT.md` - project goals and conventions
3. `docs/ai/PROGRESS_LOG.md` - recent factual changes
4. `docs/ai/ACTIVE_WORK.md` - current short backlog
5. `docs/ai/FEATURE_REGISTRY.md` - registered features

Preset catalog: `docs/ai/templates/WORKFLOW_PRESETS.md`.  
User phrase `reconfigure workflow` re-runs profile setup.

### Non-Negotiable Rules

- Never run `git commit` or push without explicit user instruction.
- Plan from trusted sources only; do not infer backlog from old roadmap or archived docs.
- New features must be registered in `FEATURE_REGISTRY.md` before implementation.
- After completing work: Process + Quality DoD, then propose "prepare commit" as a draft only.
- Honor `WORKFLOW_PROFILE.md` for strictness/autonomy/role/language; it cannot disable commit gate, trust tiers, L3 safety, comment ID ban, or branch ID ban.
- For L2+ work: Design Spec → Design Review → implementation readiness before large coding (see `.opencode/skills/engineering-design` and `design-review`).
- `Draft` design or design-review `Not ready` does not authorize large-scale coding.
- No Feature/Slice/Bug/ADR IDs in source comments; branches use `feat/<topic>[/<subtopic>]`, never ID-based names.
- Structure lenses: `docs/ai/templates/DESIGN_PRINCIPLES.md`.

### ID Conventions

- Feature: `<DOMAIN>-F<nn>` (e.g. `CORE-F01`)
- Slice: `<FeatureID>-S<nn>` (e.g. `CORE-F01-S01`)
- Bug: `BUG-<DOMAIN>-<nnn>`
- ADR: `ADR-<yyyyMMdd>-<nn>`
- Design/Implementation docs: ALL CAPS under `docs/ai/<DOMAIN>/` — `<FEATURE_ID>_<SLUG>_DESIGN.md` (or `_IMPLEMENTATION` / `_ROADMAP` / `_REFACTOR_PLAN`)
