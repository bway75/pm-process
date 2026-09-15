# Starting a New Product — Zero to Baseline Requirements and Roadmap

## Overview

The other documents in this repo each cover one stage of the practice operating model. This document is the connective narrative for the specific situation of starting a brand-new product from nothing: which document to write first, in what order, and what each one hands to the next — ending in baseline requirements and a working roadmap.

It was written after running this exact sequence for real (the OT security / Prism relaunch, see `customer-problem-definition/`), so the gotchas below aren't theoretical — they're what actually went wrong or needed correcting along the way.

```
Phase 0: Frame the product        (new — not covered elsewhere in this repo)
Phase 1: Discover the problems    → problem-portfolio-to-roadmap.md's precondition
Phase 2: Validate (or substitute) → problem-portfolio-to-roadmap.md Step 1 + no-time contingency
Phase 3: Prioritize & sequence    → problem-portfolio-to-roadmap.md Steps 2-3
Phase 4: Build the roadmap        → problem-portfolio-to-roadmap.md Steps 4-6
Phase 5: Baseline requirements    → pm-documentation-process.md (per roadmap item)
Phase 6: Build → Delivery         → delivery-and-distribution.md (engineering-owned handoff onward)
```

---

## Phase 0 — Frame the Product

**Not yet documented elsewhere in this repo — start here for anything genuinely new.** Every downstream phase assumes you already know what business you're in and who you're serving. For a brand-new product, that's not yet true, and skipping this step is the most common reason a problem-discovery pass drifts (complaints get collected without a filter for which ones are actually in-bounds).

**Document:** a short Product Framing note, a page or less. Not a strategy doc, not a business case — just enough to give Phase 1 a boundary.

- **What business are we in** — the north-star outcome the product exists to serve (see `pm-tools`' `define-north-star` skill for the Frequency × Core Action × Breadth formula, and `write-prod-strategy`'s Objective/Users/Vision components for the shape)
- **Who it's for** — the buyer and the user, if they differ, and the segments you expect to matter
- **Why now** — what makes this the right moment (a market shift, an internal capability, a leadership directive)
- **Explicit non-goals** — what this product is deliberately not trying to be, so Phase 1 has a filter

