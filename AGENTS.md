# min-agent-workflows

Portable workflow template for agent-assisted software development.

## Project Structure

- `docs/ai/` - Collaboration truth and workflow records
- `docs/ai/templates/` - Design, plan, ADR, bug, session templates
- `.cursor/rules/` - Optional Cursor enforcement layer
- `.opencode/` - Optional opencode layer
- `AGENTS.md` - This file (opencode / general agent rules)
- `CLAUDE.md` - Claude Code rules
- `INIT_GUIDE.md` - How to initialize this template in a new repo

## Doc Layout

- `docs/ai/PROJECT_CONTEXT.md` - stable project snapshot
- `docs/ai/BOOTSTRAP_DIGEST.md` - short session recovery
- `docs/ai/ACTIVE_WORK.md` - active queue
- `docs/ai/FEATURE_REGISTRY.md` - feature registration
- `docs/ai/PROGRESS_LOG.md` - append-only factual history
- `docs/ai/TECH_DEBT.md` - explicit debt
- `docs/ai/templates/` - reusable doc templates

## Naming Guidance

- Feature IDs: `<DOMAIN>-F<nn>`
- Slice IDs: `<FeatureID>-S<nn>`
- Bug IDs: `BUG-<DOMAIN>-<nnn>`
- ADR IDs: `ADR-<yyyyMMdd>-<nn>`

## Hard Constraints

### Commit preparation gate

- "Prepare commit" means draft message and readiness checks, not immediate commit.
- Never run `git commit` or push without explicit user instruction to execute.
- Draft from actual diffs, not from guessed intent.

### Planning source discipline

- Use trusted planning sources first: `docs/ai/ACTIVE_WORK.md`, `FEATURE_REGISTRY.md`, `TECH_DEBT.md`, recent `PROGRESS_LOG.md`, code/tests.
- Do not infer backlog from snapshot/archive/reference docs.

### Refactor discipline

- Refactor work should target a clear end state.
- Avoid leaving silent dual-path temporary layers; either remove or register debt.

### Context recovery

When context may be stale, re-bootstrap from:
- `docs/ai/BOOTSTRAP_DIGEST.md`
- `docs/ai/PROJECT_CONTEXT.md`
- `docs/ai/ACTIVE_WORK.md`

## Doc Trust Tiers

### Planning sources (high trust)

- `docs/ai/ACTIVE_WORK.md`
- `docs/ai/FEATURE_REGISTRY.md` (In Progress / Planned)
- `docs/ai/TECH_DEBT.md` (Open)
- recent `docs/ai/PROGRESS_LOG.md`
- code, tests, and verify commands

### Reference sources (do not auto-create backlog)

- old roadmap files
- docs explicitly marked Snapshot, Archived, or Reference
- stale unchecked checklist sections in historical design docs

### Conflict resolution

If docs conflict with runtime truth, code/tests/verification outputs take precedence.

## Workflow Triggers

When user intent implies one of these, recommend the corresponding workflow before large edits:

- Plan/roadmap/priorities:
  - check `ACTIVE_WORK.md`, `FEATURE_REGISTRY.md`, and trusted sources
- New feature/refactor:
  - register Feature ID, create or update Design Spec, then Implementation Plan
- Significant unknown scope:
  - perform a brief pre-flight (dependencies, risks, debt, verification path)
- Bug/regression:
  - create/update bug record with reproduction and regression checks
- Handoff/session switch:
  - session note + progress entry + blocked/deferred status for incomplete slices
- End of meaningful batch:
  - complete DoD checks, then propose "prepare commit"
- Commit preparation request:
  - draft commit message and wait for explicit execute instruction

## Implementation Discipline (optional, enable for engineering-heavy repos)

### Principles

1. Reuse before duplication.
2. Remove dead or superseded paths in the same change when safe.
3. If transitional code must remain, register explicit debt with exit condition.
4. Keep exports and public APIs aligned with actual usage.

### Boundary

- In scope: cleanup directly touched by the current task.
- Out of scope: unrelated large rewrites; register debt instead.

## Operating Loop

1. Register Feature ID
2. Write Design / Implementation Plan
3. Implement by slices
4. Verify
5. Update progress + registry
6. Prepare commit, then execute only with explicit approval

## Placement Rules

- New design and implementation docs belong under `docs/ai/` or domain subfolders inside it.
- Template examples belong only under `docs/ai/templates/`.
- Session notes should be stored in `docs/ai/sessions/` when used.
