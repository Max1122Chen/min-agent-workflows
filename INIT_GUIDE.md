# Initialization Guide

Use this guide to adapt this template to any new repository.

## 1) Choose your mode

- **Core only (agent-agnostic):** keep `docs/ai/`, delete `.cursor/`
- **Core + Cursor layer:** keep both `docs/ai/` and `.cursor/rules/`

## 2) Fill project metadata

Edit:
- `docs/ai/PROJECT_CONTEXT.md`
- `docs/ai/BOOTSTRAP_DIGEST.md`
- `docs/ai/WORKING_WITH_AI.md`

Required customization:
- project mission
- architecture summary
- verify/test commands
- owner and collaboration language preferences

## 3) Define domain vocabulary

In your governance docs, define domain codes used by IDs:
- examples: `CORE`, `API`, `UI`, `DATA`, `TEST`, `INFRA`
- keep them short and stable

Then register your first feature in `docs/ai/FEATURE_REGISTRY.md`.

## 4) Pick documentation topology

- **Single-track mode:** one docs system for product + implementation
- **Dual-track mode:** product truth in another doc tree, implementation workflow in `docs/ai/`

If dual-track, record the product-truth path in `PROJECT_CONTEXT.md` and repeat it in `WORKING_WITH_AI.md`.

## 5) Set planning trust defaults

Confirm these are treated as high trust:
- `ACTIVE_WORK.md`
- `FEATURE_REGISTRY.md`
- `TECH_DEBT.md`
- recent `PROGRESS_LOG.md`
- code/tests/verify

Mark old plans and snapshots as reference-only.

## 6) Enable/disable optional discipline

- Keep `.cursor/rules/implementation-discipline.mdc` only if the repo benefits from stricter cleanup/refactor rules.
- Remove or adjust any rule that conflicts with your team process.

## 7) First bootstrap check

Run a dry bootstrap prompt:

```text
Read docs/ai/PROJECT_CONTEXT.md, ACTIVE_WORK.md, FEATURE_REGISTRY.md, TECH_DEBT.md, and recent PROGRESS_LOG.md. Summarize current state and propose one next step with verification command.
```

If the answer references stale roadmap docs as backlog, refine your trust-tier rule and README guidance.

## 8) Minimum operating loop

1. Register Feature
2. Design/Plan
3. Implement by slices
4. Verify
5. Update progress and registry
6. Prepare commit (draft first, execute only with explicit approval)
