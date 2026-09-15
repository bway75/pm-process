# Problem Portfolio to Roadmap

## Overview

The standard intake-and-evaluation process (`intake-and-evaluation.md`) assumes requests arrive one at a time — each gets a 2-pager, gets evaluated on its own merits, and either enters the pipeline or doesn't.

That assumption breaks when a leadership directive defines a whole portfolio of problems at once — a mandated set, already validated as real, arriving together rather than trickling in through intake. That's the situation once a Customer Problem Definition exercise (1-left/anchor/1-right/2-right format) has produced a set of confirmed problems, each already decomposed into manifestations and candidate handling ideas.

At that point the open question is no longer "should we pursue this?" — leadership already answered that by mandating the set. The open question is: **which of these problems, and which candidate capabilities inside them, go first — and in what order does a roadmap tell that story?**

This document defines the process between a validated problem portfolio and a sequenced roadmap. It sits before Stage 3 (Pipeline) in the six-stage practice operating model, as a portfolio-level variant of Stage 2 (Evaluation) — evaluating a batch as a set rather than a single item.

```
Stage 1: Intake                    ← intake-and-evaluation.md
Stage 2: Evaluation                ← intake-and-evaluation.md (single item)
Stage 2b: Problem Portfolio        ← this document (mandated batch)
  → Roadmap
Stage 3: Pipeline
Stage 4: Delivery                  ← pm-documentation-process.md (per roadmap item)
Stage 5: Distribution & Awareness  ← delivery-and-distribution.md
Stage 6: Sales-Readiness Gate      ← delivery-and-distribution.md
```

Once a capability exits this process onto the roadmap, it re-enters the standard ladder at the 2-pager / 6-pager stage in `pm-documentation-process.md` — this document does not replace that, it feeds it.

---

## Precondition: A Structured Problem Set

This process assumes problems are already documented in the 2-left/1-left/anchor/1-right bow-tie shape, with handling and solution sketches parked in appendices (see `customer-problem-definition/ot-security-problem-definition-brief.md` for the live example — this superseded the earlier `customer-problem-definition-bw.md` draft as of v3, 2026-07-17):

- **2-left** — board/executive north-star (the business result at P&L altitude)
- **1-left** — desired outcome at the accountable-owner altitude (e.g., CISO), the sharpened problem
- **Anchor** — the complaint as heard, plus its problem-level constraints
- **1-right** — manifestations, each tagged by provenance (customer-voiced / corpus-backed hypothesis / positioning-only / internal-ops-voiced)
- **Appendix A (2-right)** — candidate handling ideas per manifestation, plus what blocks each one
- **Appendix B (3-right)** — solution acceptance sketches, feeding PRD acceptance criteria directly

If problems aren't in this shape yet, that work comes first — this process starts once it exists.

**Maturity gate — read this before Steps 2-3.** This process forks depending on whether the business has real market traction on the offering being roadmapped. Pre-traction (a relaunch, a new subsidiary, an overhauled product with no live GTM signal yet), business-case-style sizing is premature — see `customer-problem-definition/alignment/two-pm-methods-one-pipeline.md` for why: the only market data available describes the product/motion being replaced, and precision positioning has to be earned from real traction, not asserted ahead of it. Steps 2-3 below give the **pre-traction variant** first (validation-signal based) and the **post-traction variant** second (dollar-based Net Value) — use whichever matches where the business actually is, and don't reach for the post-traction variant just because it feels more rigorous. False precision on stale data is worse than acknowledged uncertainty.

---

## Step 1 — Close Out the Portfolio

Before sizing or prioritizing anything, resolve what's still loose in the problem set itself. Scoring an unresolved problem produces a false-precision roadmap.

