---
name: workflow-feature-registration
description: Register a new Feature ID before implementation work. Follow the ID scheme and create or update design/plan docs. Use when starting a new feature or refactor.
---

# Workflow: Feature Registration

## Steps

1. **Check existing registry** — read `docs/ai/FEATURE_REGISTRY.md` for the next available number in the target domain
2. **Assign Feature ID** — `<DOMAIN>-F<nn>` (e.g. `CORE-F01`, `API-F02`)
3. **Register in FEATURE_REGISTRY.md** — add row with Feature ID, Title, Domain, Status (Draft), Design Doc link (TBD), Owner
4. **Create Design Spec** — copy `docs/ai/templates/design-spec.template.md` to:
   `docs/ai/<DOMAIN>/<FEATURE_ID>_<SLUG>_DESIGN.md` (ALL CAPS filename; domain bucket required)
5. **When ready for implementation** — create:
   `docs/ai/<DOMAIN>/<FEATURE_ID>_<SLUG>_IMPLEMENTATION.md` with slice breakdown
   (same ALL-CAPS + domain-bucket rules)

## Slice IDs

- `<FeatureID>-S<nn>` (e.g. `CORE-F01-S01`)
- Each slice should be independently verifiable

## Status Guidance

- Draft: concept exists, not implementation-ready
- Planned: approved for implementation
- In Progress: active development
- Review: awaiting validation/review
- Done: accepted
- Blocked / Deferred / Cancelled: include reason and follow-up condition
