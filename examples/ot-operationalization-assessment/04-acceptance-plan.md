# Acceptance Plan — OPRA Platform MVF

**PRD reference:** PRD-001  
**User Stories reference:** US-001 through US-007  
**Version:** 0.1

---

## Scope

Covers Phase 1 (MVF) only. Tests are organized by workflow — each section maps to one or more user stories.

Pass/fail for launch: all Critical tests must pass. Major tests must pass or have a documented mitigation. Minor tests are non-blocking.

---

## TC-01 — Engagement Creation

**Story ref:** US-001  
**Severity:** Critical

| Test | Input | Expected result | Pass/Fail |
|---|---|---|---|
| TC-01-01 | Submit engagement form with all required fields | Engagement created in Draft state; visible to engagement lead and practice lead | |
| TC-01-02 | Submit engagement form with client name missing | Form blocked; error shown on client name field | |
| TC-01-03 | Submit engagement form with industry segment missing | Form blocked; error shown on industry segment field | |
| TC-01-04 | Create two engagements with identical client name and site | Warning surfaced; second engagement still created (soft block) | |
| TC-01-05 | Engagement lead field | Auto-populated with logged-in user; not editable | |
| TC-01-06 | Navigate to tool inventory after creation | Tool inventory section available and empty | |

---

## TC-02 — Tool Inventory

**Story ref:** US-002  
**Severity:** Critical

| Test | Input | Expected result | Pass/Fail |
|---|---|---|---|
| TC-02-01 | Add tool with all required fields | Tool added to inventory; checklist becomes available | |
| TC-02-02 | Add tool with tool name missing | Form blocked; error shown | |
| TC-02-03 | Add tool with category not in defined list | Form blocked; only defined categories selectable | |
| TC-02-04 | Edit a tool after adding it (engagement in Draft) | Edit succeeds; updated values saved | |
| TC-02-05 | Delete a tool with completed checklist | Confirmation prompt shown; on confirm, tool and checklist data removed | |
| TC-02-06 | Delete a tool and cancel at confirmation | Tool and checklist data unchanged | |
| TC-02-07 | Add 10 tools to a single engagement | All 10 tools display in inventory; no limit error | |

---

## TC-03 — Operationalization Checklist

**Story ref:** US-003  
**Severity:** Critical

| Test | Input | Expected result | Pass/Fail |
|---|---|---|---|
| TC-03-01 | Score all 6 dimensions with score = 2 | Checklist marked Complete; tool score = 100%; no root cause required | |
| TC-03-02 | Score one dimension with 0; leave root cause blank | Checklist cannot be marked Complete; root cause field error shown | |
| TC-03-03 | Score one dimension with 1; select a root cause category | Checklist marks Complete when remaining dimensions scored | |
| TC-03-04 | Calculate score: 3 dimensions at 2, 3 dimensions at 1 | Score = (3×2 + 3×1) / 12 = 9/12 = 75% | |
| TC-03-05 | Calculate score: all dimensions at 0 | Score = 0% | |
| TC-03-06 | Partial save: score 3 dimensions, close browser, reopen | Previously entered scores retained; checklist shows Incomplete | |
| TC-03-07 | Re-open a Completed checklist while engagement is Draft | Checklist opens for editing; score recalculates on save | |
| TC-03-08 | Attempt to edit checklist after roadmap is generated | Edit blocked; checklist locked | |
| TC-03-09 | Score entered directly into score field (not via UI scale) | Not possible; score is server-derived, no direct input | |

**Edge cases:**
- Tool with installation status = "not installed": checklist is still available; engagement lead expected to score 0 on installation/connectivity dimension
- All dimensions scored 0: valid state; score = 0%, all root causes required

---

## TC-04 — Scoring Summary and Heat Map

**Story ref:** US-004  
**Severity:** Major

| Test | Input | Expected result | Pass/Fail |
|---|---|---|---|
| TC-04-01 | All tool checklists complete; navigate to summary | Summary view accessible; per-tool scores and overall score displayed | |
| TC-04-02 | One checklist incomplete; navigate to summary | Summary view blocked with explanation | |
| TC-04-03 | Tool with score < 40% | Displayed with red indicator | |
| TC-04-04 | Tool with score between 40–70% | Displayed with amber indicator | |
| TC-04-05 | Tool with score > 70% | Displayed with green indicator | |
| TC-04-06 | Root cause heat map | Count per root cause category matches sum of recorded root causes across all tools | |
| TC-04-07 | Navigate from summary to individual tool checklist | Checklist opens; can be reviewed and revised | |
| TC-04-08 | Overall engagement score | Average of all tool scores, rounded to nearest integer | |

---

## TC-05 — Remediation Roadmap Generation

**Story ref:** US-005  
**Severity:** Critical