- **Resolve 🟥 open questions** where possible, or explicitly carry them as named risks into sizing (Step 2) rather than silently dropping them
- **Resolve structuring notes** — places where the problem set itself flagged an unresolved shape decision (e.g., "should this be one problem with three manifestations, or three separate problems?", "do these two candidates overlap enough to merge?")
- **Decide adoption of candidate additions** — anything captured as "surfaced but not mandated" needs an explicit adopt/hold/reject call from leadership before it competes for roadmap space. Don't let unadopted candidates quietly inflate the scored set.
- **Flag validation debt** — every 🟦 hypothesis carries an explicit note of what design-partner validation would resolve it and who's doing that validation. This isn't blocking — it's an input to confidence weighting in Step 3.

**Exit criteria:** every problem in the set is either 🟩 confirmed, 🟦 hypothesis with a named validation path, or explicitly parked. No 🟥 open questions remain unaddressed without an owner.

---

## Step 2 — Opportunity Signal per Problem

### Pre-traction variant (default — use this absent real GTM signal)

Don't size dollar impact yet — you don't have honest inputs for it. Instead, run each problem through its own validation plan: recruit design partners across the segments the portfolio already named, and for each problem capture:

1. **Validation status** — confirmed by which design partner(s), in which segment, or still open
2. **Demand-reality read, per segment** — is pull mandate-forced (inbound sufficient) or does value need active justification here? Ask directly: *"what made you look — a mandate, an insurer, an incident? what happens if you do nothing?"* This is the one slice of positioning worth pulling forward even in a pre-traction stage, because it's cheap to test and de-risks everything downstream — see `two-pm-methods-one-pipeline.md` and `demand-and-inaction-assumption.md`.
3. **Definitional scope resolved** — any fuzzy terms in the problem's own wording ("every," "cheap," "full," "on-prem," "baseline") pinned down to something a requirements doc can use
4. **Josh/engineering's light rough-value hypothesis** — a directional feasibility and value read from the technical side, explicitly *not* a full estimate — enough to help pick design partners and sequence, not enough to pretend precision exists

Output: one short validation note per problem. This is the input Step 3 scores against.

### No-time contingency (roadmap deadline precedes any design-partner access)

Common in a relaunch: the roadmap is due before a formal design-partner program can be recruited and run. This does not mean proceeding on zero evidence — it means substituting evidence you already have or can get opportunistically for evidence you'd otherwise get from a structured program:

