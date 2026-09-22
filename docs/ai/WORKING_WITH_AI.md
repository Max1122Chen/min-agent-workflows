# Working With AI

Last updated: 2026-09-22

## First deploy / unconfigured profile

If `docs/ai/WORKFLOW_PROFILE.md` is `unconfigured`, ask the meta-question once (see `templates/WORKFLOW_PRESETS.md`). Do not start a long questionnaire unless the user chooses **configure now**.

Suggested opener:

```text
This repo includes workflow presets that set agent strictness, autonomy, role, and docs language.
Configure now, skip to serious-engineering defaults, or defer?
```

## Session start prompt

Suggested prompt:

```text
Continue this repo. First read docs/ai/WORKFLOW_PROFILE.md, PROJECT_CONTEXT.md, PROGRESS_LOG.md, and ACTIVE_WORK.md. Summarize posture + current state and propose next step.
```

## Session end prompt

Suggested prompt:

```text
Please append today's work to docs/ai/PROGRESS_LOG.md and provide the first action for the next session.
```

## Reconfigure

```text
reconfigure workflow
```

## Design / review prompts

```text
Assess complexity (L0–L3). If L2+, run engineering-design then design-review before coding.
```

```text
Review this Design Spec for implementation readiness. Do not start large implementation if Not ready.
```

## Workflow habits

- For substantial new work: register Feature ID before large code edits.
- Assess complexity; keep L0 trivial work lightweight.
- For L2+/L3: Design Spec → Design Review → readiness → Implementation Plan with design traceability.
- Separate requirements from proposed solutions; inspect existing architecture first.
- For architecture or scope decisions: create/update a Design Spec and, if needed, an ADR.
- For cross-module defects found during another task: file a bug record before broad drive-by fixes.
- For handoff: create a session note, update progress log, and mark incomplete slice status clearly.
- For commits: prepare draft first; execute only with explicit user approval.
- Honor `WORKFLOW_PROFILE.md` Effective behavior for challenge level, autonomy pauses, language, and verification bar.
