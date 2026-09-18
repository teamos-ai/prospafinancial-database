---
id: crm-build-pipeline-3
title: 3 · Strategy Development — stage build spec
type: system
status: review
confidence: verified (today) / inferred (to build)
source: CRM build inventory 18 Sep 2026 + Role Task Matrix flow + pipeline mapping conversation; board prospa-build-blueprint (Desktop) · local http://localhost:5645
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, pipeline, strategy-development]
---

# 3 · Strategy Development

research, strategy meeting, product comparison, paraplanning request.

**6 stages** · today: 5 built · 1 part-built or empty · 0 not built · **18 things to build** (9 new · 6 fix · 3 decision-first).

Legend: ✅ works today · ⚠️ exists but weak / placeholder · ❌ missing. Build kinds: **New** = does not exist · **Fix** = exists, change it · **Check** = verify a setting · **Decide** = Prospa decision first (see `decisions-register.md`).

---

## 3.1 · Prepare for Strategy Meeting

> Associates complete the research for the adviser's strategy discussion.

| | |
|---|---|
| Live stage name | `1 \|🔱 Prepare for strategy meeting` |
| Today | **Built** |
| To build | **4** — 1 new · 2 fix · 1 decision-first |
| Mapping recommendation | Assist — Automate allocation; analysis remains human |

### To build here

- [ ] **Fix** — Assignee on all 5 tasks (associate role)
- [ ] **Fix** — Task naming: Wealth Builder vs Voyant Modelling
- [ ] **New** — Missing-information request path to the client
- [ ] **Decide** — "We're preparing your strategy" client note — nothing exists across 113 silent tasks

### What exists today

- ✅ 5 tasks on entry: Voyant modelling · INA · like-for-like quotes · research · strategy paper
- ⚠️ 4 of the 5 have no assignee
- ⚠️ The "Wealth Builder" action creates a task named "Voyant Modelling"
- ❌ The client receives nothing anywhere in this pipeline

### How it should run — Strategy prep allocation

1. **Trigger** — Card enters **3.1**
2. **Tasks** — Associate: INA · quotes · modelling · strategy paper — assigned to the associate, due dates set
3. **Task** — Missing info found → admin request to the client
4. **Send** — Optional: "we're preparing your strategy" note

### Client receives

- Missing-information requests where needed

### Internal work

- Fact-find review · analysis · modelling
- Missing information identified
- Summary and questions for the adviser
- INA · like-for-like quotes · financial modelling · strategy paper

Matrix refs: AA-023–034 · AA-060 · AA-061 · AA-007 · AA-066

---

## 3.2 · Strategy Meeting

> Adviser presents the proposed strategy to the client.

| | |
|---|---|
| Live stage name | `2 \|🗓️ Strategy Meeting` |
| Today | **Built** |
| To build | **3** — 1 new · 2 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate meeting admin |

### To build here

- [ ] **New** — Booking confirmation + reminders (Financial Planning calendar)
- [ ] **Fix** — Recap email actually sent by the workflow, not a task to write one
- [ ] **Fix** — One name for the stage everywhere

### What exists today

- ✅ Task: File Notes
- ⚠️ Task: "Strategy Discussion Email" — asks someone to write it; nothing is sent
- ⚠️ The stage goes by three names across trigger, branch and pipeline
- ❌ No confirmation or reminders for the meeting

### How it should run — Strategy meeting

1. **Trigger** — Strategy meeting **booked** → confirmation + reminders
2. **Trigger** — Meeting **held** → file-note task · strategy-discussion email (AI draft)
3. **Send** — Recap + action list to the client
4. **Move** — File note done → **Product Comparison**

### Client receives

- Confirmation + reminders
- The meeting
- Recap / action list

### Internal work

- Meeting prep
- Transcript / notes
- Capture direction and actions

Matrix refs: AD-008–012 · AA-019–022 · AA-051–056 · AD-068–074

---

## 3.3 · Product Comparison

> Associates compare risk, platform and modelling against the agreed direction.

| | |
|---|---|
| Live stage name | `3 \|🔬 Product Comparison` |
| Today | **Built** |
| To build | **2** — 1 new · 1 fix · 0 decision-first |
| Mapping recommendation | Automate — Internal task automation |

### To build here

- [ ] **Fix** — Assign to the associate role
- [ ] **New** — Completion of the three tasks advances the card

### What exists today

