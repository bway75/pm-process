# Delivery and Distribution Process

## Overview

Once development is complete, what was built does not automatically reach its audience. Delivery is a fan-out process — the same capability may simultaneously be distributed through multiple paths, to multiple audiences, at different release and commercial tiers, with different artifacts and communication for each.

This document defines that process: how completed work is assessed, staged, distributed, and communicated — and how feedback from distribution feeds back into intake.

---

## Two Dimensions of Release

Every release sits at the intersection of two independent dimensions. Both must be set explicitly before distribution begins.

### Dimension 1 — Release Tier

| Tier | What it means | Who has access |
|---|---|---|
| Internal | Not customer-facing. Practice team and firm only. | Internal staff |
| Preview | Selected subset of customers shown the capability for directional feedback. Not broadly available. | Named accounts only |
| Beta | Wider customer availability. Explicitly marked as not-GA. May have issues. Requires feedback mechanisms built in. | Opted-in customers |
| GA | Fully released, supported, stable. | All customers |

### Dimension 2 — Commercial Tier

| Tier | What it means |
|---|---|
| Not for sale | Exists but not in the sales motion. No new deals. |
| Early access | Sellable to willing early adopters, often at different terms or pricing. Requires specific commercial structure. |
| For sale | Full commercial availability at standard pricing and terms. |

### Packaging Type

Separate from release and commercial tier — packaging type drives the go-to-market motion:

| Type | Implication |
|---|---|
| New SKU | Standalone commercial entity. Needs its own pricing, SOW language, sales enablement, and external documentation. Full go-to-market motion required. |
| New feature / capability extension | Part of an existing product or service. Communication goes to current customers. Expansion selling motion rather than new-logo motion. |

---

## What Each Combination Requires

The intersection of release tier, commercial tier, and packaging type determines the distribution work. Key scenarios:

| Scenario | What it requires |
|---|---|
| Internal + not for sale | Internal brief to practice team. No customer-facing artifacts. |
| Preview + not for sale | Named-account outreach, feedback collection mechanism, NDA or preview agreement. No broad communication. |
| Beta + not for sale | Beta announcement to opted-in segment, in-product feedback tooling, Beta terms of service, internal support briefing. |
| Beta + early access | All of Beta above, plus: commercial structure, early adopter pricing, account team enablement. |
| GA + for sale + new feature | Existing customer communication, expansion selling guide for account teams, release notes, support documentation. |
| GA + for sale + new SKU | Full go-to-market: pricing model, SOW language, sales enablement package, external one-pager or brief, internal all-hands or announcement, support documentation, training. |

---

## Pre-Distribution Gates

Four gates must be cleared before any customer-facing release tier. These are separate from technical completion.

### 1 — Support and Documentation Readiness

Technical GA and distribution readiness are different. Before any customer-facing release:

- Customer-facing documentation exists and is accurate
- Support team has been briefed and knows how to handle tickets
- Known issues and workarounds are documented internally
- Escalation path is defined for issues that arise post-release

A capability that is technically complete but undocumented and unsupported is not ready to release.

### 2 — Internal Enablement

Before account teams can sell or reference a capability, they must be able to describe it, demo it, and handle objections. Internal enablement artifacts:

- Internal capability brief (what it is, who it is for, how it is positioned)
- Demo environment or walkthrough available
- Objection handling and competitive context
- Pricing and packaging guidance (if commercial)

Enablement gates the commercial tier specifically. A capability can reach Beta or Preview without full sales enablement, but it cannot enter the sales motion without it.

### 3 — Regulatory and Compliance Review

Applicable to capabilities in regulated domains (OT security, critical infrastructure, federal, utilities) or with data handling implications. Before customer-facing release in relevant segments:

- Internal compliance review completed
- Legal review of any required disclosures or limitations
- Segment-specific restrictions documented (if the capability cannot be offered to certain verticals or geographies)

This gate sits alongside sales-readiness and may vary by customer segment even within a single release.

### 4 — Sales-Readiness Gate

The determination that a capability is ready to enter the sales motion. This is not binary — it is tiered by commercial tier:

