# TMPL-F04 Engineering Design Workflow Implementation Plan

## Meta
- **ID:** `TMPL-F04`
- **Status:** `Done`
- **Owner:** Max
- **Last updated:** `2026-09-22`
- **Related:** [Design Spec](./TMPL-F04_ENGINEERING_DESIGN_WORKFLOW_DESIGN.md)

## Goal

Ship domain-neutral engineering design/review capabilities into the existing portable workflow.

## Design Decisions Being Implemented

1. Add `engineering-design` and `design-review` skills as behavior authority
2. Upgrade design + implementation templates for structured reasoning and traceability
3. Encode complexity levels + readiness gate in DOC_GOVERNANCE
4. Thin-wire adapters and presets; avoid rule duplication

## Slice plan

| Slice ID | Summary | Design decision | Verification | Status |
|----------|---------|-----------------|--------------|--------|
| `TMPL-F04-S01` | Register + design/plan docs | Authority map | Doc review | Done |
| `TMPL-F04-S02` | Skills + templates | Design/review behaviors + artifact shape | Doc review; domain-neutral scan | Done |
| `TMPL-F04-S03` | Governance + adapters + presets + DoD | Complexity/readiness; profile effects | Cross-link review; PR | Done |

## Slice → Design Traceability

- S01 → Proposed Architecture / Authority map
- S02 → Engineering Design Skill + Design Review + template structures
- S03 → Complexity Levels + Readiness Gate + Profile integration

## Risks / Mitigations

- Risk: Over-ceremony for small tasks → Complexity L0/L1 escape hatches
- Risk: Duplicate conflicting rules → single authority + thin adapters
- Risk: Engine-specific leakage → domain-neutral examples only

## Completion Criteria

- All acceptance checklist items in Design Spec checked
- Branch pushed and PR opened per request brief
