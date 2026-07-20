# Working With AI

Last updated: YYYY-MM-DD

## Session start prompt

Suggested prompt:

```text
Continue this repo. First read docs/ai/PROJECT_CONTEXT.md, docs/ai/PROGRESS_LOG.md, and docs/ai/ACTIVE_WORK.md. Summarize current state and propose next step.
```

## Session end prompt

Suggested prompt:

```text
Please append today's work to docs/ai/PROGRESS_LOG.md and provide the first action for the next session.
```

## Workflow habits

- For substantial new work: register Feature ID before large code edits.
- For architecture or scope decisions: create/update a Design Spec and, if needed, an ADR.
- For cross-module defects found during another task: file a bug record before broad drive-by fixes.
- For handoff: create a session note, update progress log, and mark incomplete slice status clearly.
- For commits: prepare draft first; execute only with explicit user approval.
