# TMPL-F02 Workflow Profile Design Spec

## Meta
- **ID:** `TMPL-F02`
- **Type:** `Feature`
- **Status:** `Done`
- **Owner:** Max
- **Last updated:** `2026-08-07`
- **Related:** [FEATURE_REGISTRY](../FEATURE_REGISTRY.md), [IMPLEMENTATION](./TMPL-F02_WORKFLOW_PROFILE_IMPLEMENTATION.md), [PRESETS](../templates/WORKFLOW_PRESETS.md)

## TL;DR

Add a deploy-time workflow profile so target repos can customize discipline without long questionnaires. Agents first ask a meta-question; if the user accepts, they pick a named preset (or answer a few hard dimensions). Results land in `docs/ai/WORKFLOW_PROFILE.md` and drive concrete rule behavior.

## Scope

- **In:**
  - Meta-question gate (configure / skip-default / later)
  - Named presets + dimension mapping
  - `WORKFLOW_PROFILE.md` as single runtime truth
  - Adapter/bootstrap triggers that notice missing/unconfigured profile once
  - Reconfigure entry (`reconfigure workflow`)
- **Out:**
  - Auto-generating language-specific full template translations
  - Complex CLI initializer scripts (P2)
  - Overriding hard constraints (commit gate, planning trust tiers)

## Context and problem

Generic template discipline is reusable, but real projects need different strictness, autonomy, and agent stance. Those needs often appear after first deploy. A README-only recommendation is too weak; a long forced questionnaire causes skip/敷衍.

## Design

### Option A (recommended): Meta-question + presets + profile file

1. On init/bootstrap, if profile is missing or `status: unconfigured`, ask meta-question once.
2. User chooses:
   - configure now (pick preset or answer dimensions)
   - skip → write `serious-engineering` defaults
   - later → write `status: deferred` and stop nagging until user asks to reconfigure
3. Persist choices in `WORKFLOW_PROFILE.md`.
4. Agents read profile every session and apply behavior switches.

### Option B: Long questionnaire only

Rejected: high friction, easy to ignore, weak persistence.

### Non-negotiable (profile cannot disable)

- Prepare commit ≠ execute commit
- Planning trust tiers (ACTIVE_WORK / registry / debt / progress / code)
- Draft design does not authorize large-scale coding

### Behavior dimensions

| Dimension | Values | Controls |
|-----------|--------|----------|
| `repo_posture` | learning / prototype / serious-engineering / commercial | Strictness, challenge frequency, pre-flight expectation |
| `autonomy` | ask-first / propose-then-act / act-within-slice | When agent must pause for approval |
| `agent_role` | mentor / partner / advisor / executor | Explanation depth, challenge style |
| `docs_language` | en / zh / bilingual | Default language for new docs/progress |
| `docs_topology` | single-track / dual-track | Whether product truth is separate |
| `verification_bar` | docs-only / smoke-required / tests-required | Slice engineering DoD |
| `implementation_discipline` | on / off | Cleanup/reuse/dead-path strictness |

### Named presets

| Preset ID | Intent |
|-----------|--------|
| `learning-mentor` | Learn by building; explain + challenge foundations |
| `prototype-partner` | Fast validated slices; partner tone; lighter ceremony |
| `serious-engineering` | Default; professional bar; challenge skipped workflow |
| `executor-tight` | Ship approved scope; minimal teaching; high compliance |

## Verification

- Docs review: missing profile triggers meta-question text in README/AGENTS/bootstrap
- Manual: pick each preset and confirm profile fields + expected switches are documented
- No runtime binary verify command in this template repo

## Acceptance checklist

- [x] Design + Implementation Plan registered
- [x] `WORKFLOW_PROFILE.md` exists with clear status machine
- [x] Preset catalog documents option → effect
- [x] Init/bootstrap/adapters mention meta-question gate
- [x] Progress + registry updated