| Commercial tier | What sales-readiness requires |
|---|---|
| Early access | Commercial structure defined, account team briefed, terms documented |
| For sale — new feature | Expansion selling motion defined, existing customer communication drafted |
| For sale — new SKU | Full go-to-market package complete: pricing, SOW language, enablement, external artifacts |

---

## Distribution Artifacts by Audience

| Audience | Artifacts |
|---|---|
| Internal firm | Capability brief, internal announcement, demo access, enablement package |
| Preview customers | Outreach communication, preview agreement, feedback collection mechanism |
| Beta customers | Beta announcement, in-product feedback tooling, Beta terms, release notes |
| All customers (GA) | Customer announcement, release notes, updated documentation, support briefing |
| Prospects / market | External one-pager, updated product/service catalog, sales enablement package |
| Account teams | Internal brief, talk track, objection handling, pricing guidance, SOW language |

---

## Beta — Special Requirements

Beta is the only tier that requires feedback and evaluation mechanisms to be built into the capability itself. This must be specified at PRD time — not designed at distribution.

Beta requirements that belong in the PRD:

- In-product feedback mechanism (how customers submit observations or issues)
- Usage telemetry to understand actual adoption patterns
- Defined feedback review cadence (how often PM reviews Beta input)
- Clear Beta exit criteria (what signals confirm readiness for GA)

If the PRD does not specify these, the capability cannot reach Beta without a remediation pass.

---

## Feedback Loop to Intake

Distribution is not the end of the process. Beta and Preview release tiers generate structured input that re-enters intake:

- Customer feedback from Beta becomes new intake items (bugs, scope additions, directional shifts)
- Account team observations from early access surface new requests
- GA adoption patterns (usage telemetry, support ticket trends) identify gaps and priorities

This feedback must enter through the standard intake process — with source type noted as Beta feedback or customer observation — rather than bypassing evaluation. The only exception is critical bugs, which take the emergency path.

---

## Bypass Tracks

Two situations require paths that operate outside the standard release process.

### Emergency / Incident Path

Security vulnerabilities, critical production bugs, and compliance deadlines cannot wait for standard evaluation and release cycles. The emergency path is a compressed version of the full process:

- Immediate triage by PM and engineering lead
- Scope limited strictly to the fix — no additions
- Customer communication drafted before release, not after
- Post-incident review feeds back into the standard process as a documented intake item

The emergency path is not an invitation to bypass quality or communication — it is a time-compressed version of the same process.

### Competitive Response Path

When a competitor ships something that requires a response, the timeline may be too compressed for standard prioritization. The competitive response path:

- Enters as a leadership directive with competitive context documented
- Receives expedited evaluation (Pass 1 only if scope is clear; full Pass 2 if scope is uncertain)
- May displace existing roadmap items — displacement must still be named explicitly
- Goes through standard pre-distribution gates (support, enablement, compliance, sales-readiness)

Speed in competitive response comes from accelerating evaluation, not from skipping it.

---

## Deprecation and Sunsetting

When a capability is replaced or retired, that is also a distribution event. Deprecation is often designed last and done badly. The deprecation process:

- **Notice period** — customers receive advance notice with timeline (length depends on capability criticality and contractual commitments)
- **Migration path** — what customers move to, documented and communicated with the deprecation notice
- **End-of-life communication** — final communication confirming removal
- **Sales catalog update** — capability removed from sales materials and pricing
- **Support wind-down** — support team briefed on end-of-support date and escalation handling during the notice period

Deprecation should be planned at the time of replacement, not after the replacement is built.

---

## Relationship to Practice Operating Model

This document defines the detail behind Stages 5 and 6 of the six-stage practice operating model (`practice-operating-model.md`). Completed work exits Stage 4 (Delivery) and enters this process.

```
Stage 1: Intake         ← intake-and-evaluation.md
Stage 2: Evaluation     ← intake-and-evaluation.md
Stage 3: Pipeline
Stage 4: Delivery       ← pm-documentation-process.md operates here
Stage 5: Distribution & Awareness   ← this document
Stage 6: Sales-Readiness Gate       ← this document
```
