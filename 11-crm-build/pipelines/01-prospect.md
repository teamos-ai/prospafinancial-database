---
id: crm-build-pipeline-1
title: 1 · Prospect — stage build spec
type: system
status: review
confidence: verified (today) / inferred (to build)
source: CRM build inventory 18 Sep 2026 + Role Task Matrix flow + pipeline mapping conversation; board prospa-build-blueprint (Desktop) · local http://localhost:5645
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, pipeline, prospect]
---

# 1 · Prospect

qualify new leads · advisers, deliberately manual.

**6 stages** · today: 0 built · 0 part-built or empty · 6 not built · **22 things to build** (15 new · 2 fix · 5 decision-first).

Legend: ✅ works today · ⚠️ exists but weak / placeholder · ❌ missing. Build kinds: **New** = does not exist · **Fix** = exists, change it · **Check** = verify a setting · **Decide** = Prospa decision first (see `decisions-register.md`).

---

## 1.1 · New Lead

> A new enquiry or partner referral lands, awaiting adviser review.

| | |
|---|---|
| Live stage name | `1 \|🌟New Lead` |
| Today | **Not built** |
| To build | **4** — 2 new · 1 fix · 1 decision-first |
| Mapping recommendation | Manual — Keep largely manual |

### To build here

- [ ] **Decide** — Confirm the entry points: partner forms (live) · website form · manual entry
- [ ] **New** — Adviser task on New Lead: review the lead, due 2 business days
- [ ] **New** — Source + referral partner stamped on every lead (check the live partner forms do this)
- [ ] **Fix** — Real win probabilities — the auto-defaults make forecasts meaningless

### What exists today

- ❌ No automation at any Prospect stage
- ✅ Partner referral forms already create a New Lead (test record, 16 Aug)
- ❌ Entry point beyond partner forms (website · manual) still being defined
- ❌ No welcome message, by the 10 Jul decision — partners sometimes submit a lead before the client knows

### How it should run — Lead intake (light)

1. **Trigger** — Partner intake form · website form · manual entry → **opportunity created** at New Lead
2. **Action** — Stamp **source** and referral partner on the contact
3. **Task** — Adviser: **review new lead** — due 2 business days
4. **Stop** — Nothing goes to the client until pre-screening says it is a genuine lead

Tags: `source:{{partner}}`

### Client receives

- None initially — no welcome message at this stage (10 Jul decision)

### Internal work

- Capture lead / contact and referral source
- Assign an adviser
- Create the opportunity in Prospect

### Decision needed

Front door: what counts as an enquiry, who handles it, and which event makes someone a "new client". Phase 0 is not in the matrix at all (file 2, §10 Q2–Q3).

Matrix refs: AD-024 · AD-037 · AD-045 · AD-047 · Phase 0 not in sheet

---

## 1.2 · Pre-screening

> Adviser assesses whether this is a genuine advice opportunity.

| | |
|---|---|
| Live stage name | `2 \|🚪Pre-screening` |
| Today | **Not built** |
| To build | **2** — 1 new · 1 fix · 0 decision-first |
| Mapping recommendation | Manual — Manual decision / gate |

### To build here

- [ ] **New** — Outcome recorded on the card: qualify · not ready · not a lead
- [ ] **Check** — Keep it a human gate — no client messages before the adviser decides

### What exists today

- ❌ Nothing built
- ✅ Definition agreed (10 Sep): the adviser records qualify · not ready · not a lead
- ✅ No automation before that decision — by design

### How it should run — Pre-screen outcome

1. **Trigger** — Adviser moves the card out of Pre-screening (the human decision)
2. **Branch** — → **Intro Booked** or **Qualified** · continue
3. **Branch** — → **Not Ready** · nurture rules (1.5)
4. **Branch** — → **Not A Lead** · close-out rules (1.6)

### Client receives

- Adviser-led if required — no automated message

### Internal work

- Adviser assesses the opportunity and records the outcome: qualify · not ready · not a lead

Matrix refs: Adviser · not itemised in the matrix (Advisor tab is empty)

---

## 1.3 · Intro Booked

> Free 15-minute intro call scheduled with an adviser.

| | |
|---|---|
| Live stage name | `3 \|🔒 Intro Booked` |
| Today | **Not built** |
| To build | **6** — 6 new · 0 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate |

### To build here

- [ ] **New** — Free 15-Minute Intro Call calendar for Monik, Neil, Peter
- [ ] **New** — Booking → confirmation email + SMS with the meeting link
- [ ] **New** — Reminders 24 h and 1 h before (timings to confirm)
- [ ] **New** — Booking moves the card to Intro Booked
- [ ] **New** — Adviser prep task: check contact details before the call
- [ ] **New** — No-show / cancel → reschedule path

### What exists today

- ❌ Nothing built
- ❌ The Free 15-Minute Intro Call calendar the definition relies on: confirm it exists

### How it should run — Intro call booked

