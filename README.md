# min-agent-workflows

Portable workflow template for agent-assisted software development.

It turns the collaboration habits refined in personal projects into a reusable structure you can copy into any repo: trusted planning sources, feature/slice IDs, DoD, handoff, and commit gates.

## Design

- **Core layer (agent-agnostic):** `docs/ai/` — docs, IDs, trust tiers, Done Definition, handoff process
- **Adapter layers (optional, per-agent):** rule/config files that enforce the same discipline in each agent

### Supported Agents

| Agent | Adapter File | Status |
|-------|-------------|--------|
| Any agent | `docs/ai/` (core, agent-agnostic) | ✅ Always active |
| **opencode** | `AGENTS.md` + `opencode.json` + `.opencode/skills/` | ✅ |
| **Cursor** | `.cursor/rules/` | ✅ |
| **Claude Code** | `CLAUDE.md` | ✅ |
| **GitHub Copilot** | `.github/copilot-instructions.md` | ✅ |
| **Cline** | `.clinerules` | ✅ |
| **Windsurf** | `.windsurfrules` | ✅ |

You can use the core alone with any agent, or keep the agent-specific adapters you need.

## What it solves

- Stops agents from treating old roadmaps or snapshot docs as backlog
- Makes planning sources explicit: `ACTIVE_WORK`, `FEATURE_REGISTRY`, `TECH_DEBT`, recent `PROGRESS_LOG`, plus code/tests
- Standardizes Feature / Slice / Bug / ADR IDs
- Separates **prepare commit** (draft) from **execute commit** (explicit approval)
- Makes session recovery and handoff reliable

## Repository layout

```text
docs/ai/                 Collaboration truth and workflow records (agent-agnostic)
docs/ai/WORKFLOW_PROFILE.md   Deploy-time posture (presets / autonomy / role)
docs/ai/templates/       Design, plan, ADR, bug, session, preset templates
AGENTS.md                opencode rules
opencode.json            opencode project config
.opencode/skills/        opencode reusable skills
CLAUDE.md                Claude Code rules
.github/copilot-instructions.md   GitHub Copilot instructions
.clinerules              Cline rules
.windsurfrules           Windsurf rules
.cursor/rules/           Optional Cursor enforcement layer
INIT_GUIDE.md            How to initialize this template in a new repo
```

## Quick start

1. Read [`INIT_GUIDE.md`](INIT_GUIDE.md).
2. **Configure workflow profile** (or skip to defaults): see [`docs/ai/WORKFLOW_PROFILE.md`](docs/ai/WORKFLOW_PROFILE.md) and [`docs/ai/templates/WORKFLOW_PRESETS.md`](docs/ai/templates/WORKFLOW_PRESETS.md).
3. Fill project metadata in [`docs/ai/PROJECT_CONTEXT.md`](docs/ai/PROJECT_CONTEXT.md).
4. Define domain codes and verification commands.
5. Keep or remove adapter layers based on which agents you use.

### First-deploy meta-question (for agents)

If `docs/ai/WORKFLOW_PROFILE.md` status is `unconfigured`, ask once:

> This template includes recommended workflow presets (strictness, autonomy, agent role, docs language). Configure now, skip to `serious-engineering` defaults, or defer until later?

Do not force a long questionnaire unless the user chooses **configure now**.

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
