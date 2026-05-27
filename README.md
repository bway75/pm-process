# Practice Process

How something new gets requested, reviewed, documented, built, delivered, and communicated.

This repo covers two levels:

1. **The operating model** — the end-to-end pipeline from intake to sales-readiness (Steve's "machine")
2. **The PM documentation process** — the artifact-production framework that operates inside the delivery stage

## What's Here

| File | What It Is |
|---|---|
| [practice-operating-model.md](practice-operating-model.md) | The six-stage operating model — intake through sales-readiness gate |
| [pm-documentation-process.md](pm-documentation-process.md) | PM doc process — key principles and decision rules for the delivery stage |
| [pm-docs-gpt-prompt.md](pm-docs-gpt-prompt.md) | Full PM doc spec — GPT manifest, Claude setup guide, complete instructions |

## The Operating Model

```
Intake → Vetting & Assessment → Pipeline → Delivery → Distribution & Awareness → Sales-Readiness Gate
```

The PM documentation process (below) operates inside **Delivery**.

## The PM Documentation Process

```
Concept Narrative → 6-Pager → PRD (7-Section) → JTBD & User Stories → Acceptance Plan → Iteration Planning
```

For larger initiatives, use the JTBD-sliced flow:

```
MVP Definitions → PRDs per JTBD/function → User Stories → Acceptance Criteria / Test Cases
```

An **umbrella Initiative Brief** holds the JTBD-sliced flow together.

## Quick Start (PM Docs)

1. Read `pm-docs-gpt-prompt.md` — it has the full operating spec
2. Deploy to ChatGPT (paste Instructions section into GPT Configure UI) or Claude (paste into Project custom instructions)
3. Update the Role line in the instructions to reflect your domain before deploying
4. Upload your own domain reference document as the knowledge file

## Supported PM Deliverables

Concept Narrative · 6-Pager · PRD (7-Section) · JTBD & User Stories · Feature & Outcome Progression · Iteration Planning · Acceptance Plan · PR/FAQ · Executive Slide Summary