1. **Trigger** — Appointment booked on the **Intro Call** calendar (prospect books, or admin on their behalf)
2. **Send** — Confirmation email + SMS with the meeting link
3. **Send** — Reminder 24 h and 1 h before
4. **Task** — Adviser: prep for intro call · check contact details
5. **Move** — Card → Intro Booked automatically on booking

Tags: `intro-booked`

### Client receives

- Booking confirmation
- Reminders before the call

### Internal work

- Adviser prep task
- Confirm CRM details are complete before the call

Matrix refs: AD-008 · AD-009 · AD-010 · AD-012 · AD-056 · AD-235

---

## 1.4 · Qualified

> Intro call confirms fit; the prospect wants to proceed to advice.

| | |
|---|---|
| Live stage name | `4 \|🎖️Qualified` |
| Today | **Not built** |
| To build | **3** — 2 new · 0 fix · 1 decision-first |
| Mapping recommendation | Automate — Automate handoff |
| Hands off to | 2 · Engagement |

### To build here

- [ ] **Decide** — Rule: move the card, or create a new opportunity per pipeline (D8)
- [ ] **New** — Mandatory-field check before the handoff: name, email, phone, source, adviser
- [ ] **New** — Automatic handoff to Engagement 2.1

### What exists today

- ❌ Nothing built
- ❌ Handoff into Engagement is manual: someone creates or moves the opportunity by hand
- ❌ Duplicate opportunities are switched off — "move" vs "new opportunity" needs a rule

### How it should run — Qualified → Engagement

1. **Trigger** — Card enters **Qualified**
2. **Action** — Verify record: name, email, phone, referral source, assigned adviser
3. **Move** — **Create the Engagement opportunity** (or move the card — rule per D8) at stage 2.1
4. **Handoff** — Engagement 2.1 fires the welcome pack

Tags: `qualified`

### Client receives

- Onboarding can begin — the welcome pack fires at Engagement 2.1

### Internal work

- Create / verify the client record
- Initiate Engagement (the "new client confirmed" event, T1)

### Decision needed

D8 · is stage progression done by a person or automatically at each gate? This is the first of six pipeline boundaries that are all manual today.

Matrix refs: AD-024 · AD-045 · AD-046 · T1 "new client confirmed"

---

## 1.5 · Not Ready

> A genuine prospect who is not ready to proceed right now.

| | |
|---|---|
| Live stage name | `5 \|🙈Not Ready` |
| Today | **Not built** |
| To build | **4** — 3 new · 0 fix · 1 decision-first |
| Mapping recommendation | Decision first — Automate once rules confirmed |
| Exit | nurture |

### To build here

- [ ] **Decide** — Nurture rules: what the newsletter is, how often, what brings a lead back
- [ ] **New** — Tag nurture · close open sales tasks · set a re-engagement date
- [ ] **New** — Newsletter nurture sequence (see "Newsletter nurture", around the journey)
- [ ] **New** — Re-engagement path back to Pre-screening

### What exists today

- ❌ Nothing built
- ❌ "Newsletter nurture" is a tag, not a pipeline — the nurture pipeline from 10 Jul was never built
- ❌ Tag name and the workflow behind it: unconfirmed

### How it should run — Not Ready → nurture

1. **Trigger** — Card enters **Not Ready**
2. **Action** — Tag **nurture** · close open sales tasks · set a re-engagement date
3. **Send** — Newsletter nurture sequence (content and cadence: not defined yet)
4. **Loop** — Re-engaged → back to Pre-screening

Tags: `nurture`

### Client receives

- Nurture / newsletter

### Internal work

- Apply the nurture classification
- Remove active sales tasks

### Decision needed

Nurture rules: what the newsletter is, how often, and what brings a Not Ready lead back.

Matrix refs: Not in sheet

---

## 1.6 · Not A Lead

> The enquiry is not a genuine advice opportunity.

| | |
|---|---|
| Live stage name | `6 \| Not A Lead✌️` |
| Today | **Not built** |
| To build | **3** — 1 new · 0 fix · 2 decision-first |
| Mapping recommendation | Decision first — Client decision required |
| Exit | closed out |

### To build here

- [ ] **Decide** — Definition: close out, or nurture? (Neil + Monik)
- [ ] **New** — Set status Lost + lost reason · close open tasks
- [ ] **Decide** — Close-out message, or silence

### What exists today

- ❌ Nothing built
- ❌ Live stage with no agreed definition (DRAFT)
- ❌ Outcomes are columns, not statuses — won / lost reporting stays empty

### How it should run — Not A Lead close-out

1. **Trigger** — Card enters **Not A Lead**
2. **Action** — Set opportunity status **lost** + lost reason · close tasks
3. **Send** — Optional close-out note (Prospa to decide)

Tags: `not-a-lead`

### Client receives

- Close-out message if required

### Internal work

- Close tasks
- Record the outcome (reason)

### Decision needed

Close out or nurture? And should the status be set to Lost so reporting works?

Matrix refs: Not in sheet

