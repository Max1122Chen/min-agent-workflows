---
name: workflow-dod
description: Verify Definition of Done after completing a meaningful batch of work. Check docs, engineering, and handoff requirements before proposing a commit.
---

# Workflow: Definition of Done (DoD) Check

## When to Use

After completing a meaningful batch of work, before proposing "prepare commit".

## Docs DoD

- [ ] Progress entry appended to `docs/ai/PROGRESS_LOG.md`
- [ ] Feature and slice status synchronized in `docs/ai/FEATURE_REGISTRY.md`
- [ ] Design/Plan updated when scope or status changed
- [ ] ADR updated for meaningful architectural trade-off
- [ ] Bug record updated for defect fixes

## Engineering DoD

- [ ] Verification command executed and recorded
- [ ] No unrecorded blocking defect discovered during work
- [ ] Public API changes reflected in callers or explicitly documented

## After DoD Passes

- Propose "prepare commit" (draft message only, do not execute commit)
- Do not start unrelated new feature work unless explicitly requested
