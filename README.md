# Practice Process

How something new gets requested, reviewed, documented, built, delivered, and communicated.

This repo is the operating model scaffolding — the end-to-end pipeline Steve calls "the machine." It covers what's owned by PM: intake through the artifacts that hand off to Dev, and the delivery / distribution fan-out after Dev completes. The Dev execution stage is intentionally not defined here; that's owned by Engineering.

---

## Start Here

**[process-overview.html](process-overview.html)** — Five-slide visual overview of the full pipeline. Open in a browser. No install required.

---

## Examples

The [`examples/`](examples/) directory contains a synthetic end-to-end run through the process — Concept Narrative → PRD → User Stories — for an OT security capability built from the B&M research corpus. Shows what the PM→Dev handoff actually looks like.

---

## What's in This Repo

| File | Stage | What It Covers |
|---|---|---|
| [practice-operating-model.md](practice-operating-model.md) | All stages | Six-stage overview and document reference map |
| [intake-and-evaluation.md](intake-and-evaluation.md) | Stages 1–2 | Request intake, signal quality, evaluation criteria, routing, and go/no-go decision model |
| [pm-documentation-process.md](pm-documentation-process.md) | Stage 4 | PM artifact-production process — Concept Narrative through PRD and User Stories |
| [pm-docs-gpt-prompt.md](pm-docs-gpt-prompt.md) | Stage 4 | Full PM doc spec — deployable as a ChatGPT or Claude custom instruction set |
| [delivery-and-distribution.md](delivery-and-distribution.md) | Stages 5–6 | Release tiers, commercial tiers, parallel workstreams, pre-release gates, and distribution fan-out |

---

## The Pipeline Shape

```
[Sales] [TAMs] [CS] [Leadership] [SMEs] [PM Research] [Partners]
                          ↓
                   Intake & Evaluation
                          ↓
              PM Documentation Process
              (Concept Narrative → PRD → User Stories)
                          ↓
              Development  ← Engineering-owned, not defined here
                          ↓
              Delivery & Distribution (fan-out)
                          ↓
    [Internal] [Preview] [Beta] [GA] × [Not for sale] [Early access] [For sale]
                          ↓
                   Feedback → back to Intake
```

---

## What's Defined

- How requests enter, get evaluated, get routed, and get a go/no-go decision
- The PM artifact sequence that gates development (what Dev receives before a ticket is ready)
- The delivery and distribution model after development completes
- Parallel workstream timelines by release type (Feature/MVF, Beta, New SKU)

## What's Intentionally Not Defined Here

- **Dev execution process** — owned by Engineering; what matters to this model is what artifacts Dev receives and what signals Dev-complete
- **Specific tooling** — Linear, JIRA, specific AI skills, deployment infrastructure — these are implementation decisions that follow from the operating model, not part of the scaffolding itself

---

## Version Note

This is a V0.1 operating model — defined at the handoff and decision-gate level. Individual stage subprocesses are owned by their respective functions and will evolve as real work moves through the pipeline. The intent is a working model, not a locked procedure.
