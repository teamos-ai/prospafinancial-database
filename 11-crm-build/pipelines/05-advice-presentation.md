---
id: crm-build-pipeline-5
title: 5 · Advice Presentation — stage build spec
type: system
status: review
confidence: verified (today) / inferred (to build)
source: CRM build inventory 18 Sep 2026 + Role Task Matrix flow + pipeline mapping conversation; board prospa-build-blueprint (Desktop) · local http://localhost:5645
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, pipeline, advice-presentation]
---

# 5 · Advice Presentation

present the SOA · accept, decline or wait.

**5 stages** · today: 1 built · 2 part-built or empty · 2 not built · **18 things to build** (12 new · 3 fix · 3 decision-first).

Legend: ✅ works today · ⚠️ exists but weak / placeholder · ❌ missing. Build kinds: **New** = does not exist · **Fix** = exists, change it · **Check** = verify a setting · **Decide** = Prospa decision first (see `decisions-register.md`).

---

## 5.1 · Advice Presentation

> Adviser presents the SOA and seeks a decision.

| | |
|---|---|
| Live stage name | `1 \|🫆Advice Presentation Meeting` |
| Today | **Built** |
| To build | **4** — 2 new · 2 fix · 0 decision-first |
| Mapping recommendation | Assist — Human meeting + automated admin |

### To build here

- [ ] **Check** — Verify the trigger points at this stage
- [ ] **New** — Confirmation + reminders for the presentation
- [ ] **New** — Decision recorded on the card: accepted · declined · waiting
- [ ] **Fix** — Stage order: Waiting On Decision before Won / Lost

### What exists today

- ✅ Task: File Notes, due 2 days (weekends counted)
- ⚠️ The trigger may not point at this stage — the exported stage reference was malformed
- ❌ No confirmation or reminders for the presentation
- ❌ Waiting On Decision sits after Won / Lost in the stage order

### How it should run — Presentation meeting

1. **Trigger** — Presentation booked → confirmation + reminders
2. **Trigger** — Meeting held → file-note task · decision recorded
3. **Branch** — Accepted → 5.2 · Declined → 5.4 · No decision → 5.5

### Client receives

- Meeting reminders
- The presentation

### Internal work

- Capture presentation notes
- Record the client decision

Matrix refs: Phase 5 not itemised · AD-008–012 · AA-051 · AD-068

---

## 5.2 · Instructions to Assistant

> Associate writes file notes and hands implementation instructions to admin.

| | |
|---|---|
| Live stage name | `2 \|🎩Provide instructions to assistant on implementation step` |
| Today | **Fires · nothing** |
| To build | **2** — 2 new · 0 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate handoff |

### To build here

- [ ] **New** — Associate brief task: review requirements · brief admin
- [ ] **New** — Handoff to admin recorded on the card

### What exists today

- ⚠️ Branch exists, no actions
- ❌ Nobody gets a task to write the notes or hand over the instructions
- ⚠️ Sits before Advice WON although acceptance triggers it

### How it should run — Implementation brief

1. **Trigger** — Card enters **5.2**
2. **Task** — **Associate**: review implementation requirements · brief admin (AA-074, AA-075)
3. **Move** — Brief done → **Advice WON**

### Client receives

- Normally none

### Internal work

- Implementation brief
- Work allocation to admin

Matrix refs: AA-074 · AA-075 · PP-043 · PP-085

---

## 5.3 · Advice WON

> Client accepts and signs the Authority to Proceed.

| | |
|---|---|
| Live stage name | `3 \|🏁Advice WON` |
| Today | **Fires · nothing** |
| To build | **5** — 4 new · 0 fix · 1 decision-first |
| Mapping recommendation | Strong automation — Critical automation trigger |
| Hands off to | 6 · Implementation |

### To build here

- [ ] **New** — ATP signing flow (CRM signing, or DocuSign where a provider demands it)
- [ ] **New** — Confirmation email: what happens next, who to expect
- [ ] **New** — Won status set, so reporting works
- [ ] **New** — Automatic handoff to Implementation 6.1
- [ ] **Decide** — First service agreement · fee arrangement · advice-fee invoice (D6)

### What exists today

- ⚠️ Branch exists, no actions
- ❌ No confirmation email to the client
- ❌ Status is not set to won
- ❌ Nothing moves the client into Implementation

### How it should run — Advice won

1. **Trigger** — Card enters **Advice WON**
2. **Gate** — Signed ATP on file (upload or e-sign complete)
3. **Send** — Confirmation: what happens next, who to expect
4. **Action** — Opportunity status = **won**
5. **Move** — **Create / move to Implementation 6.1**

Tags: `advice-won` · `atp-signed`

### Client receives

- Acceptance / next-steps confirmation

### Internal work

- Verify the signed Authority to Proceed
- Initiate Implementation

### Decision needed

D6 · exact fee, consent and ongoing-service events: the first service agreement, fee arrangement and advice-fee invoice are not in the matrix.

Matrix refs: Not in sheet · AD-188 · AD-162

---

## 5.4 · Opportunity Lost

> Client declines to proceed with the advice.

| | |
|---|---|
| Live stage name | `4 \|😔Opportunity Lost` |
| Today | **Not captured** |
| To build | **4** — 2 new · 1 fix · 1 decision-first |
| Mapping recommendation | Decision first — Automate after rules confirmed |
| Exit | nurture |

### To build here

- [ ] **Check** — Get the rest of the export before touching this stage
- [ ] **New** — Lost status + reason · close open tasks
- [ ] **Decide** — Decline note tone + nurture rules
- [ ] **New** — Nurture handoff

### What exists today

- ❌ Not captured — the workflow export cut off before this branch

### How it should run — Lost → nurture

1. **Trigger** — Card enters **Opportunity Lost**
2. **Action** — Status = **lost** + lost reason · close open tasks
3. **Send** — Decline note (tone per Prospa) → tag **nurture**

Tags: `nurture`

### Client receives

- Decline / nurture communication

### Internal work

- Record the loss + reason
- Close tasks
- Apply nurture rules

### Decision needed

Nurture rules and tone for a declined client.

Matrix refs: Not in sheet (decline path)

---

## 5.5 · Waiting On Decision

> The client has not said yes or no — the "on the fence" case.

| | |
|---|---|
| Live stage name | `5 \| ⏳Waiting On Decision` |
| Today | **Not built** |
| To build | **3** — 2 new · 0 fix · 1 decision-first |
| Mapping recommendation | Decision first — Client must define cadence / escalation |
| Exit | holding |

### To build here

- [ ] **Decide** — Sign-off on the stage itself · cadence + escalation (D4)
- [ ] **New** — Adviser follow-up task at day X · reminders at day X, Y
- [ ] **New** — Exit → Advice WON or Opportunity Lost; escalate after Z days

### What exists today

- ❌ No trigger, no branch
- ❌ Added 10 Sep after the definitions doc went out; not signed off by Monik + Neil

### How it should run — Waiting on decision

1. **Trigger** — Card enters **Waiting On Decision**
2. **Task** — Adviser: outbound call at day X (cadence per D4)
3. **Send** — Gentle reminders at day X · Y
4. **Exit** — → Advice WON or Opportunity Lost; escalate after Z days

### Client receives

- Follow-up / reminders

### Internal work

- Adviser follow-up task
- Elapsed-time monitoring

### Decision needed

D4 · cadence and escalation rules for Waiting On Decision.

Matrix refs: Not in sheet · AD-162 (generic)

