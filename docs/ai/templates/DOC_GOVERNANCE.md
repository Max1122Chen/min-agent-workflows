# Document Governance

Last updated: YYYY-MM-DD
Status: Active

## 1) Purpose

Ensure any contributor (human or agent) can answer:
1. What problem is being solved?
2. What is done vs pending?
3. What is the next verifiable action?
4. Why was work paused, deferred, or cancelled?

## 2) Document types

- Roadmap: sequencing and priorities
- Design Spec: scope, approach, risks
- Implementation Plan: slices and acceptance checks
- ADR: architectural trade-off decision
- Progress Log: factual timeline
- Bug Record: defect lifecycle and regression safety

## 3) ID conventions

- Feature: `<DOMAIN>-F<nn>`
- Slice: `<FeatureID>-S<nn>`
- Bug: `BUG-<DOMAIN>-<nnn>`
- ADR: `ADR-<yyyyMMdd>-<nn>`

New features must be registered in `docs/ai/FEATURE_REGISTRY.md` before implementation work.

## 4) Required Meta block for long docs

Design, Roadmap, Implementation, and ADR files should include:

```markdown
## Meta
- **ID:** <FeatureID or N/A>
- **Status:** Draft | Planned | In Progress | Review | Done | Blocked | Deferred | Cancelled | Snapshot | Archived | Reference
- **Owner:** <name>
- **Last updated:** YYYY-MM-DD
- **Related:** [link1](./...), [link2](./...)
```

## 5) Agent doc trust

Planning sources:
- `WORKFLOW_PROFILE.md` (for posture; not backlog)
- `ACTIVE_WORK.md`
- `FEATURE_REGISTRY.md` (In Progress / Planned)
- `TECH_DEBT.md` (Open)
- Recent `PROGRESS_LOG.md`
- Code/tests/verify scripts

Reference-only sources:
- old roadmaps
- Snapshot/Archived/Reference docs
- stale checklist fragments

If docs conflict with code/tests, code/tests win.

## 5.1) Workflow profile

- Deploy-time posture lives in `docs/ai/WORKFLOW_PROFILE.md`.
- Preset catalog: `templates/WORKFLOW_PRESETS.md`.
- If profile status is `unconfigured`, ask meta-question once before large work.
- Profile may tune strictness/autonomy/role/language/verification; it cannot disable commit gate or planning trust tiers.

## 6) Slice Done Definition (DoD)

### Docs DoD
- Progress entry appended
- Feature and slice status synchronized
- Design/Plan updated when scope or status changed
- ADR updated for meaningful architectural trade-off
- Bug record updated for defect fixes

### Engineering DoD
- Verification command executed and recorded
- No unrecorded blocking defect discovered during work
- Public API changes reflected in callers or explicitly documented

## 7) Handoff requirements

On handoff/session switch:
1. Create or update a session note
2. Append one progress entry
3. Mark incomplete slice as Blocked/Deferred with reason and unblock condition
4. Provide first concrete next action

## 8) Work boundary

After completing a meaningful batch:
- finish DoD updates
- propose "prepare commit"
- do not start unrelated new feature work unless explicitly requested
