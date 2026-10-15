# TMPL-F05 Artifact Quality And Design Principles Design Spec

## Meta
- **ID:** `TMPL-F05`
- **Type:** `Feature`
- **Complexity:** `L2`
- **Status:** `Done`
- **Owner:** Max
- **Last updated:** `2026-10-15`
- **Related:** [FEATURE_REGISTRY](../FEATURE_REGISTRY.md), [IMPLEMENTATION](./TMPL-F05_ARTIFACT_QUALITY_AND_DESIGN_PRINCIPLES_IMPLEMENTATION.md), [DOC_GOVERNANCE](../templates/DOC_GOVERNANCE.md), [TMPL-F04 design](./TMPL-F04_ENGINEERING_DESIGN_WORKFLOW_DESIGN.md), [DESIGN_PRINCIPLES](../templates/DESIGN_PRINCIPLES.md), [engineering-design](../../../.opencode/skills/engineering-design/SKILL.md), [design-review](../../../.opencode/skills/design-review/SKILL.md), [workflow-dod](../../../.opencode/skills/workflow-dod/SKILL.md)

## TL;DR

Close the “process shell, weak core” gap: add quality bars and red flags for designs/plans/verification; hard-ban Feature/Slice IDs in source comments **and** in git branch names; require topic-granular `feat/...` branch naming; fold modular design principles (cohesion/coupling, SOLID-shaped lenses, YAGNI) into the existing F04 path—not a parallel methodology.

## Problem

1. **Shell without core.** The template already specifies *what artifacts to produce* (Design Spec, Plan, DoD checklists, IDs, gates). Agents often fill templates and flip statuses while the substance stays vague: untestable acceptance, ceremonial alternatives, plans that still require guessing, “verified” with no command/result.
2. **Missing coding-design norms.** Collaboration rules cover docs and gates well; they do not yet steer day-to-day structure toward high cohesion, low coupling, open-for-extension / closed-for-modification, or related public modular design norms. `engineering-design` already implies much of this (responsibilities, boundaries, simplicity) but does not name or operationalize those lenses for implementers.
3. **ID leakage into comments.** Feature/Slice IDs belong in collaboration docs; putting them in source comments couples code to workflow bookkeeping and replaces real intent comments.
4. **ID leakage into branch names.** Branches named after a single Feature ID (e.g. `feat/core-f01-event-bus`) are ugly, over-coupled to registry bookkeeping, and push agents to open one branch per Feature ID instead of a topic-granular area branch.

## Requirements

### R1 — Artifact quality (process + quality)

- Distinguish **Process DoD** (docs/registry/progress synced) from **Quality DoD** (artifact is usable by a fresh reader/implementer without reconstructing intent from chat).
- Provide **shell-product red flags** agents must treat as failure, not style nits.
- For ambiguous non-trivial requests (typically L1+): require short **intent playback** before registering large design work or coding (user may explicitly skip).
- Implementation plans must be **executable**: concrete paths, observable acceptance, verification command + expected signal; ban empty steps (“handle edge cases”, “add appropriate tests”).
- Declaring done requires **evidence** matching profile `verification_bar` (command + result recorded), not assertion alone.

### R2 — Comment hygiene (hard constraint)

- Source comments (and analogous inline docs in code) **must not** contain Feature / Slice / Bug / ADR IDs.
- Comments explain non-obvious *why*, invariants, hazards, or trade-offs; stay short; remain understandable from surrounding code.
- IDs remain in: registry, ACTIVE_WORK, design/plan/progress/session docs, and commit messages when the project uses them there.

### R3 — Design principles for better code structure

- Agents designing or implementing non-trivial code apply a **small, named set of modular design principles** as judgment aids.
- Principles must **merge into** existing skills/templates/DoD—not a second ceremony track or mandatory “SOLID essay” in every Design Spec.
- Principles apply at design *and* implementation time; design-review and (when enabled) implementation-discipline both check for violations that matter to the change.

### R5 — Git branch naming (hard constraint)

