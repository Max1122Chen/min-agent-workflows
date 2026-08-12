# Feature Registry

Register every new Feature ID before implementation planning.

| Feature ID | Title | Domain | Status | Design Doc | Implementation Plan | Owner | Notes |
|------------|-------|--------|--------|------------|---------------------|-------|-------|
| `TMPL-F01` | Multi-agent generalization | TMPL | Done | — | — | Max | Add opencode, Claude Code, Copilot, Cline, Windsurf adapter layers |
| `TMPL-F02` | Workflow profile init wizard | TMPL | Done | [design](./TMPL/TMPL-F02_WORKFLOW_PROFILE_DESIGN.md) | [plan](./TMPL/TMPL-F02_WORKFLOW_PROFILE_IMPLEMENTATION.md) | Max | Meta-question + presets → WORKFLOW_PROFILE |
| `TMPL-F03` | Doc naming and domain bucketing | TMPL | Done | [design](./TMPL/TMPL-F03_DOC_NAMING_AND_BUCKETING_DESIGN.md) | — | Max | ALL-CAPS Feature-ID filenames; design docs under `docs/ai/<DOMAIN>/` |

## Status guidance

- Draft: concept exists, not implementation-ready
- Planned: approved for implementation
- In Progress: active development
- Review: awaiting validation/review
- Done: accepted
- Blocked / Deferred / Cancelled: include reason and follow-up condition in related docs
