# Intake and Evaluation Process

## Overview

This document defines the front-end process for the practice operating model — how new requests and ideas enter, how they are assessed, and how the business determines what to build, when, and why.

The goal is a **decision-visibility system**, not a decision-making machine. The output of this process is a structured statement of factors that makes the right decision obvious — or, when it isn't, surfaces the real disagreement so it can be resolved on substance rather than politics.

---

## Stage 1 — Intake

### Sources

**Customer-facing channels**
- Sales / BD — pipeline-driven, deal-specific, often urgent
- SEs / Pre-sales — technically informed, often surfacing capability gaps mid-deal
- Customer Success / TAMs — relationship-driven, pattern-based, longer time horizon
- Managed Services / SOC — operational, seeing what breaks in the real world
- Professional Services / Delivery — in-engagement discovery
- Support — reactive, symptom-level, high volume but low individual signal quality

**Internal / Leadership**
- Leadership strategic directive — aligned to firm strategy, high urgency by default
- Practice leads / technical SMEs — research-driven, often ahead of the market

**PM-initiated / Strategic**
- Competitive analysis and market research
- Usage data / operational telemetry — patterns in what is being used, failing, or repeatedly requested

**Partners and market signals**
- Partner integrations, channel requests
- Industry reports, standards bodies, regulatory shifts

### Signal Quality

The inputs that arrive loudest are often the weakest signal. The ones with the best signal are often the quietest.

| Source | Signal Quality | Urgency | Primary Risk |
|---|---|---|---|
| Sales rep (single deal) | Low — one data point, self-interested | High | Building for one customer |
| Managed services / SOC | Medium — operational patterns, reactive | Medium | Solving symptoms not root cause |
| CS / TAMs across accounts | High — cross-customer pattern | Low–Medium | Slow to surface |
| PM research | High — proactive, synthesized | Low | No external validation yet |
| Leadership directive | Variable | Very high | May be underdefined |
| Regulatory / market shift | High — industry-wide signal | Variable | Scope can expand rapidly |

### AI-Enabled Intake

Any input — transcript, email, message, document, or verbal summary — is processed through an intake skill that extracts whatever it can, then asks for missing fields one at a time. It never asks for information already present in the input.

The skill produces a structured intake ticket with five fields:

- **Requestor** — who or what originated this
- **Source type** — which category above
- **Request summary** — 2 sentences max
- **Priority signals** — urgency indicators, deals at risk, client names
- **Open questions** — what is missing before evaluation can proceed

The ticket is automatically created in the project management tool (Linear, JIRA, or equivalent) for PM review. **The ticket is a triage artifact, not an evaluation document.** It gets the request into the queue. No one evaluates off the ticket alone.

### First Gate: Routing Question

Before any evaluation, classify the request:

| Classification | Definition | Process |
|---|---|---|
| On roadmap | Already approved and researched; question is sequencing | Lightweight — sequencing review only |
| Roadmap acceleration | On roadmap, but urgency justifies moving earlier | Sequencing cost analysis |
| Net new, small scope | Not on roadmap; contained enough that research burden is low | Fast-track eligible |
| Net new, large scope | Not on roadmap; significant research required; will displace roadmap items | Full evaluation required |

**Net new requests compete against the roadmap, not just against each other.** Adding a large net new item requires naming what gets deferred and why.

---

## Documentation Layer

Documentation requirements scale with confidence and stakes, not with process. The right amount of detail at each gate is the minimum needed to answer that gate's question — no more.

| Stage | Document | Who writes it | Gate question it answers |
|---|---|---|---|
| Intake | Intake ticket (AI-generated) | AI from any input | Is this routable and qualifiable? |
| Fast qualification | Intake ticket sufficient | — | Is this urgent enough to evaluate now? |
| Structured evaluation | 2-pager Concept Narrative | PM (AI-assisted) | Is this worth pursuing? |
| Direction confirmed | 6-pager | PM | Are we committed to scope and resourcing? |
| Development handoff | PRD (7-section) | PM | Is this ready to build? |
| Engineering execution | User Stories + AC | PM | Is engineering ready to execute? |

You never write the next document until the current one has cleared its gate.

**The 2-pager Concept Narrative is the minimum viable evaluation document.** It is the smallest document that gives multiple stakeholders enough shared understanding to make a real decision on value, scope, and impact. It must contain:

- Problem — what pain or gap is being addressed
- Who it serves — customer segment and rough count affected
- Rough outcome — what does done look like as a result, not a spec
- Revenue or strategic rationale — why does the business care
- Scope signal — feature-level, capability-level, or new dimension
- Known risks or dependencies — what do we know we don't know

**The 6-pager is an expansion, not a replacement.** When the 2-pager cannot cleanly articulate the components — multiple user types, cross-functional dependencies, things that need separate sections to be legible — the scope warrants a 6-pager. Same purpose, more room.

**The requestor is never required to write a document.** The intake skill structures whatever they provide — email, transcript, verbal summary. PM writes the 2-pager once a ticket passes fast qualification, using the ticket and any supporting materials as input.

### The AI-Enabled Pipeline

