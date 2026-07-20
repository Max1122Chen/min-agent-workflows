# AI Collaboration Docs Index

This folder is the project collaboration truth for humans and agents.

## Agent: required planning sources

Use these files for "what to do next":

1. `ACTIVE_WORK.md` - current short backlog
2. `FEATURE_REGISTRY.md` - registered features (focus on In Progress / Planned)
3. `TECH_DEBT.md` - open debt items
4. `PROGRESS_LOG.md` - recent factual changes
5. Code + tests + verify scripts - runtime truth overrides stale docs

Rules for trust tiers and exceptions:
- If using Cursor: `.cursor/rules/docs-trust-tiers.mdc`
- Otherwise: follow `templates/DOC_GOVERNANCE.md` section "Agent doc trust"

## Core files

- `PROJECT_CONTEXT.md` - stable high-level project snapshot
- `BOOTSTRAP_DIGEST.md` - fast session recovery page
- `ACTIVE_WORK.md` - human-maintained working queue
- `FEATURE_REGISTRY.md` - feature IDs and status
- `PROGRESS_LOG.md` - chronological log of completed work
- `TECH_DEBT.md` - acknowledged debt with owners and revisit date
- `WORKING_WITH_AI.md` - collaboration prompts and working habits

## Templates

See `templates/` for Design, Implementation Plan, ADR, Bug Record, and Session Note templates.