**Gotcha:** don't let this phase turn into positioning. It answers "what are we here to do," not "how do we sell it." If you catch yourself drafting messaging or competitive framing here, that's Phase 6-adjacent work sneaking in too early — park it (see Phase 2's note on the same failure mode, it recurs).

---

## Phase 1 — Discover the Customer Problems

**Document:** the Initiative Brief, at 6-pager depth, in the bow-tie format: **2-left** (board/executive north-star) → **1-left** (desired outcome at the accountable-owner's altitude) → **Anchor** (the complaint as heard, plus its hard constraints) → **1-right** (manifestations, provenance-tagged). See `customer-problem-definition/ot-security-problem-definition-brief-v4.md` for a full worked example, including its appendix structure — copy its shape, not its content.

**Process:**

1. Gather raw complaints from every real source available — sales, CS, delivery teams, direct customer conversations, existing research. Don't filter for solvability yet.
2. For each complaint, work outward in both directions from the complaint as heard: back it up one step to the desired business outcome (1-left), and decompose it one step forward into its specific manifestations (1-right), each tagged by evidence tier.
3. **Use provenance tags from day one**, not just at review time: customer-voiced (a real customer or defining meeting said this), internal-ops-voiced (your own delivery team lives this pain independently), corpus-backed (research supports it but no customer confirmed it), positioning-only (market/analyst material with no customer voice at all). This is what let the OT brief separate real signal from imported claims later — retrofitting tags after the fact is much harder than tagging as you go.
4. **Resist the solution.** The discipline that keeps this phase honest: discovery works outward from what the customer said, not inward from what you could build. The moment a "handling idea" starts defining the problem statement itself, the problem set stops being trustworthy. Solution hypotheses have a home — the appendices, not the body.
5. **Park solution thinking in appendices, in three parts, not two.** The original bow-tie format calls for Appendix A (handling ideas and blockers) and Appendix B (solution acceptance sketches). Add a third: **Appendix C, viability and alignment risk** — for each problem, ask "could this fail to be solvable, or fail to find alignment, even if we built it?" This was missing from the first pass at the OT brief and is worth building in from the start rather than retrofitting: it catches problems that are real but structurally hard to close (a regulatory question that might not resolve favorably, a customer segment that might reject the proposed authority model) before they're deep into requirements.
6. **Close Gate 1 explicitly.** Get an actual leadership sign-off moment on the problem set — which items are mandated, which are proposed additions, which surfaced-but-unadopted candidates stay out. Don't let this drift into "everyone seems to agree" without a stated decision; the OT case had this ambiguity (a brief marked `status: draft-for-review` well past the point where the room had informally agreed).

---

## Phase 2 — Validate (or Substitute, If Time Doesn't Allow)

**Document:** a Validation Plan section within the Initiative Brief, naming design partners across your real segment spread and the specific hypotheses each partner would test. If a design-partner program can't run before the roadmap is due, this phase's document becomes a short **substitution log** instead — what evidence you used in its place, and when real validation will catch up.

**Process, if time allows:**

- Name 1-3 design partners spanning your actual segment diversity, not a convenience sample
- For each unconfirmed (corpus-backed or positioning-only) item, write the specific question a partner conversation would need to answer
- Pull forward the one slice of positioning work that's cheap and de-risks everything downstream: is demand mandate-forced (inbound is sufficient) or does value need active justification (you'll need to build pipeline, not just serve it)? This single question is worth testing even when the rest of positioning is correctly deferred.

**Process, if time does not allow (the common case for a real deadline):**

- Don't block the roadmap on a validation program you can't run in time. Substitute:
  - The evidence-tier system from Phase 1 — customer-voiced and internal-ops-voiced items are real signal, gathered without a formal program
  - Opportunistic capture — any live client touchpoint already scheduled for any reason is a chance to ask your open questions, exactly as it happened when a routine integration call surfaced the first real validation for an entirely different brief (see `customer-problem-definition/client-portal-2026-07-09-weyerhaeuser-call-detail.md`)
  - An internal SME panel — people who already talk to real accounts regularly scoring validation-strength and demand-reality from what they already know, as a fast, honest, if imperfect, stand-in
- **Say so explicitly, to whoever asked for validation.** If leadership specifically asked for design-partner validation before any commitment, proceeding without it is a real, deliberate deviation driven by the deadline, not a quiet process substitution. Name what was used instead.

**Gotcha (the same one as Phase 0, recurring):** the temptation at this phase is to reach for business-case-style sizing (revenue impact, dollar value) because it looks more rigorous than evidence-tier scoring. Resist it if you don't yet have real market traction — the numbers would be fiction, and false precision on stale data is worse than acknowledged uncertainty. See `problem-portfolio-to-roadmap.md`'s pre-traction vs. post-traction fork for exactly where that line is and how to tell which side of it you're on.

---

## Phase 3 — Prioritize and Sequence the Portfolio

**Document:** a prioritized ordering added directly into the Initiative Brief — not a separate artifact. See `problem-portfolio-to-roadmap.md` Steps 2-3 for the full method (pre-traction and post-traction variants) and the OT brief's Section 10 for a worked example of the pre-traction / no-design-partner scoring in practice.

**Process, in brief** (full detail lives in `problem-portfolio-to-roadmap.md`):

- Score at the problem level, not the manifestation level, until the field has narrowed
- Absent real traction: score on evidence tier, cross-problem leverage (a problem whose solution unlocks several others ranks higher even if no single validation is the strongest), and leadership signal already on record
- With real traction: switch to the practice's Net Value formula (`intake-and-evaluation.md`) — revenue/strategic value against build effort and dependency cost
- Cross-problem leverage is usually the single most under-weighted factor in a first pass — the OT case's context problem (#6) scored as the clear first move not because it was cheapest, but because two other problems were explicitly said to depend on it

---

## Phase 4 — Build the Roadmap

**Document:** the roadmap itself, Now/Next/Later format (`pm-tools`' `roadmap-template.md`), grouped into 4-6 board-legible strategic pillars (see `problem-portfolio-to-roadmap.md` Step 5 for pillar construction).

**Process:**

- Gate tiers by validation state, not just date confidence: **Now** = strongest evidence and fewest open blockers; **Next** = credible but still validating; **Later** = adopted but unresolved or narrowly-scoped
- Segment explicitly by buyer context if your problems don't affect every segment equally — a single undifferentiated timeline reads as generic to whoever's evaluating it against their own situation
- Pre-traction, frame "Now" as what gets piloted with real customers, not a scaled sales commitment — the roadmap's first cut is itself part of how you get the validation signal the timeline didn't allow earlier
- Name the deliberate deviation from ideal process (per Phase 2) inside the roadmap review, not buried in a footnote — a stakeholder evaluating the roadmap should know which items rest on real validation and which rest on evidence-tier substitution

---

## Phase 5 — Baseline Requirements, Per Roadmap Item

**Document:** the standard documentation ladder, per item, from `pm-documentation-process.md` — 2-pager Concept Narrative → 6-pager (if scope warrants: multiple user types, cross-functional dependencies) → PRD (7-section: Problem/Why, Context & Objectives, Users & Use Cases, Core Functionality, Architecture & Dependencies, Delivery Phases, Risks/Metrics/Success) → User Stories with acceptance criteria.

**Process:**

- Never write the next document in the ladder until the current one has cleared its gate — the 2-pager answers "is this worth pursuing," the PRD answers "is this ready to build," skipping ahead produces a spec built on an unagreed premise
- Separate MVF (minimum viable/feasible) from Future explicitly in every PRD — the most common source of scope creep at handoff is this line blurring
- Appendix A and B from the Initiative Brief (Phase 1) are direct input here, not a starting-from-scratch exercise — the handling ideas become the PRD's core functionality section, the solution acceptance sketches become its acceptance criteria
- If multiple related items share dependencies, use an umbrella Initiative Brief (the same document from Phase 1-4, now also serving this role) to hold problem, objectives, non-goals, global constraints, shared dependencies, sequencing, and cross-PRD metrics — so child PRDs don't drift independently

---

## Phase 6 — Build, Then Delivery and Distribution

Outside this document's main scope, but named for completeness: development is engineering-owned (not defined in this repo by design — see `pm-process/README.md`'s "What's Intentionally Not Defined Here"). Once a build completes, `delivery-and-distribution.md` governs release tiers, commercial tiers, pre-distribution gates, and the fan-out to internal, preview, beta, and GA audiences. Feedback from that stage re-enters at Phase 1/3 as new problem signal, not as a bypass of intake.

---

## One-Page Summary

| Phase | Document | Core question it answers |
|---|---|---|
| 0. Frame | Product Framing note | What business are we in, who's it for, why now |
| 1. Discover | Initiative Brief (bow-tie, Appendices A/B/C) | What are the real problems, in the customer's own words |
| 2. Validate | Validation Plan or substitution log | Is this real, and if we can't fully check, what did we use instead |
| 3. Prioritize | Prioritized ordering (in the Brief) | Which problems, and in what order |
| 4. Roadmap | Now/Next/Later roadmap | What ships when, to whom, at what confidence |
| 5. Baseline requirements | 2-pager → 6-pager → PRD → User Stories | Is this specific thing ready to build |
| 6. Build → Delivery | (engineering-owned) → release/distribution artifacts | Is it built, and how does it reach its audience |

## Related

- `problem-portfolio-to-roadmap.md` — the detailed method behind Phases 2-4
- `pm-documentation-process.md` — the detailed method behind Phase 5
- `intake-and-evaluation.md` — the steady-state (post-launch, one-item-at-a-time) version of Phases 1-3, for after this product already has a roadmap and is taking in new requests
- `delivery-and-distribution.md` — Phase 6 in full
- `customer-problem-definition/ot-security-problem-definition-brief-v4.md` — a full worked example of Phases 1-4 end to end