- Feature work uses topic-granular branch names under `feat/` (depth as needed): e.g. `feat/render`, `feat/render/material`, `feat/gameplay`.
- Granularity tracks **product/area topic**, not registry IDs. One long-lived area branch may carry multiple Features/slices when that matches how the team lands work.
- **Forbidden:** naming a branch primarily after a Feature/Slice/Bug/ADR ID, e.g. `feat/core-f01-xxx`, `feat/TMPL-F05`, `feat/core-f01-s02-...`.
- Same spirit as comment hygiene: IDs live in collaboration docs; VCS names describe *what area of the system* is changing.
- Other prefixes (`fix/`, `refactor/`, `chore/`, …) follow the same rule: topic words, not ID strings. Exact prefix set may follow repo convention; the ID ban is universal.

### R6 — Integration & portability

- One concept → one authority; adapters (AGENTS/CLAUDE/Cursor/opencode) only reference.
- Domain-neutral vocabulary; no product-specific architecture religion.
- Profile may tune *how hard* to push (challenge / implementation_discipline / verification_bar); cannot disable: comment ID ban, **branch ID ban**, planning trust tiers, commit gate, L3 safety checks, or Quality DoD existence for L2+ slices.

## Constraints

- Must extend TMPL-F04 design loop, not replace or fork Superpowers-style SDLC.
- Do not vendor or copy large copyrighted texts from books/courses; cite public principle names + short operational rules + reference links.
- Keep L0 trivial work lightweight (no full principle write-up; still obey comment ID ban and branch ID ban when a branch is created).
- Avoid checkbox theater: ticking “followed OCP” without a structural consequence is a Quality DoD fail.

## Preferences

- Prefer **red flags + good/bad exemplars** over long theory chapters.
- Prefer mapping principles onto sections agents already fill (Responsibilities, Boundaries, Dependencies, Simplicity).
- Prefer optional fresh-context review for serious presets; not mandatory for prototype posture.

## Assumptions

- Public principle names (SOLID, cohesion/coupling, YAGNI, DRY) are widely enough known that short operational restatements suffice.
- Deployed repos can keep language-specific style guides separately; this feature covers *structural* design norms, not formatting.

## Non-Goals

- Adopting obra/superpowers wholesale (TDD mandate, worktree ritual, alternate docs tree).
- Language-specific style guides (Google Java Style, clang-format, etc.).
- Requiring every Design Spec to contain a filled “SOLID matrix”.
- Mandatory subagent review on every slice for all presets.
- Forbidding Feature IDs in *collaboration* docs or filenames.
- Mandating a single global branch taxonomy beyond `feat/<topic>[/<subtopic>...]` examples (repos may add `fix/` etc.).

## Current Architecture

Already present and should be extended:

| Asset | Role today | Gap |
|-------|------------|-----|
| `engineering-design` skill | Discovery, responsibilities, boundaries, failure, simplicity | No named modular principles; weak “how good is good enough” |
| `design-review` skill | Ambiguity / readiness | No shell-product / principle red flags |
| `workflow-dod` + DOC_GOVERNANCE §6 | Mostly process completeness | Little substance quality |
| `implementation-discipline` (optional) | Reuse, dead path, debt, API alignment | No cohesion/coupling/OCP guidance |
| `implementation-plan.template` | Traceability skeleton | No executable-step quality bar |
| `hard-constraints` / AGENTS | Commit gate, trust tiers, context recovery | No comment ID ban |
| TMPL-F04 loop | Design → review → readiness → plan | Assumes filling the loop yields quality; often does not |