1. **Use the provenance tiers already on the problem set as the confidence input**, instead of design-partner confirmation. Customer-voiced and internal-ops-voiced claims are real signal, gathered without a formal program — score them accordingly. Corpus-backed hypotheses carry real but weaker weight. Positioning-only claims don't enter "Now" — no customer ever said them.
2. **Mine every existing client touchpoint opportunistically**, rather than waiting on new design-partner recruitment. Any live call already on the calendar for any reason (QBR, renewal, support escalation, delivery sync) is a chance to ask the open validation questions and capture the answer as a short call-detail doc feeding back into the brief — this firm already has a working precedent for exactly this pattern (see `customer-problem-definition/client-portal-2026-07-09-weyerhaeuser-call-detail.md`: a ServiceNow-integration call that became the first client-voiced validation for an entirely different brief, because the team asked its open questions while the client was already on the line).
3. **Run the internal SME/leadership panel as a fast proxy for design-partner scoring.** People who already talk to real accounts regularly (sales, delivery, leadership who've heard these complaints directly) can score validation-strength and demand-reality from what they already know. Not equivalent to real customer validation, but a legitimate, fast stand-in when a structured program isn't available in time.
4. **Sequence by cost-of-being-wrong, not by certainty you don't have time to earn.** Favor cheap, reversible, broadly-leveraged bets (capabilities multiple problems depend on) over expensive, narrow, hard-to-reverse ones when validation strength is otherwise similar.
5. **Make delivery the validation.** Ship the first "Now" item to real customers as fast as possible and treat their reaction as the validation the timeline didn't allow upfront.
6. **Surface the deviation to whoever asked for validation-before-building, explicitly.** If leadership specifically asked for design-partner validation ahead of any commitment, shipping a roadmap without it is a real, deliberate deviation driven by the deadline — not a quiet process substitution. Name what was used instead and when real validation catches up.

### Post-traction variant (once real GTM signal exists)

Once design partners have converted to paying/committed use and there's live pipeline data, apply the 4-step impact-sizing framework (`impact-sizing` skill) at the problem level — usage funnel, tie to the segment's business outcome, de-risk assumptions, takeaway — the same as any mature-product roadmap pass. Don't reach for this variant early just because it produces more official-looking numbers; the numbers would be fiction until traction exists to ground them.

---

## Step 3 — Cross-Problem Prioritization

### Pre-traction variant (default)

Score at the problem level using **Validation-Signal Score**, not dollar value:

| Factor | Source | Notes |
|---|---|---|
| Validation strength | Step 2 validation status | How many design partners confirmed it, across how many segments |
| Demand-reality fit | Step 2 demand read | Theory-A segments (mandate-forced, inbound-sufficient) are readier buyers now; Theory-B segments (value must be justified) need more groundwork before they're a "Now" candidate |
| Feasibility | Josh's rough-value hypothesis | Directional only — a clear "hard/unclear/tractable" read is enough |
| Dependency cost | The problem's own documented blockers | These are already written down in the handling/blockers appendix; don't re-derive them, just note them as a drag on sequencing |
| Cross-problem leverage | Portfolio review | A capability that resolves or feeds multiple problems (e.g., a context/topology capability feeding both an inventory problem and a talent problem) ranks higher even if no single problem's validation is the strongest — don't double-count its cost across the problems it serves |

This produces a sequencing signal, not a forecast. Its job is to answer "what do we put in front of design partners first, and in what order," not "what will this be worth."

### Post-traction variant (once real GTM signal exists)

Adapt the practice's existing Net Value formula (`intake-and-evaluation.md`) rather than importing an external framework (RICE, ICE, etc.) — reusing it keeps one scoring mental model across the whole operating model instead of two competing ones.

**Portfolio Net Value** = (Segment Impact + Strategic Value) − (Build Effort + Dependency Cost) — × **Confidence Weight**

| Factor | Source | Notes |
|---|---|---|
| Segment Impact | Step 2 sizing | Revenue/retention impact for the segment(s) this problem serves |
| Strategic Value | Portfolio review | Does this open a market position no one else holds? |
| Build Effort | Engineering estimate on the leading candidate handling idea(s) | Rough order of magnitude is enough at this stage |
| Dependency Cost | The problem's own documented blockers | Already written down in the handling/blockers appendix; don't re-derive, just cost them |
| Confidence Weight | Provenance tag on the problem | Full weight for confirmed, discounted for unvalidated hypothesis, excluded until resolved for open questions |

**What neither variant does:** score every manifestation and handling idea individually. Score at the problem level first. Once a problem clears prioritization, its manifestations get ranked against each other only within that problem, when it's time to scope the actual capability (Step 4).

---

## Step 4 — Solution Framing (Problem → Candidate Capability)

For each problem that clears Step 3, promote its credible handling ideas into named candidate capabilities — the shape a 2-pager Concept Narrative needs (`intake-and-evaluation.md`'s documentation layer):

- **Problem** — which mandated problem this serves
- **Who it serves** — segment and rough count
- **Rough outcome** — what "done" looks like, at the business-outcome altitude the problem definition already established (not a feature description)
- **Rationale** — why now, referencing the Step 3 score
- **Scope signal** — feature-level, capability-level, or new dimension (this determines which track it takes in `intake-and-evaluation.md`'s scope routing table once it enters Stage 4)
- **Known risks/dependencies** — pulled directly from the problem's documented blockers

This is where multiple manifestations under one problem either consolidate into a single capability or split into separate roadmap items — the structuring calls flagged in Step 1 get finalized here if they weren't already.

---

## Step 5 — Thematic Grouping

Group the prioritized candidate capabilities into a small number of pillars — 4-6 is the useful range; more than that and the roadmap reads as a feature list again, which defeats the point (`roadmap-template.md`'s Features vs. Outcomes principle).

Pillars should read as strategic bets a board would recognize, not internal work-stream names. Draft candidates from this portfolio (confirm/rename, don't treat as final):

- **Detection Quality** — tuning, alert trust, coverage assurance
- **Data Sovereignty & Compliance** — on-prem, NERC CIP posture, tokenization
- **IT/OT Bridging** — enabling an existing IT SOC to safely cover OT
- **Context & Visibility** — asset inventory, topology, cross-site environment awareness
- **Managed Talent Wedge** — the "fast for a senior, simple for a junior" service layer
- **OT-Safe Response** *(if adopted from candidates)* — authority, safe action, restoration
- **Assurance & Board Communication** *(if adopted from candidates)* — proving risk reduction, not just activity

---

## Step 6 — Roadmap Construction

Use the Now/Next/Later format (`roadmap-template.md`), gated explicitly by validation state rather than by date confidence alone — the biggest roadmap risk pre-traction is shipping a "Now" commitment built on an unvalidated hypothesis.

| Tier | Gate |
|---|---|
| **Now** | Confirmed by at least one design partner, Step 1 exit criteria met, no unresolved blockers on the leading capability. Pre-traction, treat "Now" as **what gets piloted with named design partners**, not a scaled sales commitment — see Step 7. |
| **Next** | Hypothesis-backed capabilities with an active design-partner validation path already underway |
| **Later** | Adopted-but-unvalidated candidates, and anything still carrying an unresolved structuring or definitional question |

Segment the roadmap explicitly by buyer context rather than presenting one undifferentiated timeline — regulated utilities, manufacturing, and oil & gas carry different regulatory postures, different business outcomes, and (per Step 2's demand-reality read) different degrees of inbound-sufficient vs. justification-needed demand. A single Now/Next/Later that doesn't say which segment each tier targets, and which demand theory that segment tested as, will read as generic to a CISO evaluating it.

Name market-entry points per segment explicitly — which capability, piloted with which segment's design partner, is the first packageable offer.

**Pre-traction, don't let the roadmap imply GTM-grade commitments it can't back up.** The Now tier is a validated pilot plan; it becomes a sales-grade roadmap once Step 2's post-traction variant is actually running.

---

## Step 7 — Packaging Handoff

Before full build starts on a "Now" item, decide whether it should be packaged and positioned ahead of development to validate direction with design partners — this was explicitly called for in the 2026-07-10 review ("potentially ahead of full development, to validate direction").

This is the handoff into the existing Stage 5/6 model (`delivery-and-distribution.md`): a pre-build package is functionally a Preview-tier, not-for-sale release — named design partners, a feedback mechanism, no broad availability — using the same release-tier and pre-distribution-gate machinery already defined there, just applied earlier than usual (before Stage 4 documentation is complete, not after).

---

## Summary Flow

```
Structured problem set (2-left/1-left/anchor/1-right, Appendix A/B)
  → Step 1: Close out portfolio (resolve open Qs, structuring notes, candidate adoption)
    → Step 2: Opportunity signal per problem
        [pre-traction] validation status + demand-reality read + rough feasibility
        [post-traction] impact-sizing (usage funnel, segment impact, de-risk)
      → Step 3: Cross-problem prioritization
          [pre-traction] Validation-Signal Score
          [post-traction] Portfolio Net Value × Confidence Weight
        → Step 4: Frame solutions (problem → candidate capability, 2-pager shape)
          → Step 5: Group into pillars (4-6, board-legible)
            → Step 6: Build roadmap (Now/Next/Later, gated by validation, segmented by buyer + demand theory)
              → Step 7: Packaging handoff (pre-build Preview release with design partners, if warranted)
                → Stage 3/4: standard pipeline + PM documentation process, per item
                  → traction event (design partners actually using it)
                    → re-run Steps 2-3 in the post-traction variant; positioning/GTM work begins
```
