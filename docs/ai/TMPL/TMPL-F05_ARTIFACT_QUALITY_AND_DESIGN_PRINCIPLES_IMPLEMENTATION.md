# TMPL-F05 Artifact Quality And Design Principles Implementation Plan

## Meta
- **ID:** `TMPL-F05`
- **Status:** `Done`
- **Owner:** Max
- **Last updated:** `2026-10-15`
- **Related:** [Design Spec](./TMPL-F05_ARTIFACT_QUALITY_AND_DESIGN_PRINCIPLES_DESIGN.md)
- **Design readiness:** `Ready with deferred items`

## Goal

Land Quality DoD, comment/branch ID hygiene, and design-principle lenses on the existing F04 path without a parallel methodology.

## Design Decisions Being Implemented

| Decision ID / title | Design section | Notes |
|---------------------|----------------|-------|
| D1 Process vs Quality DoD | D1 | L2+ required; L1 recommended |
| D2 Shell red flags | D2 | In DOC_GOVERNANCE + design-review + DoD |
| D3 Intent playback | D3 | engineering-design + WORKING_WITH_AI / triggers |
| D4 Comment hygiene | D4 | hard-constraints + adapters |
| D4b Branch naming | D4b | same hard-constraints cluster |
| D5 Principle lenses | D5 | skill + DESIGN_PRINCIPLES card (~1 page) |
| D6 Optional | D6 | exemplars on; fresh review deferred |
| D7 Touch list | D7 | this plan’s slices |

Frozen open questions: Quality DoD L2+ required / L1 recommended; fresh code-review skill deferred; English principle card only.

## Implementation Slices

| Slice ID | Summary | Design decision | Dependencies | Verification | Status |
|----------|---------|-----------------|--------------|--------------|--------|
| `TMPL-F05-S01` | Comment + branch hard rules in constraints + adapters | D4, D4b | — | Grep adapters for ban text; no ID-named branch examples as “good” | Done |
| `TMPL-F05-S02` | Quality DoD, red flags, executable plan bar, workflow-dod | D1, D2 | S01 optional | Doc cross-link; DoD skill lists Quality | Done |
| `TMPL-F05-S03` | DESIGN_PRINCIPLES card + engineering-design / design-review / discipline | D3, D5 | — | Card ≤ ~1 page; no SOLID matrix in design-spec | Done |
| `TMPL-F05-S04` | Presets, WORKING_WITH_AI, bootstrap, registry/progress; design Done | D6, D7 | S01–S03 | Acceptance checklist; cross-links | Done |

## Slice → Design Traceability

### TMPL-F05-S01

- **Design decision:** D4, D4b
- **Implementation:** Extend `hard-constraints.mdc`; short mirrors in AGENTS, CLAUDE, BOOTSTRAP, Copilot/Cline/Windsurf; pointer in git-commit-habits
- **Verification:** Rules present; examples match design good/bad lists

### TMPL-F05-S02

- **Design decision:** D1, D2
- **Implementation:** DOC_GOVERNANCE §6 split; workflow-dod updated; implementation-plan.template executable bar
- **Verification:** Quality DoD + red-flag pointer visible from DoD skill

### TMPL-F05-S03

- **Design decision:** D3, D5
- **Implementation:** New `DESIGN_PRINCIPLES.md`; extend engineering-design + design-review; implementation-discipline; one-liner in design-spec template; templates README
- **Verification:** Domain-neutral; anti-abuse present; exemplars in principle card

### TMPL-F05-S04

- **Design decision:** D6, D7 + docs sync
- **Implementation:** WORKING_WITH_AI + workflow triggers (intent playback, challenge shell); presets note; ACTIVE_WORK / registry / progress; mark design+plan Done
- **Verification:** Feature Done; ACTIVE next action clear

## Integration Points

- Modules / APIs touched: docs/ai templates, `.cursor/rules`, `.opencode/skills`, AGENTS/CLAUDE/adapters
- Data contracts: none (docs only)
- Feature flags / rollout hooks: none

## Risks / Mitigations

- Risk: SOLID becomes empty checklist — Mitigation: anti-abuse + no mandatory matrix
- Risk: Adapter bloat — Mitigation: short bullets pointing at hard-constraints / DESIGN_PRINCIPLES

## Verification per Slice

Docs-only bar: cross-link review + domain-neutrality scan + exemplar presence.

## Migration / Compatibility

- No runtime migration
- New Quality DoD applies to new L2+ work

## Deferred Work

| Item | Why deferred | Unblock condition |
|------|--------------|-------------------|
| Fresh-context code-review skill | Explicitly deferred in design-review | New feature when needed |
| ZH principle card | English-first | Profile `docs_language: zh` demand |

## Completion Criteria

- [x] All in-scope slices Done or explicitly Deferred with note
- [x] Design acceptance criteria covered or mapped to deferred work
- [x] Docs DoD + engineering DoD + Quality DoD satisfied
- [x] Ready to propose prepare commit

## Blocked/Deferred note (required if applicable)

Not applicable because no blockers at plan start.
