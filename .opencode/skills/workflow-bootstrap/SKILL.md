---
name: workflow-bootstrap
description: Recover collaboration context at session start. Load project context, recent progress, active work, and feature registry to get oriented. Use when starting a new session or when context may be stale.
---

# Workflow: Session Bootstrap

## Read Order

1. `docs/ai/PROJECT_CONTEXT.md` — stable project snapshot
2. `docs/ai/PROGRESS_LOG.md` (recent entries only)
3. `docs/ai/ACTIVE_WORK.md` — current short backlog
4. `docs/ai/FEATURE_REGISTRY.md` (In Progress / Planned)
5. `docs/ai/TECH_DEBT.md` (Open)
6. Task-specific design doc (if linked by ACTIVE_WORK or explicitly named by user)

## Output

After reading, produce a summary covering:
- Current project phase and milestone
- Active feature/slice being worked on
- Last verification state
- First concrete next action with verification command

## When to Use

- Starting a new agent session
- Context has become stale (long idle, many external changes)
- User explicitly asks "where were we?"
