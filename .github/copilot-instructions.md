# Agent Workflow Rules for GitHub Copilot

## Core Collaboration Docs

All collaboration artifacts live in `docs/ai/`. Always refer to these files for planning context:

### Required Reading Order

1. `docs/ai/PROJECT_CONTEXT.md` - project goals and conventions
2. `docs/ai/PROGRESS_LOG.md` - recent factual changes
3. `docs/ai/ACTIVE_WORK.md` - current short backlog
4. `docs/ai/FEATURE_REGISTRY.md` - registered features

### Non-Negotiable Rules

- Never run `git commit` or push without explicit user instruction.
- Plan from trusted sources only; do not infer backlog from old roadmap or archived docs.
- New features must be registered in `FEATURE_REGISTRY.md` before implementation.
- After completing work, update progress log, then propose "prepare commit" as a draft only.

### ID Conventions

- Feature: `<DOMAIN>-F<nn>` (e.g. `CORE-F01`)
- Slice: `<FeatureID>-S<nn>` (e.g. `CORE-F01-S01`)
- Bug: `BUG-<DOMAIN>-<nnn>`
- ADR: `ADR-<yyyyMMdd>-<nn>`
