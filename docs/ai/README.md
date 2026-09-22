# AI Collaboration Docs Index

This folder is the project collaboration truth for humans and agents.

## Agent: required planning sources

Use these files for "what to do next":

1. `WORKFLOW_PROFILE.md` - collaboration posture (configure if `unconfigured`)
2. `ACTIVE_WORK.md` - current short backlog
3. `FEATURE_REGISTRY.md` - registered features (focus on In Progress / Planned)
4. `TECH_DEBT.md` - open debt items
5. `PROGRESS_LOG.md` - recent factual changes
6. Code + tests + verify scripts - runtime truth overrides stale docs

Rules for trust tiers and exceptions:
- If using Cursor: `.cursor/rules/docs-trust-tiers.mdc`
- Otherwise: follow `templates/DOC_GOVERNANCE.md` section "Agent doc trust"

## Core files

- `WORKFLOW_PROFILE.md` - deploy-time posture / presets (strictness, autonomy, role, language)
- `PROJECT_CONTEXT.md` - stable high-level project snapshot
- `BOOTSTRAP_DIGEST.md` - fast session recovery page
- `ACTIVE_WORK.md` - human-maintained working queue
- `FEATURE_REGISTRY.md` - feature IDs and status
- `PROGRESS_LOG.md` - chronological log of completed work
- `TECH_DEBT.md` - acknowledged debt with owners and revisit date
- `WORKING_WITH_AI.md` - collaboration prompts and working habits

## Templates

See `templates/` for Design, Implementation Plan, ADR, Bug Record, Session Note, and Workflow Preset templates.

## Domain buckets and naming

- Long design/implementation docs live under `docs/ai/<DOMAIN>/` (not root).
- Filename pattern (ALL CAPS): `<FEATURE_ID>_<SLUG>_DESIGN.md` (also `_IMPLEMENTATION` / `_ROADMAP` / `_REFACTOR_PLAN`).
- Full rules: `templates/DOC_GOVERNANCE.md` §3.1–3.2.
- Design complexity + readiness: `templates/DOC_GOVERNANCE.md` §5.2–5.3.
- Skills: `.opencode/skills/engineering-design/`, `.opencode/skills/design-review/`.
