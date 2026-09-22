# Workflow Profile

Last updated: YYYY-MM-DD  
Status: `unconfigured`  
<!-- Allowed status: unconfigured | configured | deferred | default-applied -->

This file is the **single runtime truth** for collaboration posture in a deployed repo.  
Agents must read it during bootstrap. If `status` is `unconfigured`, ask the meta-question once before large work.

## Meta-question (ask once when unconfigured)

> This template includes recommended workflow presets. Configuring them sets how strict the agent is, how often it asks before acting, what role it plays, and which language docs use.
>
> Do you want to configure now?
> 1. **configure now** — pick a preset (or answer a few dimensions)
> 2. **skip** — apply `serious-engineering` defaults and continue
> 3. **later** — mark deferred; do not ask again until user says `reconfigure workflow`

## Current selection

| Field | Value |
|-------|-------|
| `preset_id` | `<unset \| learning-mentor \| prototype-partner \| serious-engineering \| executor-tight \| custom>` |
| `repo_posture` | `<learning \| prototype \| serious-engineering \| commercial>` |
| `autonomy` | `<ask-first \| propose-then-act \| act-within-slice>` |
| `agent_role` | `<mentor \| partner \| advisor \| executor>` |
| `docs_language` | `<en \| zh \| bilingual>` |
| `docs_topology` | `<single-track \| dual-track>` |
| `verification_bar` | `<docs-only \| smoke-required \| tests-required>` |
| `implementation_discipline` | `<on \| off>` |
| `product_truth_path` | `<n/a \| path/to/product/docs>` |

## Effective behavior (derived)

Fill after configure/skip. Keep short and actionable.

- Challenge skipped workflow: `<low | medium | high>`
- Pre-flight before large feature/refactor: `<optional | recommended | required>`
- Pause for approval when: `<...>`
- Default explanation depth: `<minimal | normal | teaching>`
- New docs/progress language: `<en | zh | bilingual>`
- Engineering DoD bar: `<...>`

## Non-negotiable constraints (never disabled by profile)

- Prepare commit ≠ execute commit
- Plan only from trusted sources (`ACTIVE_WORK`, registry In Progress/Planned, open TECH_DEBT, recent progress, code/tests)
- `Draft` design does not authorize large-scale coding
- Level-3 architectural safety checks (ownership/contracts/migration/failure when relevant) cannot be skipped by preset

## Reconfigure

User phrase: `reconfigure workflow`  
Agent action: re-run meta-question + preset/dimension flow; update this file; summarize what changed.
