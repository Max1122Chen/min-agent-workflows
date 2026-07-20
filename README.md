# min-agent-workflows

Portable workflow template for agent-assisted software development.

It turns the collaboration habits refined in personal projects into a reusable structure you can copy into any repo: trusted planning sources, feature/slice IDs, DoD, handoff, and commit gates.

## Design

- **Core layer (agent-agnostic):** docs, IDs, trust tiers, Done Definition, handoff process under `docs/ai/`
- **Cursor layer (optional):** `.cursor/rules` policies that enforce the same discipline in Cursor

You can use the core alone with any agent, or keep the Cursor layer when working in Cursor.

## What it solves

- Stops agents from treating old roadmaps or snapshot docs as backlog
- Makes planning sources explicit: `ACTIVE_WORK`, `FEATURE_REGISTRY`, `TECH_DEBT`, recent `PROGRESS_LOG`, plus code/tests
- Standardizes Feature / Slice / Bug / ADR IDs
- Separates **prepare commit** (draft) from **execute commit** (explicit approval)
- Makes session recovery and handoff reliable

## Repository layout

```text
docs/ai/                 Collaboration truth and workflow records
docs/ai/templates/       Design, plan, ADR, bug, session templates
.cursor/rules/           Optional Cursor enforcement layer
INIT_GUIDE.md            How to initialize this template in a new repo
```

## Quick start

1. Read [`INIT_GUIDE.md`](INIT_GUIDE.md).
2. Fill project metadata in [`docs/ai/PROJECT_CONTEXT.md`](docs/ai/PROJECT_CONTEXT.md).
3. Define domain codes and verification commands.
4. Choose single-track or dual-track documentation mode.
5. Keep `.cursor/rules/` if you use Cursor; remove it otherwise.

## Core operating loop

1. Register a Feature ID
2. Write Design / Implementation Plan
3. Implement by slices
4. Verify
5. Update progress + registry
6. Prepare commit, then execute only with explicit approval

## Source inspiration

This template generalizes stable patterns from agent collaboration practice in engineering and prototype repos (docs trust tiers, bootstrap digest, registry-first features, and work-boundary commit gates).

## License

Private / personal use unless otherwise noted.
