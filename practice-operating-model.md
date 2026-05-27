# Practice Operating Model — "The Machine"

The question Steve (Managing Director) raised: before executing on any capability, there needs to be a defined operating model — the pipeline that takes something from initial request through delivery, distribution, and sales-readiness. Without this, the practice has depth but no repeatable way to deploy it.

This document captures that model. Each stage is detailed in a dedicated document. See the reference map at the bottom of this document.

---

## The Six Stages

### Stage 1 — Intake
**How do new requests come in?**

The front door for a new capability, service, or deliverable. A request can originate from:
- A client inquiry or sales engagement
- A partner referral
- An internal proposal from a technical SME or practice lead
- A leadership directive

**What needs to be defined:**
- What qualifies as a request vs. background research?
- Who receives it?
- Where does it land (a shared queue, a named owner, a standing meeting)?
- What minimum information is required to open a request?

---

### Stage 2 — Vetting and Assessment
**How do we evaluate whether to pursue it?**

Not every request becomes work. This stage is the filter.

**What needs to be defined:**
- What criteria determine whether we pursue something? (client value, scope, feasibility, strategic fit)
- Who does the assessment? (one person, a small panel, the MD?)
- How do we distinguish a one-off request from a candidate for a repeatable service offering?
- What is the output of this stage — a go/no-go, a scoped proposal, a prioritized backlog entry?

---

### Stage 3 — Pipeline
**What are the stages between "approved" and "delivered"?**

Once a request passes vetting, it enters the work pipeline. This is the operational backbone.

**What needs to be defined:**
- What are the named stages (e.g., scoping → research → draft → review → finalize)?
- Who owns each stage?
- What is the handoff model between roles — sales, technical SMEs, delivery, engineering?
- How is status tracked and visible to stakeholders?
- What does a "blocked" item look like, and who unblocks it?

---

### Stage 4 — Delivery
**How does it get built and reach the customer?**

This is where the work happens. The PM documentation process (`pm-documentation-process.md`) governs how deliverables are structured and documented in this stage.

**What needs to be defined:**
- What is the delivery model for a given type of engagement — assessment, design, implementation, managed service, internal capability?
- What does "done" look like? What are the exit criteria for delivery?
- Who reviews and approves before handoff?
- How does a project formally close?

*The PM docs process (Concept Narrative → 6-Pager → PRD → User Stories → Acceptance Plan) is the artifact-production framework for this stage.*

---

### Stage 5 — Distribution and Awareness
**How does everyone know about it?**

Once something is built — a capability, a service offering, a tool, a product — the firm and its clients need to know it exists.

**What needs to be defined:**
- How does internal awareness get built across the firm?
- Is there a knowledge management function? An internal comms model?
- How do clients learn it exists — account teams, marketing, direct outreach?
- Is there a standard format for announcing new capabilities (a one-pager, a brief, an internal demo)?

---

### Stage 6 — Sales-Readiness Gate
**How do we know something is ready to be sold?**

Research-stage and commercially-deployable are different things. This gate is the checkpoint between them.

**What needs to be defined:**
- What criteria distinguish a research-stage capability from a service that can be sold?
- Who makes that determination?
- What is the internal review and approval model before something enters the sales process?
- What does a "sales-ready" artifact look like — a one-pager, a statement of work template, a pricing model?

---

## Why This Matters

Without this model, the practice accumulates research and technical depth but has no systematic way to convert findings into client value, revenue, or firm capability.

The six stages answer the full lifecycle question: **how does "something new" get requested, reviewed, documented, built, delivered, and communicated?**

---

## Document Reference Map

Each stage is covered in detail by a dedicated document. The overview stages above describe the shape of each stage; the detail documents contain the process, criteria, artifacts, and decision logic.

```
Stage 1: Intake              ← intake-and-evaluation.md
Stage 2: Vetting & Assessment← intake-and-evaluation.md
Stage 3: Pipeline            ← governed by project management tool (Linear / JIRA)
Stage 4: Delivery            ← pm-documentation-process.md + pm-docs-gpt-prompt.md
Stage 5: Distribution        ← delivery-and-distribution.md
Stage 6: Sales-Readiness     ← delivery-and-distribution.md
```

### Fan-In / Fan-Out Shape

The full process has an asymmetric shape: many input paths converge toward a single accepted development process, and many delivery paths fan out from it.

```
[Sales] [TAMs] [CS] [Leadership] [SMEs] [PM Research] [Partners]
                          ↓
                   Intake & Evaluation
                          ↓
              PM Documentation Process (2-pager → PRD)
                          ↓
                 Development (accepted process)
                          ↓
              Delivery & Distribution (fan-out)
                          ↓
[Internal] [Preview] [Beta] [GA] × [Not for sale] [Early access] [For sale]
                          ↓
                 Feedback loop → back to Intake