| Test | Input | Expected result | Pass/Fail |
|---|---|---|---|
| TC-05-01 | Generate roadmap with all checklists complete | Roadmap generated; one action per dimension with score < 2 | |
| TC-05-02 | Generate roadmap with one checklist incomplete | Generation blocked | |
| TC-05-03 | Dimension with score = 2 | No action generated for that dimension | |
| TC-05-04 | Detection-critical tool (passive detection) with score < 40% | Appears as Priority 1 | |
| TC-05-05 | Non-critical tool with score < 40% | Appears as Priority 2 | |
| TC-05-06 | Two Priority 1 actions — one S effort, one M effort | S effort action appears first | |
| TC-05-07 | Revise a checklist after roadmap generated | Engagement returns to Checklists Complete state; roadmap must be regenerated | |
| TC-05-08 | Roadmap action count | Equals the total number of dimensions across all tools that scored < 2 | |

**Edge case:**
- All dimensions on all tools score 2 (fully operationalized): roadmap generates with zero actions; engagement can still be exported

---

## TC-06 — Report Export

**Story ref:** US-006  
**Severity:** Critical

| Test | Input | Expected result | Pass/Fail |
|---|---|---|---|
| TC-06-01 | Export PDF from engagement in Roadmap Generated state | PDF file generated using 1898 template; download triggered | |
| TC-06-02 | Export Word from engagement in Roadmap Generated state | .docx file generated using 1898 template; download triggered | |
| TC-06-03 | Attempt export before roadmap is generated | Export option not available or disabled with explanation | |
| TC-06-04 | Verify PDF contents | Contains: engagement summary, overall score, per-tool findings, root cause heat map, prioritized roadmap in priority order | |
| TC-06-05 | Verify Word contents | Same as PDF; document uses correct fonts, colors, logo, and footer per 1898 template | |
| TC-06-06 | Export action logged | Timestamp and format recorded in engagement record | |
| TC-06-07 | Attempt to edit checklist after export | Edit blocked; engagement is in Exported state | |
| TC-06-08 | Manual formatting required post-export | None required; report passes 1898 client delivery review as-is | |

**Operational validation:**
- Have a practice lead review an exported report against the 1898 client delivery standard before marking this test complete
- Confirm the report can be emailed directly to a client without additional editing

---

## TC-07 — Role and Access Control

**Story ref:** US-007, US-001  
**Severity:** Critical

| Test | Input | Expected result | Pass/Fail |
|---|---|---|---|
| TC-07-01 | Engagement Lead A views engagement list | Only their own engagements visible | |
| TC-07-02 | Engagement Lead A attempts to open Engagement Lead B's engagement | Access denied | |
| TC-07-03 | Practice Lead views engagement list | All engagements visible regardless of engagement lead | |
| TC-07-04 | Practice Lead opens any engagement | Read-only access; no edit controls visible | |
| TC-07-05 | Practice Lead attempts to edit checklist data | Edit blocked | |
| TC-07-06 | Unauthenticated user attempts to access any page | Redirected to login | |
| TC-07-07 | Engagement Lead attempts to access practice lead view | Access denied | |

---

## TC-08 — End-to-End Workflow

**Severity:** Critical — must run as a complete scenario, not unit-by-unit

**Scenario:** New engagement, 3 tools, full assessment, roadmap generation, report export

| Step | Action | Expected result | Pass/Fail |
|---|---|---|---|
| 1 | Create engagement: "Acme Power, Electric Utility, Main Plant" | Engagement created in Draft | |
| 2 | Add 3 tools: passive detection (installed, active), SIEM (installed, active), asset management (installed, expired) | 3 tools in inventory; 3 checklists available | |
| 3 | Complete passive detection checklist: dimensions 1–3 score 2, dimensions 4–6 score 0 with root causes | Score = 6/12 = 50%; 3 root causes recorded | |
| 4 | Complete SIEM checklist: all dimensions score 1 with root causes | Score = 6/12 = 50%; 6 root causes recorded | |
| 5 | Complete asset management checklist: dimension 1 score 2, dimensions 2–6 score 0 with root causes | Score = 2/12 = 17%; 5 root causes recorded | |
| 6 | Navigate to scoring summary | 3 tool scores shown; passive detection = amber, SIEM = amber, asset management = red; overall = ~39% | |
| 7 | Generate roadmap | Roadmap generated; asset management and passive detection Priority 1 (detection-critical, <40%); SIEM Priority 2; effort sort applied within tiers | |
| 8 | Export PDF | PDF downloaded; all sections present; uses 1898 template | |
| 9 | Confirm engagement state | Exported state; edit blocked | |
| 10 | Practice lead opens engagement | All data visible; read-only | |

**Time target:** An engagement lead completing steps 1–9 for the first time should complete within 45 minutes for this 3-tool scenario. Extrapolates to ≤ 4 hours active time for a typical 10–15 tool client environment.

---

## Non-Functional Requirements

| Requirement | Target | Severity |
|---|---|---|
| Page load time | < 2 seconds for all views | Major |
| Report generation time | < 30 seconds for PDF or Word | Major |
| Concurrent engagements | Support at least 10 active engagements without performance degradation | Major |
| Session handling | Inactive session expires after 60 minutes; partial checklist saves are retained | Minor |
| Browser support | Chrome and Edge (latest stable); Firefox acceptable but not required | Minor |
