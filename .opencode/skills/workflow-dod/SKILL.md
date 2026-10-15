---
name: workflow-dod
description: Verify Process and Quality Definition of Done after a meaningful batch. Check docs sync, evidence-based verification, comment/branch ID hygiene, and shell-product red flags before proposing a commit.
---

# Workflow: Definition of Done (DoD) Check

## When to Use

After completing a meaningful batch of work, before proposing "prepare commit".

Authority: `docs/ai/templates/DOC_GOVERNANCE.md` §6.

## Process DoD (Docs)

- [ ] Progress entry appended to `docs/ai/PROGRESS_LOG.md`
- [ ] Feature and slice status synchronized in `docs/ai/FEATURE_REGISTRY.md`
- [ ] Design/Plan updated when scope or status changed
- [ ] For L2+: design review verdict recorded; slices trace to design decisions
- [ ] ADR updated for meaningful architectural trade-off
- [ ] Bug record updated for defect fixes
- [ ] New design/impl docs follow ALL-CAPS Feature-ID naming and domain bucketing

## Process DoD (Engineering bookkeeping)

- [ ] Verification **command + result** recorded (per profile `verification_bar`) — not “verified” alone
- [ ] No unrecorded blocking defect discovered during work
- [ ] Public API changes reflected in callers or explicitly documented
- [ ] Implementation matches reviewed design decisions (or documents approved deviation)
- [ ] Touched source comments contain no Feature / Slice / Bug / ADR IDs
- [ ] If branch created/renamed: `feat/<topic>[/<subtopic>]` (or fix/… topic form) — never ID-based names

## Quality DoD

Required for L2+ before Done; recommended for L1.

- [ ] Design (if required): fresh implementer could plan without chat; no critical TBD on needed ownership/API/failure
- [ ] Plan (if required): paths + observable acceptance + verification signal; no empty steps
- [ ] No shell-product red flag left unaddressed (see DOC_GOVERNANCE §6.3), unless explicitly deferred

## After DoD Passes

- Propose "prepare commit" (draft message only, do not execute commit)
- Do not start unrelated new feature work unless explicitly requested
