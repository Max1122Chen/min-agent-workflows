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
- `docs/ai/WORKFLOW_PROFILE.md` - deploy-time collaboration posture (presets)
- `docs/ai/BOOTSTRAP_DIGEST.md` - short session recovery
- `docs/ai/ACTIVE_WORK.md` - active queue
- `docs/ai/FEATURE_REGISTRY.md` - feature registration
- `docs/ai/PROGRESS_LOG.md` - append-only factual history
- `docs/ai/TECH_DEBT.md` - explicit debt
- `docs/ai/templates/` - reusable doc templates
- `docs/ai/templates/WORKFLOW_PRESETS.md` - preset catalog and option→effect map

## Workflow Profile Gate

On bootstrap / first substantial work:

1. Read `docs/ai/WORKFLOW_PROFILE.md`.
2. If `status` is `unconfigured`, ask the meta-question **once**:
   - configure now / skip (`serious-engineering` defaults) / later (`deferred`)
3. If user configures, prefer named presets in `WORKFLOW_PRESETS.md`; allow dimension overrides.
4. Write results back to `WORKFLOW_PROFILE.md` and summarize Effective behavior.
5. Do not re-ask when status is `configured`, `default-applied`, or `deferred` (unless user says `reconfigure workflow`).

Profile may tune strictness, autonomy, role, language, topology, verification bar, and implementation discipline.  
Profile must **not** disable: commit preparation gate, planning trust tiers, or Draft≠large-coding.

## Naming Guidance

- Feature IDs: `<DOMAIN>-F<nn>`
- Slice IDs: `<FeatureID>-S<nn>`
- Bug IDs: `BUG-<DOMAIN>-<nnn>`
- ADR IDs: `ADR-<yyyyMMdd>-<nn>`
- Long docs (ALL CAPS): `docs/ai/<DOMAIN>/<FEATURE_ID>_<SLUG>_<DOC_TYPE>.md`
  - `<DOC_TYPE>`: `DESIGN` | `IMPLEMENTATION` | `ROADMAP` | `REFACTOR_PLAN`

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
- `docs/ai/WORKFLOW_PROFILE.md`
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
- Workflow profile missing / `unconfigured`:
  - ask meta-question once per `docs/ai/templates/WORKFLOW_PRESETS.md`
- User says `reconfigure workflow`:
  - re-run profile flow and update `WORKFLOW_PROFILE.md`

## Implementation Discipline (optional; follow profile)

If `WORKFLOW_PROFILE.md` has `implementation_discipline: on` (or preset implies it):

### Principles

1. Reuse before duplication.
2. Remove dead or superseded paths in the same change when safe.
3. If transitional code must remain, register explicit debt with exit condition.
4. Keep exports and public APIs aligned with actual usage.

### Boundary

- In scope: cleanup directly touched by the current task.
- Out of scope: unrelated large rewrites; register debt instead.

If profile sets `implementation_discipline: off`, do not force cleanup beyond task needs; still avoid silently growing unbounded dual paths without debt.

## Operating Loop

1. Register Feature ID
2. Write Design / Implementation Plan
3. Implement by slices
4. Verify
5. Update progress + registry
6. Prepare commit, then execute only with explicit approval

## Placement Rules

- Design / Implementation / Roadmap / Refactor Plan / ADR docs **must** live under `docs/ai/<DOMAIN>/`.
- Do **not** place those long docs in `docs/ai/` root (root is for core collaboration truth only).
- Template examples belong only under `docs/ai/templates/`.
- Session notes should be stored in `docs/ai/sessions/` when used.
- Filenames for Feature-linked long docs are ALL CAPS and include the Feature ID.
