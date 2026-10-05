# TMPL-F04 Engineering Design Workflow Design Spec

## Meta
- **ID:** `TMPL-F04`
- **Type:** `Feature`
- **Status:** `Done`
- **Owner:** Max
- **Last updated:** `2026-09-22`
- **Related:** [IMPLEMENTATION](./TMPL-F04_ENGINEERING_DESIGN_WORKFLOW_IMPLEMENTATION.md), [DOC_GOVERNANCE](../templates/DOC_GOVERNANCE.md), [WORKFLOW_PRESETS](../templates/WORKFLOW_PRESETS.md)

## TL;DR

Strengthen the portable workflow with domain-neutral engineering design capability: discovery before invention, responsibility/boundary reasoning, design review, implementation readiness gate, and complexity-scaled ceremony. Keep existing commit/trust/profile gates; do not create a parallel bureaucracy.

## Problem

Current workflow is strong on collaboration discipline (IDs, trust tiers, commit gate, profile) but weak on **system design quality before coding**. Agents can skip understanding existing architecture, confuse proposed solutions with requirements, and start implementation with ambiguous ownership/state/failure behavior.

## Requirements

- Agents inspect existing architecture before designing non-trivial work
- Separate requirements / constraints / preferences / assumptions / proposed solutions
- Define responsibilities, boundaries, dependencies, and (when relevant) ownership/lifetime/state/failure
- Compare meaningful alternatives and check overengineering
- Independent design review focused on implementation readiness
- Complexity levels so trivial work is not slowed down
- Domain-neutral core rules and templates
- Integrate with existing profile presets without conflict

## Constraints

- Must embed into existing workflow, not replace it
- One concept → one authoritative source (skills + DOC_GOVERNANCE); adapters reference
- Non-negotiable gates remain: prepare≠execute commit, planning trust tiers, Draft≠large coding
- No game-engine-specific vocabulary in core workflow assets

## Preferences

- Prefer extending/reuse over parallel abstractions
- Prefer simplest architecture that meets known requirements
- Prefer short N/A notes over forced empty sections

## Assumptions

- Target agents can follow skills referenced from AGENTS / CLAUDE / Cursor triggers / opencode
- Deployed repos already use Feature registration for substantial work

## Non-Goals

- Language-specific architecture frameworks
- Mandatory full design template for typo/one-line fixes
- Replacing code review with design review
- Auto-generating design docs without reading code

## Current Architecture

Existing strengths:
- Feature registry + design/impl templates
- Profile presets (strictness/autonomy/role)
- Workflow triggers and DoD
- Implementation discipline (optional)

Gaps:
- No dedicated engineering-design skill
- No design-review skill
- Design template lacks structured design reasoning sections
- Implementation plan lacks design traceability
- No explicit complexity levels or readiness gate

## Proposed Architecture

```text
Request
  → Discovery (existing system + problem framing)
  → Complexity Assessment (L0–L3)
  → Design (engineering-design skill; depth by level)
  → Design Review (design-review skill; L2+/L3)
  → Implementation Readiness gate
  → Implementation Plan (traceable slices)
  → Implementation
  → Verification / DoD
```

Authority map:
- **Behavior authority:** `.opencode/skills/engineering-design/SKILL.md`, `.opencode/skills/design-review/SKILL.md`
- **Process authority:** `docs/ai/templates/DOC_GOVERNANCE.md` (complexity + readiness)
- **Artifact shape:** design-spec / implementation-plan templates
- **Adapters:** AGENTS.md, CLAUDE.md, Cursor triggers, presets — thin references only

## Responsibilities

| Module | Owns |
|--------|------|
| `engineering-design` skill | How to discover, frame, and produce implementation-ready design reasoning |
| `design-review` skill | How to challenge a design for gaps before coding |
| `DOC_GOVERNANCE` | When design/review/readiness is required by complexity + profile |
| Design template | Sections agents fill (with N/A allowed) |
| Implementation template | Traceability from design decisions to slices |
| Profile presets | How strict each posture is about requiring review/readiness |

## Boundaries

- Design review ≠ code review
- Profile cannot disable readiness for Level 3 architectural work that changes public contracts / lifecycle / migration
- Skills must not duplicate commit-gate / trust-tier rules

## Design Complexity Levels

| Level | Examples | Required artifacts |
|-------|----------|--------------------|
| L0 Trivial | typo, one-line fix, local constant | none beyond normal verify |
| L1 Local | single-module logic | short design note optional; register Feature if substantial |
| L2 Feature | multi-module, API, state, lifetime | Design Spec + Design Review + Implementation Plan |
| L3 Architectural | core abstraction, cross-module deps, persistence, concurrency, public API, migration, major refactor | Full Design + Design Review + Readiness gate + Implementation Plan |

## Alternatives & Trade-offs

### Option A (selected): Skills + governance sections + template upgrade

- Pros: embeddable, reusable across agents, complexity-scaled
- Cons: agents must actually invoke skills

### Option B: Only enlarge design template

- Rejected: templates without behavioral skills become ignored checklists

## Integration Impact

- Updates AGENTS/CLAUDE/triggers/presets/DoD/feature-registration
- Adds two opencode skills
- Preserves TMPL-F02 profile system; extends preset effects for design ceremony

## Verification Strategy

- Doc consistency review (links, ALL-CAPS naming, domain bucket)
- Domain-neutrality search for engine-specific terms in core assets
- Acceptance Qs from the enhancement brief answered in Progress Log / PR
- Manual walkthrough: L0 skip vs L2/L3 gate behavior described in governance

## Implementation Readiness

- [x] Requirements and constraints captured
- [x] Authority map defined
- [x] Complexity levels defined
- [x] Domain neutrality required
- [x] Skills and templates landed
- [x] Adapters wired

## Acceptance Checklist

- [x] engineering-design + design-review skills exist
- [x] Design/Implementation templates enhanced
- [x] DOC_GOVERNANCE has complexity + readiness gate
- [x] Presets describe design ceremony differences
- [x] Adapters reference the flow without duplicating full text
- [x] Domain-neutral check passes
- [x] Progress + registry updated
