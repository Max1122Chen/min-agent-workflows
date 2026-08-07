# TMPL-F02 Implementation Plan

## Meta
- **ID:** `TMPL-F02`
- **Status:** `Done`
- **Owner:** Max
- **Last updated:** `2026-08-07`
- **Related:** [Design Spec](./TMPL-F02_WORKFLOW_PROFILE_DESIGN.md)

## Goal

Ship a usable profile system: preset catalog, profile file, and adapter triggers.

## Slice plan

| Slice ID | Summary | Dependencies | Verification | Status |
|----------|---------|--------------|--------------|--------|
| `TMPL-F02-S01` | Add `WORKFLOW_PROFILE.md` + presets catalog + design docs | Registry | Doc review | Done |
| `TMPL-F02-S02` | Wire INIT_GUIDE / README / WORKING_WITH_AI / bootstrap | S01 | Doc review | Done |
| `TMPL-F02-S03` | Wire adapters (AGENTS, CLAUDE, Cursor, bootstrap skill, others) | S01 | Doc review | Done |

## Risks and mitigations

- Risk: Agents ignore meta-question
  - Mitigation: Put gate in AGENTS.md, CLAUDE.md, Cursor triggers, and bootstrap skill
- Risk: Profile becomes stale prose
  - Mitigation: Keep fields machine-oriented key/value; map each to concrete behavior

## Blocked/Deferred note (required if applicable)

N/A