- ✅ 3 tasks: Risk · Platform · Wealth Builder Proposed
- ⚠️ All go to the contact's assigned user, whatever their role

### How it should run — Product comparison tasks

1. **Trigger** — Card enters **3.3**
2. **Tasks** — Associate: risk · platform · proposed modelling — due dates set
3. **Move** — All three complete → **Debrief**

### Client receives

- Normally none

### Internal work

- Research / product comparison: features, fees, options, alternatives, limitations, replacement info
- Comparison saved to SharePoint

Matrix refs: AA-038–049

---

## 3.4 · Debrief with Adviser

> Associate walks the adviser through the research; the adviser signs off.

| | |
|---|---|
| Live stage name | `4 \|🎉 Debrief research with adviser` |
| Today | **Built** |
| To build | **3** — 1 new · 1 fix · 1 decision-first |
| Mapping recommendation | Assist — Internal gate / task |

### To build here

- [ ] **New** — Adviser sign-off task (named adviser) — the gate to 3.5
- [ ] **Fix** — Clarify "Save to SP"
- [ ] **Decide** — Adviser sign-off ownership at the gates (D5)

### What exists today

- ✅ Task: "Save to SP" (SharePoint or Strategy Paper? term to confirm)
- ❌ No adviser sign-off task — the adviser has no task list anywhere in the matrix

### How it should run — Adviser sign-off

1. **Trigger** — Card enters **3.4**
2. **Task** — **Adviser**: sign off strategy + paraplanner instructions
3. **Gate** — Sign-off recorded → **Submit PP Request**

Tags: `strategy-signed-off`

### Client receives

- None

### Internal work

- Adviser review and sign-off
- Outstanding issues listed

### Decision needed

D5 · adviser decision and sign-off ownership at the major gates. The adviser is a dependency on 335 of 443 tasks but has no task list.

Matrix refs: AA-035–037 · adviser decision implied

---

## 3.5 · Submit PP Request

> The formal paraplanning request is raised for SOA production.

| | |
|---|---|
| Live stage name | `5 \|🥅 Submit PP Request` |
| Today | **Built** |
| To build | **3** — 3 new · 0 fix · 0 decision-first |
| Mapping recommendation | Strong automation — Strong automation / handoff |

### To build here

- [ ] **New** — Four-point completeness gate as subtasks: file · instructions · docs · research
- [ ] **New** — Paraplanning instructions template attached (AI draft candidate)
- [ ] **New** — Submission advances the card automatically

### What exists today

- ✅ Task: Send PPR
- ❌ No completeness gate before the request goes

### How it should run — Paraplanning handoff

1. **Trigger** — Card enters **3.5**
2. **Gate** — Checklist: file complete · instructions clear · docs current · research attached (AA-096–099)
3. **Task** — Associate: paraplanning instructions
4. **Move** — Request submitted → **PP Request Submitted** → Advice Production 4.1

Tags: `pp-requested`

### Client receives

- None

### Internal work

- File-completeness gate: file complete · instructions clear · documents current · research attached
- Paraplanning instructions, calculations, research, outstanding info

Matrix refs: AA-096–099 · AA-063–066 · AD-242

---

## 3.6 · PP Request Submitted

> Holding stage: the request is with the paraplanner.

| | |
|---|---|
| Live stage name | `6 \|👮‍♂️PP Request Submitted` |
| Today | **Fires · nothing** |
| To build | **3** — 2 new · 0 fix · 1 decision-first |
| Mapping recommendation | Automate — Automate |
| Hands off to | 4 · Advice Production |

### To build here

- [ ] **New** — Paraplanner task + notification · advice due date set
- [ ] **New** — Automatic handoff into Advice Production 4.1
- [ ] **Decide** — Or retire this holding stage (doc vs live drift)

### What exists today

- ⚠️ Fires the workflow, gets routed, then nothing happens
- ❌ The paraplanner is not notified
- ❌ The move into Advice Production is manual
- ❌ Live-only stage: the definitions doc hands off straight from 3.5

### How it should run — Notify paraplanner + handoff

1. **Trigger** — Card enters **3.6**
2. **Task** — **Paraplanner**: SOA due date set · added to the paraplanning queue
3. **Notify** — Paraplanner + associate notified
4. **Move** — **Create / move the opportunity to Advice Production 4.1**

### Client receives

- None

### Internal work

- Assign / notify the paraplanner
- Due date and work-queue tracking

Matrix refs: PP-079 · PP-080 · AA-104 · AD-075

