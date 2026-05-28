# Iteration Planning — OPRA Platform

**PRD reference:** PRD-001  
**Version:** 0.1

---

## Summary

Three phases from MVF to scale. Phase 1 makes the service deliverable. Phase 2 makes it repeatable and quality-controlled. Phase 3 makes it scalable and differentiated at the market level.

---

## Phase 1 — MVF

**Goal:** 1898 engagement teams can run a complete operationalization assessment and deliver a client-ready gap report.

**Success gate:** 2 live client engagements completed; reports delivered without manual reformatting.

### Deliverables

| Deliverable | Notes |
|---|---|
| Engagement creation and management | Metadata, Draft state, engagement lead ownership |
| Tool inventory input | Manual form; defined category taxonomy |
| Operationalization checklist | 6 dimensions per tool, 3-point scale, root cause capture |
| Scoring engine | Server-side; tool-level percentage; color thresholds |
| Root cause heat map | Aggregated view by category |
| Remediation roadmap generation | Priority and effort sort; one action per gap |
| Client gap report export | PDF + Word; 1898 brand template |
| Practice lead review view | All-engagements read-only view |
| Role-based access control | Engagement Lead vs Practice Lead |

### Pre-Phase 1 dependencies (blocking)

- Operationalization rubric reviewed and signed off by named OT security SME
- 1898 client report template finalized and approved
- Hosting environment confirmed

### Phase 1 exclusions

- Client portal
- API ingestion from tool vendors
- Cross-engagement analytics
- Multi-site rollup
- Re-assessment tracking

---

## Feature & Outcome Progression — Phase 1

| Feature | What users can do after this feature ships |
|---|---|
| Engagement creation | Engagement lead can start a new client project with a clean record |
| Tool inventory | Engagement lead can document a client's full security tool environment in one place |
| Checklist engine | Engagement lead can score every tool consistently using a structured, defensible framework |
| Scoring and heat map | Engagement lead can see at a glance which tools are operationalized and where the gaps cluster |
| Roadmap generation | Engagement lead can give the client a prioritized action plan without manual analysis |
| Report export | Engagement lead can deliver a client-ready document without any reformatting |
| Practice lead view | Practice lead can ensure every delivered OPRA assessment meets a consistent quality bar |

---

## Phase 2 — Operationalization and Validation

**Goal:** Service is repeatable and quality-controlled. Re-assessments are trackable. Practice lead has cross-engagement visibility.

**When to start:** After 2 successful Phase 1 engagements. Phase 2 scope is informed by what Phase 1 delivery surfaces.

### Deliverables

| Deliverable | Notes |
|---|---|
| Re-assessment tracking | Link a new engagement to a prior engagement for the same client; score-over-time view |
| Cross-engagement aggregate view | Practice lead only; no cross-engagement-lead client data exposure |
| Improved report templates | Based on Phase 1 feedback from delivered reports |
| Checklist revision workflow | Ability to update the rubric (add/modify dimensions) without breaking existing engagement records |

### Feature & Outcome Progression — Phase 2

| Feature | What users can do |
|---|---|
| Re-assessment tracking | Practice lead can show a client their score improvement over time |
| Cross-engagement aggregate | Practice lead can identify which gap types are most common across clients — enables practice-level pattern insight |
| Rubric versioning | PM can update the operationalization rubric as the OT landscape changes without invalidating prior assessments |

---

## Phase 3 — Scale

**Goal:** Service is scalable. Clients can participate directly. Cross-client benchmarking creates differentiated market insight.

**When to start:** When Phase 2 is stable and at least 5–10 engagements have been completed.

### Deliverables

| Deliverable | Notes |
|---|---|
| Client self-service input | Client logs in to input their own tool inventory; engagement lead reviews and approves before scoring |
| API ingestion | Pull asset and coverage data from Dragos, Claroty, Nozomi APIs to pre-populate checklist inputs |
| Cross-client benchmark dataset | Aggregated, anonymized operationalization scores by sector, tool category, and organization size |
| Benchmark reporting | Clients receive their score in context of sector peers (no individual client data exposed) |

### Feature & Outcome Progression — Phase 3

| Feature | What users can do |
|---|---|
| Client self-service | Engagement lead time per assessment reduced; client prepares the inventory before the first meeting |
| API ingestion | Checklist inputs for coverage and connectivity are pre-populated from the tool itself; reduces manual entry and confirms data accuracy |
| Benchmark reporting | Client can see their operationalization score relative to sector peers — gives the gap report external context and strengthens the remediation business case |

---

## Dependencies and Sequencing

```
Rubric SME sign-off ──► Phase 1 dev starts
1898 report template ──► Export feature built (within Phase 1)
2 Phase 1 engagements ──► Phase 2 starts
5–10 engagements ──► Phase 3 scope confirmed

Phase 3: client portal ──► blocked on legal review (client data handling)
Phase 3: API ingestion ──► blocked on vendor API access agreements (Dragos, Claroty)
Phase 3: benchmark dataset ──► blocked on legal review (data aggregation terms)
```

---

## Risks by Phase

| Phase | Risk | Mitigation |
|---|---|---|
| 1 | Rubric not signed off before dev starts → invalid scoring model | Name the SME reviewer in project kickoff; block checklist feature on their approval |
| 1 | Report template not ready before export feature → launch delay | Parallelize template design with dev; export is not on the critical path until Phase 1 final |
| 2 | Re-assessment data model incompatible with Phase 1 engagement records | Design the data model in Phase 1 to support versioning, even if the UI feature ships in Phase 2 |
| 3 | Client data handling compliance → GDPR, CCPA, sector-specific regs | Legal review must precede client portal build; do not assume internal-only data handling rules apply |
| 3 | Vendor API access → Dragos, Claroty terms may restrict third-party ingestion | Engage vendors in Phase 2 to confirm API access terms before committing to Phase 3 build |