```
Any input (transcript, email, message, document)
  → AI intake skill (extract first, ask for delta only)
    → structured intake ticket
      → Linear / JIRA (auto-created)
        → PM reviews queue
          → Pass 1: fast qualification
            → AI drafts 2-pager from ticket + materials
              → PM reviews and refines
                → Pass 2: structured evaluation
                  → Approved → 6-pager if scope warrants → PRD → dev
```

---

## Stage 2 — Evaluation

### Scope / Scale Routing (Before Scoring)

Scope is a routing factor, not a scoring factor. It determines which process the request goes through — not just how long it takes, but what type of commitment is being made.

| Scope signal | Track | Implication |
|---|---|---|
| Feature addition / iteration | Lightweight | Quick brief, fast approval |
| Significant new capability | Standard | Full PRD process, defined review gate |
| New product dimension / practice area | Full | Multi-phase planning, stakeholder alignment, phased delivery |

Scope affects reversibility, organizational change required, and compounding uncertainty — not just effort.

### Pass 1 — Fast Qualification (AI-assisted, ~30 min)

- What is the source, and how much weight does that source carry?
- How many customers does this represent?
- Is there a deal or account at risk?
- Assign urgency tier: **Immediate / This quarter / Backlog**

### Pass 2 — Structured Evaluation

Pass 2 is conducted against the 2-pager Concept Narrative. The 2-pager is the document that drives this evaluation — it is not a formality that follows a decision, it is the artifact that makes the decision possible.

#### Value (assess independently of cost)

| Dimension | What to evaluate |
|---|---|
| Revenue impact | Direct (closes deal, expands account, prevents churn) or indirect (positions practice for a market). Evaluate across all customers, not just the requesting one. |
| Client reach | How many clients benefit? One-client asks are candidates for professional services engagements, not practice investments. |
| Strategic fit | Does this advance a named practice area? Open or protect a market position? |
| Risk of inaction | What happens if we do not build it? Churn, lost deal, competitive disadvantage, regulatory gap. |

#### Total Cost of Ownership (assess independently of value)

| Dimension | What to evaluate |
|---|---|
| Build effort | Engineering time, resources — one-time |
| Ongoing maintenance | Recurring cost once it exists |
| Support load | Expected ticket volume, edge cases, customer-specific handling |
| Complexity tax | Does this make the system harder to reason about, test, or extend? This compounds over time and slows every future change that touches the same area. |

**Net value = (Revenue + Strategic value) − (Build + Maintenance + Support + Complexity tax)**

Note: complexity occasionally goes negative — a feature that replaces a worse workaround reduces complexity, and that should count as a credit.

#### Portfolio Impact

- Does building this conflict with existing customer commitments or roadmap items?
- What does it cost the rest of the portfolio in roadmap capacity, technical debt, or directional alignment?
- Does this take the product in a direction that serves or underserves the broader customer base?

### Mitigating Factors

**Individual vs. aggregate customer weight**

A single customer's urgency is a real signal, but it must be weighed against aggregate customer signals. The factors that govern individual weight:

| Factor | How it adjusts individual weight |
|---|---|
| Revenue threshold | Does this customer represent enough of the business that losing them changes strategic trajectory? Below a threshold, individual urgency is capped. |
| Strategic value | Is this a reference account, market signal, or lighthouse customer? Revenue alone understates their weight. |
| Replicability | Is their need unique to them, or an early signal that more customers will surface the same need? Early signals increase individual weight significantly. |
| Directional alignment | Is where this customer wants to go aligned with where the broader customer base is going? A customer whose needs conflict with the portfolio direction is a different conversation than one who is ahead of the curve. |

**The cost of building for one customer is paid by all other customers** — in roadmap capacity, maintenance burden, and complexity. That cost must be explicit in the evaluation.

A large deal can be canceled out by increased support overhead, maintenance burden, or the complexity tax it imposes on future development. The business should see the full number, not just the contract value.

### Decision Output

The output of evaluation is not a recommendation. It is a structured statement of factors — how they line up, and what would change them.

**Three possible decisions:**

| Decision | Meaning |
|---|---|
| Approved | Enters pipeline; scope track assigned |
| Hold | Specific information needed before deciding (named explicitly) |
| No-go | Declined; reason documented for future reference |

**Every decision must include:**
- **Rationale** — which factors drove the outcome
- **Conditions for reversal** — what new information would change this decision (open questions, assumptions)
- **What this displaces** (if approved) — named explicitly, with sequencing impact visible

---

## Process Philosophy

This process is a decision-visibility system, not a decision-making machine. The business decides — PM's job is to make the signals legible, the trade-offs visible, and the decision defensible.

Two jobs:
1. Surface the current state of the factors
2. Name what would change them

A decision made with full factor visibility — even a hard one — is sustainable. A decision made with invisible costs or invisible competing signals will be relitigated.

---

## Relationship to Practice Operating Model

This document defines the detail behind Stages 1 and 2 of the six-stage practice operating model (`practice-operating-model.md`). Approved requests exit this process into Stage 3 (Pipeline) and Stage 4 (Delivery), where the PM documentation process (`pm-documentation-process.md`) governs artifact production.

```
Stage 1: Intake         ← this document
Stage 2: Evaluation     ← this document
Stage 3: Pipeline
Stage 4: Delivery       ← pm-documentation-process.md operates here
Stage 5: Distribution & Awareness
Stage 6: Sales-Readiness Gate
```
