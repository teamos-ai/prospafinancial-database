---
id: crm-build-around-the-journey
title: Around the journey — continuous operational layer
type: system
status: review
confidence: inferred
source: Role Task Matrix flow analysis 18 Sep 2026; board prospa-build-blueprint (Desktop) · local http://localhost:5645
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, operations]
---

# Around the journey

149 matrix tasks run continuously and should not be forced into a pipeline stage. Plus the newsletter nurture, which lives outside the seven pipelines by tag.

## Daily operations (7 tasks)

Inbox triage · admin enquiries · outstanding client actions · advice questions escalated · tasks due today · overdue tasks · end-of-day notes.

**Where it lives:** Task views + saved lists per role; overdue escalation to a manager. Nothing to build per stage.

Matrix refs: AD-006 · AD-007 · AD-018–021 · AD-023

## CRM & data management (14 tasks)

Contact updates · communications log · document links · stage updates · task creation · duplicates · naming · mandatory fields · data-quality checks.

**Where it lives:** Define mandatory fields, naming convention and dedupe rules once, then enforce at entry rather than policing after. Depends on D7 (system of record).

Matrix refs: AD-025–038

## Ad hoc client administration (24 tasks)

Contact, bank, beneficiary and pension changes · duplicate / tax / Centrelink documents · portal access · withdrawals · provider delays · complaints · signing · filing.

**Where it lives:** A request-intake form → task templates per request type, outside the pipeline.

Matrix refs: AD-168–191

## Authorities & provider requests (11 tasks)

Prepare → submit → track → follow up authorities; request policy, super, investment, transaction, cost-base and Centrelink information; authority expiry.

**Where it lives:** An authority-expiry field + reminder — an expired authority silently blocks the provider lane.

Matrix refs: AD-139–149

## Work queues & quality (5 tasks)

Associate work queue · handoff reviews · delay escalation · paraplanning queue · advice due dates.

**Where it lives:** One task board with due dates instead of three separate queues.

Matrix refs: AA-102–104 · PP-079 · PP-080

## Technical research & knowledge (10 tasks)

Super, tax, social-security, product and insurance rules · references · assumptions · knowledge sharing · templates.

**Where it lives:** Stays in SharePoint / Xplan — not a CRM concern.

Matrix refs: PP-069–078

## Business administration (17 tasks)

Manuals · templates · naming standards · provider and supplier records · registers · dashboards · weekly outstanding-task report · bottlenecks · archiving.

**Where it lives:** Dashboards and the weekly report come straight from pipeline data once won / lost statuses are real.

Matrix refs: AD-192–208 · AD-253

## Process improvement, AI & SOPs (61 tasks)

Map the five workflows · find waste · 20 automation investigations (AD-234–253) · 12 SOP tasks.

**Where it lives:** This board is that map — each investigation sits on the stage it automates.

Matrix refs: AD-209–265 · AA-105 · PP-086–088

---

## outside · Newsletter nurture

> Outside the seven pipelines, by tag. Fed by Not Ready (1.5) and Opportunity Lost (5.4).

| | |
|---|---|
| Live stage name | `tag · no pipeline` |
| Today | **Not captured** |
| To build | **3** — 2 new · 0 fix · 1 decision-first |
| Mapping recommendation | Decision first — Automate once rules confirmed |

### To build here

- [ ] **Decide** — Content + cadence from Prospa
- [ ] **New** — Nurture workflow: send → wait → send, until re-engaged or unsubscribed
- [ ] **New** — Exit rule: reply or booking → adviser alert · back into Prospect

### What exists today

- ❌ The definitions doc sends Not Ready + Opportunity Lost to "newsletter nurture" by tag
- ❌ The tag name and the workflow behind it were not in any export
- ❌ The nurture pipeline mentioned on 10 Jul was never built

### How it should run — Newsletter nurture

1. **Trigger** — Tag **nurture** applied (Not Ready · Opportunity Lost)
2. **Loop** — Send → wait → send, until re-engaged or unsubscribed
3. **Exit** — Reply or booking → alert adviser · back into Prospect

Tags: `nurture`

### Client receives

- Newsletter / education sequence — content not defined

### Internal work

- Tag-driven; no stage to move

Matrix refs: File 1 §4.5 · Q4

