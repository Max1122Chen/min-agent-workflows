# TMPL-F03 Doc Naming And Domain Bucketing Design Spec

## Meta
- **ID:** `TMPL-F03`
- **Type:** `Feature`
- **Status:** `Done`
- **Owner:** Max
- **Last updated:** `2026-08-12`
- **Related:** [FEATURE_REGISTRY](../FEATURE_REGISTRY.md), [DOC_GOVERNANCE](../templates/DOC_GOVERNANCE.md)

## TL;DR

Tighten collaboration-doc naming: filenames must be ALL CAPS and keyed by Feature ID (same scheme as IDs). Design and implementation docs must live under domain buckets `docs/ai/<DOMAIN>/`, not scattered at `docs/ai/` root.

## Scope

- **In:**
  - Filename pattern for Design / Implementation / related long docs
  - Mandatory domain subfolders for those docs
  - Governance + layout/adapters updates
- **Out:**
  - Renaming third-party or historical docs outside this template
  - Changing core root truth filenames beyond already-uppercase names
  - Automating renames via script

## Design

### Filename pattern (required)

```text
<FEATURE_ID>_<SLUG>_<DOC_TYPE>.md
```

Rules:
- Entire filename is **ALL CAPS** (including slug)
- `<FEATURE_ID>` matches registry ID exactly (e.g. `TMPL-F03`)
- `<SLUG>` is short `A-Z0-9_` description
- `<DOC_TYPE>` is one of: `DESIGN` | `IMPLEMENTATION` | `ROADMAP` | `REFACTOR_PLAN`

Examples:
- `TMPL-F03_DOC_NAMING_AND_BUCKETING_DESIGN.md`
- `CORE-F01_EVENT_BUS_IMPLEMENTATION.md`

### Domain bucketing (required for design/impl)

```text
docs/ai/<DOMAIN>/<FEATURE_ID>_<SLUG>_<DOC_TYPE>.md
```

- `<DOMAIN>` equals the Feature ID domain segment and is ALL CAPS (`TMPL`, `CORE`, …)
- Design Spec and Implementation Plan **must** live in the domain bucket
- Do **not** place long design/implementation docs in `docs/ai/` root

### Root exceptions (stay at `docs/ai/`)

Core collaboration truth only, e.g.:
`WORKFLOW_PROFILE.md`, `PROJECT_CONTEXT.md`, `BOOTSTRAP_DIGEST.md`, `ACTIVE_WORK.md`, `FEATURE_REGISTRY.md`, `PROGRESS_LOG.md`, `TECH_DEBT.md`, `WORKING_WITH_AI.md`, `README.md`

### Other placements

| Kind | Location | Naming |
|------|----------|--------|
| Templates | `docs/ai/templates/` | keep `*.template.md` / governance names |
| Session notes | `docs/ai/sessions/` | `YYYY-MM-DD-<topic>.md` allowed lowercase topic |
| Bugs | `docs/ai/bugs/` or `docs/ai/<DOMAIN>/bugs/` | `BUG-<DOMAIN>-<nnn>_<SLUG>.md` (ALL CAPS) |
| ADR | `docs/ai/<DOMAIN>/` | `ADR-<yyyyMMdd>-<nn>_<SLUG>.md` (ALL CAPS) |

## Verification

- Governance and layout rules state the pattern explicitly
- Existing TMPL docs already match; new TMPL-F03 design follows the pattern
- Adapters mention domain bucketing + ALL-CAPS Feature-ID filenames

## Acceptance checklist

- [x] Feature registered
- [x] DOC_GOVERNANCE + docs-ai-layout updated
- [x] Adapters / README / INIT synced
- [x] Progress updated
