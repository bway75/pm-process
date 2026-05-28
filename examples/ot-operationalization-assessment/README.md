# Example: OT Security Operationalization Assessment (OPRA)

Synthetic end-to-end run through the full PM artifact chain. Built from the B&M OT security research corpus finding that fewer than 10% of OT networks are meaningfully monitored despite significant tool investment.

**Scenario:** 1898 & Co. builds a platform-backed assessment service that helps OT asset owners operationalize the security tools they have already purchased but are not running.

---

## Artifacts

| # | File | Artifact | What it answers |
|---|---|---|---|
| 1 | [01-concept-narrative.md](01-concept-narrative.md) | Concept Narrative | Should we build this? Problem, goals, direction, open questions. |
| 2 | [02b-6-pager.md](02b-6-pager.md) | 6-Pager | Why are we building this and what does it look like? Cross-functional context, business case, customer experience. |
| 3 | [02-prd.md](02-prd.md) | PRD (7-Section) | What are we building? Full development spec — inputs, outputs, scope, phases, risks. |
| 4 | [03-user-stories.md](03-user-stories.md) | User Stories | How does Dev execute? Engineering-ready stories with inputs, outputs, and acceptance criteria. |
| 5 | [04-acceptance-plan.md](04-acceptance-plan.md) | Acceptance Plan | How do we know it works? Test cases, edge cases, operational validation, pass/fail criteria. |
| 6 | [05-iteration-planning.md](05-iteration-planning.md) | Iteration Planning | What's the roadmap? MVF → Phase 2 → Phase 3 with deliverables, outcomes, and dependencies per phase. |

---

## How These Artifacts Connect

```
Concept Narrative  →  "here is the problem and direction"
       ↓
   6-Pager        →  "here is the full case and experience"
       ↓
     PRD          →  "here is what we are building and how"  ← PM→Dev handoff
       ↓
 User Stories     →  "here is what Dev picks up as tickets"
       ↓
Acceptance Plan   →  "here is how QA validates it is done"
       ↓
Iteration Plan    →  "here is the roadmap beyond MVF"
```

The PM→Dev handoff is the PRD. Everything before it is for evaluation and alignment. Everything after it is execution-layer detail.
