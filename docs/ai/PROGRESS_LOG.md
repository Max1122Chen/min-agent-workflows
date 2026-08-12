# Progress Log

Append-only chronological project record.

## 2026-08-12

- Scope: `TMPL-F03` / `TMPL-F03-S01`
- Completed:
  - Tightened doc naming: ALL-CAPS `<FEATURE_ID>_<SLUG>_<DOC_TYPE>.md`
  - Required domain bucketing for design/impl/roadmap/ADR under `docs/ai/<DOMAIN>/`
  - Updated `DOC_GOVERNANCE`, `docs-ai-layout`, adapters, templates, INIT_GUIDE, docs index
  - Added `docs/ai/TMPL/TMPL-F03_DOC_NAMING_AND_BUCKETING_DESIGN.md`
- Verification:
  - Existing TMPL-F02 docs already matched the pattern
  - New TMPL-F03 design path/name complies
- Docs updated:
  - `FEATURE_REGISTRY.md`, `ACTIVE_WORK.md`, `PROGRESS_LOG.md`
- Next action:
  - Prepare commit when user requests

## 2026-08-07

- Scope: `TMPL-F02` / `TMPL-F02-S01..S03`
- Completed:
  - Added `docs/ai/WORKFLOW_PROFILE.md` with status machine (`unconfigured` / `configured` / `deferred` / `default-applied`)
  - Added `docs/ai/templates/WORKFLOW_PRESETS.md` (meta-question, 4 presets, dimension→effect map, apply algorithm)
  - Wrote design + implementation docs under `docs/ai/TMPL/`
  - Wired README, INIT_GUIDE, BOOTSTRAP_DIGEST, WORKING_WITH_AI, DOC_GOVERNANCE, docs index
  - Wired adapters: AGENTS.md, CLAUDE.md, Cursor rules, opencode bootstrap skill + `opencode.json`, Cline/Windsurf/Copilot
- Verification:
  - Doc review of preset mapping and adapter read-order consistency
  - Confirmed profile gate appears in bootstrap paths
- Docs updated:
  - `FEATURE_REGISTRY.md`, `ACTIVE_WORK.md`, `PROGRESS_LOG.md`, design/plan acceptance
- Next action:
  - Prepare commit for TMPL-F02 when user requests

## 2026-07-23

- Scope: `TMPL-F01`
- Completed:
  - Created `AGENTS.md` — translated `.cursor/rules/` hard constraints, trust tiers, workflow triggers, doc layout into opencode format
  - Created `opencode.json` — project config with instructions referencing core docs, plus bootstrap/handoff/register-feature commands
  - Created `.opencode/skills/` — 4 workflow skills (bootstrap, handoff, feature-registration, dod) + 3 code-style skills (c-style, cpp-style, git-commit-habits)
  - Created cross-agent adapter files: `CLAUDE.md`, `.github/copilot-instructions.md`, `.clinerules`, `.windsurfrules`
  - Updated `README.md` — added agent support matrix and repo layout
  - Updated `INIT_GUIDE.md` — added agent adapter selection as first init step
  - Synced user's global Cursor skills (c-style, cpp-style, git-commit-habits) to `~/.config/opencode/skills/`
- Verification:
  - `git status` — all expected files present
  - `git diff --stat` — README.md (29 insertions), INIT_GUIDE.md (19 insertions)
- Docs updated:
  - `FEATURE_REGISTRY.md` — registered `TMPL-F01`
  - `ACTIVE_WORK.md` — marked `TMPL-F01` as Done
  - `PROGRESS_LOG.md` — this entry
- Next action:
  - Review the prepared commit draft, then execute `git add` + `git commit`