External reference (inspiration only, not dependency): [obra/superpowers](https://github.com/obra/superpowers) — skill anti-rationalization tables, executable plans, evidence-before-done, fresh-context review. Steal mechanisms; do not import parallel workflow.

## Proposed Architecture

```text
Request
  → Intent playback when ambiguous (short; skippable by user)
  → Discovery + Complexity (existing)
  → Design (engineering-design + design-principle lenses)
  → Design Review (readiness + shell red flags + principle findings)
  → Implementation Plan (executable-slice quality bar)
  → Implement (comment hygiene hard rule; principles via discipline)
  → Verify with evidence
  → Process DoD + Quality DoD
  → prepare commit (existing gate)
```

### Authority map (one concept → one place)

| Concept | Authority | Adapters |
|---------|-----------|----------|
| Comment / ID hygiene | `hard-constraints` (+ short AGENTS/CLAUDE mirror) | Cursor/opencode/others reference |
| Branch naming / ID ban | `hard-constraints` (same cluster as comment hygiene) | git-commit-habits / bootstrap may point; do not duplicate full rules |
| Design principle lenses | `engineering-design` skill § principles | design-review checks; optional short `templates/DESIGN_PRINCIPLES.md` card |
| Shell vs quality / Quality DoD | `DOC_GOVERNANCE` § DoD + `workflow-dod` | WORKING_WITH_AI habits |
| Executable plan bar | `implementation-plan.template` + short plan-quality notes in DOC_GOVERNANCE or skill | — |
| Coding-time cleanup + structure | `implementation-discipline` (when on) | profile `implementation_discipline` |
| Evidence before done | `workflow-dod` / verification notes | profile `verification_bar` |

### D1 — Process DoD vs Quality DoD

Keep Process DoD roughly as today. Add Quality DoD (apply to L1+ meaningful batches; L2+ required before “Done”):

- Design (when required): a fresh implementer could plan without chat history; no critical TBD on ownership/API/failure that the change needs.
- Plan (when required): each in-scope slice has paths + observable acceptance + verification signal; no empty steps.
- Implementation: matches reviewed decisions or records approved deviation; comments obey hygiene rule.
- Verification: evidence recorded per `verification_bar`.
- No shell-product red flag remains unaddressed.

### D2 — Shell-product red flags (reject / rework)

Treat as Quality DoD failures when present without explicit deferral:

| Red flag | Why it is shell |
|----------|-----------------|
| Sections filled with restated headings or “TBD” on critical decisions | Ceremony without decisions |
| Alternatives that are strawmen | Fake trade-off |
| Acceptance that cannot be observed (“more maintainable”, “properly handled”) | Unverifiable |
| Plan steps with no file path or no checkable result | Not executable |
| “Tests/docs updated” with no what/where | Assertion |
| “Followed SOLID/OCP” with no structural consequence named | Principle theater |
| Progress says Done but verification evidence missing | Claim over evidence |

### D3 — Intent playback (lightweight)

When the request is non-trivial and intent/success criteria are incomplete:

1. Playback in ~150–300 words: problem, success, non-goals, key constraints (mark guesses).
2. One clarifying question **or** ask for correction.
3. Only then open/expand Design Spec or large coding.

User phrases like “skip questions / just do it” exit this gate (record assumptions). L0 exempt.

### D4 — Comment hygiene (hard constraint)

Non-negotiable (profile cannot disable):

- **Forbidden in source comments / code-adjacent inline docs:** Feature IDs, Slice IDs, Bug IDs, ADR IDs (e.g. `TMPL-F05`, `TMPL-F05-S01`, `BUG-CORE-001`, `ADR-20261015-01`).
- **Allowed:** collaboration docs, registry, progress, session notes; commit messages if the team uses IDs there.
- **Comment content bar:** explain non-obvious why / invariant / hazard / trade-off; prefer clarity over process bookkeeping; delete comments that only restate the next line of code.

DoD / review: scan touched files for ID-shaped tokens in comments.

### D4b — Branch naming (hard constraint)

Non-negotiable (profile cannot disable):

| Rule | Detail |
|------|--------|
| Shape | `feat/<topic>` or `feat/<topic>/<subtopic>` (further nesting OK when it matches real area structure) |
| Good examples | `feat/render`, `feat/render/material`, `feat/gameplay`, `feat/agent-workflows` |
| Bad examples | `feat/core-f01-event-bus`, `feat/TMPL-F05`, `feat/tmpl-f05-artifact-quality`, `feat/core-f01-s01` |
| Granularity | Name the **area of change**, not one registry row. Prefer continuing an existing matching area branch over opening a new ID-named branch |
| ID placement | Feature/Slice IDs stay in ACTIVE_WORK / registry / design / progress / PR body—not in the branch string |

When creating a branch, agent must choose topic words from the product/module vocabulary (or template domain like `workflows`), never from `<DOMAIN>-F<nn>`.

DoD: if the session created or renamed a branch, name must pass this rule before Done.

### D5 — Design principles: public sources → merged lenses

#### Public sources (cite, do not copy)

Use widely taught, publicly documented principles as *names + operational meaning*. Primary references for implementers:

| Family | Common public anchors | What we take |
|--------|----------------------|--------------|
| Modular structure | Classic cohesion & coupling (e.g. Constantine/Yourdon tradition; taught widely in SE courses); Fowler on reducing coupling via interfaces | High cohesion, low coupling as default structural goals |
| SOLID | Robert C. Martin’s design principles (SOLID acronym popularized later); Meyer’s Open-Closed Principle; public explainers (e.g. university notes, [Wikipedia SOLID](https://en.wikipedia.org/wiki/SOLID)) | Five lenses for OO/modular boundaries—not a religion |
| Simplicity | YAGNI / “simplest that works”; overlaps existing overengineering check | Prefer extension of real need over speculative abstraction |
| Reuse hygiene | DRY as *knowledge* DRY, not clone-every-line | Aligns with implementation-discipline “reuse before duplication” |

**Explicitly out of authority for this feature:** paid book excerpts, full style guides, framework-specific architectures (Clean Architecture folders as mandatory layout, etc.). Deployed repos may add those locally.

#### How principles merge (not a parallel track)

Add one section to `engineering-design` (and a one-page `templates/DESIGN_PRINCIPLES.md` card) mapping principles → **existing design questions**:

| Lens | Operational rule (agent-facing) | Already-covered hook |
|------|----------------------------------|----------------------|
| **High cohesion** | A unit’s parts serve one clear purpose; unrelated reasons-to-change do not share a home | Responsibilities |
| **Low coupling** | Changes in one unit should not force wide unrelated edits; depend on narrow interfaces | Boundaries, Dependencies |
| **SRP** (Single responsibility) | One primary reason to change per unit; split when reasons diverge | Responsibilities “not responsible for” |
| **OCP** (Open-closed) | Prefer extending via existing extension points / new units over editing many closed behaviors; do **not** invent speculative hooks “for OCP” | Prefer reuse/extend; Simplicity check |
| **LSP** (Liskov) | Subtypes / implementations honor the contract callers rely on; no surprising strengthening of preconditions or weakening of postconditions | API / Interface Semantics |
| **ISP** (Interface segregation) | Do not force clients to depend on unused surface; keep interfaces tight | Boundaries, API surface |
| **DIP** (Dependency inversion) | High-level policy should not depend on volatile details; both depend on abstractions *when* indirection is justified by real churn/test needs | Dependencies direction |
| **YAGNI / simplicity** | No speculative generality | § Simplicity / overengineering |
| **DRY (knowledge)** | One authoritative place for a rule/fact; do not dedupe coincidental similarity | implementation-discipline |

#### Anti-abuse rules (critical)

- Principles are **lenses for findings**, not a mandatory matrix in every doc.
- **OCP does not mean** “add interfaces/plugins everywhere.” Speculative extension points fail the simplicity check.
- If the language is not class-OO, apply cohesion/coupling, ISP/DIP *ideas* to modules/packages/functions; skip LSP when no substitution relationship exists.
- design-review may cite a principle in a finding only when it names **concrete structural risk** (e.g. “Parser also owns network I/O — cohesion/SRP”).

### D6 — Optional enhancements (profile-gated)

| Enhancement | Default serious-engineering | Prototype |
|-------------|----------------------------|-----------|
| Fresh-context review after large slice | Recommended | Off |
| Good/bad exemplar snippets in templates | On | On (short) |
| Principle card linked from bootstrap | On | Optional |

Not in MVP: full Superpowers TDD skill; diagnosing-session skill (nice follow-up).

### D7 — Skill / doc touch list (implementation preview)

Expected edits (for later Implementation Plan):

1. `hard-constraints.mdc`, `AGENTS.md`, `CLAUDE.md`, bootstrap digest — comment ID ban + branch naming / branch ID ban
2. `DOC_GOVERNANCE.md` §6 — Process vs Quality DoD + red flags pointer
3. `workflow-dod` skill — dual DoD + evidence + comment/branch scan
4. `engineering-design` skill — principles lenses + intent-playback pointer + anti-shell note
5. `design-review` skill — shell red flags + principle findings format
6. New `docs/ai/templates/DESIGN_PRINCIPLES.md` — one-page card + reference links
7. `implementation-plan.template.md` — executable-slice quality bar
8. `implementation-discipline.mdc` + AGENTS discipline section — cohesion/coupling/OCP/YAGNI at code time
9. `design-spec.template.md` — optional one-liner under Responsibilities/Boundaries pointing at principle card (no new mandatory SOLID section)
10. Presets / WORKING_WITH_AI — when Quality DoD applies; challenge shell products
11. Good/bad micro-examples (design + plan + comment + branch) in template README or principle card
12. `git-commit-habits` (optional pointer only) — do not invent ID-based branch names when suggesting branch/PR flow

## Responsibilities

| Unit | Responsible for | Not responsible for |
|------|-----------------|---------------------|
| `engineering-design` skill | How to design; principle lenses; anti-shell design habits | Code style formatting |
| `design-review` skill | Catch shell + structural principle failures before coding | Implementing fixes |
| `DESIGN_PRINCIPLES.md` | Short card + citations | Workflow gates |
| `DOC_GOVERNANCE` / `workflow-dod` | When Done is allowed; Quality DoD | Teaching full SE theory |
| `hard-constraints` | Comment ID ban; branch topic naming + branch ID ban | Full git branching strategy / release trains |
| `implementation-discipline` | Coding-time structure hygiene when enabled | Forcing refactors outside task touch set |
| Adapters | Pointers only | Duplicate full text of principles |

## Boundaries

- Allowed: extend F04 artifacts; add one principle card under `templates/`.
- Forbidden: second design methodology tree; requiring Superpowers install; putting Feature IDs into code comments or branch names as “traceability”.

## Dependencies

- Depends on: TMPL-F04 design loop, profile/DoD machinery, existing skills.
- Depended on by: future template hardenings; deployed repos that opt into stricter engineering posture.
- New dependency direction justified because: quality failure mode is already visible in F04 outcomes; principles are the missing *code structure* vocabulary that F04’s design questions were aiming at.

## Ownership & Lifetime

Not applicable because this feature is documentation/skills governance; no runtime state.

## Data Flow

`User intent → (playback) → Design artifact → Review findings → Plan slices → Code + comments → Verification evidence → DoD (process + quality) → Commit prep`

## Control Flow

Agent-driven; design-review remains a distinct step for L2+. Optional fresh review is a subagent/callout, not a new status in FEATURE_REGISTRY.

## State & Invariants

- Design Status `Draft` ⇒ no large coding (existing).
- Quality DoD fail ⇒ slice not Done (new).
- Comment ID ban always active (new invariant).
- Branch ID ban always active when creating/renaming branches (new invariant).

## API / Interface Semantics

Not applicable because no programmatic API; skill frontmatter `description` fields must mention triggers (quality/shell, principles, comment hygiene) so harnesses surface them.

## Failure Model

| Failure | Expected behavior |
|---------|-------------------|
| Agent produces shell Design/Plan | design-review / Quality DoD → Not ready / rework; list concrete gaps |
| Agent cites OCP to add unused abstractions | simplicity + anti-abuse → reject; prefer YAGNI |
| Agent puts Feature ID in comment | hard constraint violation; fix before Done |
| Agent creates `feat/<domain>-f<nn>-...` branch | hard constraint violation; rename to topic branch before Done |
| User skips playback | proceed with recorded assumptions |
| Profile tries to disable comment/branch ID ban | ignore; non-negotiable |

## Alternatives & Trade-offs

### Option A (recommended) — Merge principles into F04 path + Quality DoD + hard comment rule

- Summary: Extend existing skills/DoD; one principle card; no parallel SDLC.
- Pros: Fits template philosophy; reduces shell risk; principles reinforce sections agents already write; low ceremony for L0.
- Cons: Requires careful anti-theater wording so SOLID does not become a new empty checklist.

### Option B — Adopt Superpowers (or large subset) as the quality engine

- Summary: Install/port brainstorming, writing-plans, TDD, subagent review as primary loop.
- Pros: Battle-tested skill behaviors.
- Cons: Dual workflow, different docs paths, conflicts with commit gate and Feature-ID collaboration model; heavy for a portable template.

### Option C — Principles-only doc, no Quality DoD

- Summary: Add SOLID/cohesion markdown only.
- Pros: Small diff.
- Cons: Does not fix shell-without-core; principles likely become unread wallpaper.

**Choice:** Option A.

## Integration Impact

- Touches core workflow docs and skills; no runtime product code in this repo.
- Deployed repos inherit via template sync/copy; local style guides remain additive.

## Migration / Compatibility

- Backward compatible: existing Design Specs remain valid; new Quality DoD applies to new work.
- No data migration.
- Transitional: none expected; if a deployed repo relied on Feature IDs in comments for traceability, move that trace to progress/commits and register short debt if cleanup is phased.

## Verification Strategy

- Doc cross-link review: authority map has single owners; adapters only point.
- Domain-neutrality scan on new core text.
- Red-flag table exercised against one intentional bad Design/Plan sample (in principle card or test doc).
- Comment-rule examples: good vs bad comments included and greppable in review.
- Acceptance: design-review of *this* spec reaches Ready before implementation slices.

## Open Questions

1. Should Quality DoD be required for L1, or only L2+? — **Proposal:** L2+ required; L1 recommended; L0 process-light only. Blocking? no (default as proposal unless overridden in review).
2. Fresh-context code review skill in MVP or defer? — **Proposal:** defer to follow-up; document as optional. Blocking? no.
3. Bilingual principle card vs English-only core? — **Proposal:** follow profile `docs_language`; ship English core first, ZH gloss optional later. Blocking? no.

## Design Review

- **Verdict:** `Ready with deferred items`
- **Reviewer / date:** Agent design-review / 2026-10-15
- **Link or summary:** See findings below (recorded in-session).

### Review findings

- [important] Open Question 1–3 need explicit acceptance — defaults are sound but Implementation Plan must freeze them. **Resolution:** accept proposals: Quality DoD required L2+ (L1 recommended); fresh-context review deferred; English principle card first.
- [minor] `DESIGN_PRINCIPLES.md` must stay a card (lenses + anti-abuse + links), not a mini-textbook — otherwise agents may paste theory into every Design Spec. **Resolution:** Implementation Plan caps length (~1 page) and forbids mandatory SOLID matrix in design-spec template.
- [minor] Intent-playback gate needs one adapter sentence so it is not forgotten outside the skill. **Resolution:** add trigger bullet in WORKING_WITH_AI / workflow triggers during impl.
- [nit] Verification “bad sample” should live under `templates/` examples or DESIGN_PRINCIPLES, not a fake Feature doc. **Resolution:** keep exemplars inside the principle card / templates README.

### Deferred / accepted risks

- Fresh-context code-review skill — deferred; optional later feature
- ZH bilingual principle card — deferred until `docs_language` demand
- Superpowers-like diagnosing-session skill — out of scope

## Implementation Readiness

- [x] Requirements understood
- [x] Constraints identified
- [x] Relevant existing architecture inspected
- [x] Responsibilities and boundaries defined
- [x] Key dependencies understood
- [x] Ownership/lifetime resolved or N/A
- [x] Major state/invariants resolved or N/A
- [x] API semantics sufficiently defined
- [x] Important failure modes considered
- [x] Alternatives considered where meaningful
- [x] Integration impact understood
- [x] Verification strategy exists
- [x] Unresolved questions resolved or explicitly deferred/accepted — Q1–Q3 accepted as proposed above

**Ready for implementation?** `yes` — after Implementation Plan traces D1–D7; large coding of adapters still waits for that plan.

## Acceptance Checklist

- [x] Design review complete (L2)
- [x] Implementation plan traces to D1–D7 / D4b
- [x] Progress log updated when status changes
- [x] Feature registry status synced
