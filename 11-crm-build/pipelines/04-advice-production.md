---
id: crm-build-pipeline-4
title: 4 · Advice Production — stage build spec
type: system
status: review
confidence: verified (today) / inferred (to build)
source: CRM build inventory 18 Sep 2026 + Role Task Matrix flow + pipeline mapping conversation; board prospa-build-blueprint (Desktop) · local http://localhost:5645
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, pipeline, advice-production]
---

# 4 · Advice Production

SOA drafted, peer-reviewed, finalised, implementation docs.

**6 stages** · today: 4 built · 2 part-built or empty · 0 not built · **20 things to build** (13 new · 4 fix · 3 decision-first).

Legend: ✅ works today · ⚠️ exists but weak / placeholder · ❌ missing. Build kinds: **New** = does not exist · **Fix** = exists, change it · **Check** = verify a setting · **Decide** = Prospa decision first (see `decisions-register.md`).

---

## 4.1 · Prepare SOA

> Paraplanner drafts the Statement (or Record) of Advice.

| | |
|---|---|
| Live stage name | `1 \|☂️Prepare SOA` |
| Today | **Built** |
| To build | **4** — 2 new · 1 fix · 1 decision-first |
| Mapping recommendation | Automate — Automate assignment / tracking |

### To build here

- [ ] **Fix** — Task to the paraplanner role
- [ ] **New** — Advice due-date field drives the task
- [ ] **New** — Clarification loop back to the associate when instructions are incomplete
- [ ] **Decide** — "Your advice is being prepared, expected by …" client note

### What exists today

- ✅ Task: Prepare Statement of Advice, due 2 days (weekends counted)
- ⚠️ Goes to the contact's assigned user — as does every task in this pipeline
- ❌ The client receives nothing while the advice is prepared

### How it should run — SOA production

1. **Trigger** — Card enters **4.1**
2. **Task** — **Paraplanner**: prepare SOA / ROA (fork: PP-048) — due = advice due date
3. **Loop** — Instructions incomplete → return to associate (PP-082) · queries logged
4. **Send** — Optional client note: "your advice is being prepared, expected by …"
5. **Move** — Draft complete → **Peer-Review SOA**

Tags: `soa-in-progress`

### Client receives

- Normally none

### Internal work

- Paraplanner intake: missing instructions early → return for clarification
- Modelling · research · SOA / ROA drafting
- Technical queries tracked

Matrix refs: PP-006–023 · PP-081–084 · PP-048 · PP-024–052 · AA-100 · AA-101

---

## 4.2 · Peer-Review SOA

> Associate independently checks the SOA. Hard gate.

| | |
|---|---|
| Live stage name | `2 \|🫣Peer-Review SOA` |
| Today | **Built** |
| To build | **3** — 2 new · 1 fix · 0 decision-first |
| Mapping recommendation | Automate — Automated task + hard gate · **hard gate** |

### To build here

- [ ] **Fix** — Reviewer = associate role, never the preparer
- [ ] **New** — Gate enforced: no advance until signed off
- [ ] **New** — Amendment loop back to Prepare SOA

### What exists today

- ✅ Task: Review SoA
- ⚠️ Reviewer = preparer — same assigned user
- ⚠️ Not a gate: the card can move on before the review is done

### How it should run — Peer review gate

1. **Trigger** — Card enters **4.2**
2. **Task** — **Associate** (not the preparer): review SOA — QC list as subtasks
3. **Gate** — Review signed off → allow **Provide Implementation Instructions**; otherwise back to 4.1

Tags: `peer-reviewed`

### Client receives

- None

### Internal work

- Associate review: factual, technical, compliance checks
- Amendments back to the paraplanner or adviser

Matrix refs: PP-053–065 · AA-067–073

---

## 4.3 · Implementation Instructions

> Instructions drafted for the admin team to execute after approval.

| | |
|---|---|
| Live stage name | `3 \|👮‍♀️Provide Implementation Instructions` |
| Today | **Built** |
| To build | **3** — 2 new · 0 fix · 1 decision-first |
| Mapping recommendation | Assist — Internal task / AI-assisted drafting candidate |

### To build here

- [ ] **Decide** — Name the owner: the paraplanner writes (PP-043), the associate briefs (AA-075)
- [ ] **New** — Instructions template by product lane
- [ ] **New** — Attachment advances the card

### What exists today

- ✅ Task: Provide Implementation Instructions
- ⚠️ No owner named for this stage in the definitions

### How it should run — Implementation instructions

1. **Trigger** — Card enters **4.3**
2. **Task** — Owner TBC: instructions attached to the file
3. **Move** — Attached → **SoA Finalise**

### Client receives

- None

### Internal work

- Create implementation instructions
- Product / action requirements per lane

Matrix refs: PP-043 · AA-072 · AD-242

---

## 4.4 · SoA Finalise

> Adviser final check and approval.

| | |
|---|---|
| Live stage name | `4 \|📧SoA Finalise` |
| Today | **Placeholders** |
| To build | **3** — 1 new · 1 fix · 1 decision-first |
| Mapping recommendation | Automate — Automate after adviser approval |

### To build here

- [ ] **New** — Adviser approval task (named adviser)
- [ ] **Fix** — Move the booking sequence to Ready for Advice (4.6); delete the blind 3-day waits here
- [ ] **Decide** — Adviser sign-off ownership (D5)

### What exists today

- ⚠️ Wait 3 d → "Email Booking Link" — blank
- ⚠️ Wait 3 d → "A reminder to book in" — blank
- ❌ No booking link in either email
- ❌ The reminder fires even if the client has booked
- ❌ The sequence starts before the docs are ready (4.5) and before Ready for Advice (4.6)

### How it should run — SOA approved

1. **Trigger** — **Adviser approves** (task complete / stage move)
2. **Move** — → **Prepare Implementation Docs**; the invite sequence starts at 4.6, not here
3. **Note** — 3-day minimum wait enforced by the presentation calendar's booking window, not a blind wait step

Tags: `soa-approved`

### Client receives

- Advice-presentation booking invitation (after approval, minimum 3-day wait per the definition)

### Internal work

- Adviser final review and sign-off

### Decision needed

D5 · adviser sign-off ownership.

Matrix refs: PP-066–068

---

## 4.5 · Implementation Docs

> Admin prepare and upload the implementation document pack.

| | |
|---|---|
| Live stage name | `5 \|🎪Prepare Implementation Docs` |
| Today | **Built** |
| To build | **3** — 2 new · 1 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate checklist / tasks |

### To build here

- [ ] **Fix** — Admin-role assignee
- [ ] **New** — Checklist by product lane
- [ ] **New** — Completion advances to Ready for Advice

### What exists today

- ✅ 2 tasks: Upload to MP Vault · Upload to SP
- ⚠️ Both to the contact's assigned user

### How it should run — Implementation pack

1. **Trigger** — Card enters **4.5**
2. **Tasks** — **Admin**: forms by lane · pack · upload to MP vault + SharePoint
3. **Send** — Signing requests where a provider needs pre-signed forms
4. **Move** — Uploads done → **Ready for Advice**

Tags: `docs-ready`

### Client receives

- Signing requests where appropriate

### Internal work

- Prepare forms, implementation pack, signing docs
- Upload to MyProsperity vault + SharePoint

Matrix refs: Not itemised · AD-061 · AD-062 · AD-188

---

## 4.6 · Ready for Advice

> SOA approved, docs ready; the client has yet to book the presentation.

| | |
|---|---|
| Live stage name | `6 \|💊Ready for Advice` |
| Today | **Fires · nothing** |
| To build | **4** — 4 new · 0 fix · 0 decision-first |
| Mapping recommendation | Strong automation — Strong automation point |
| Hands off to | 5 · Presentation |

### To build here

- [ ] **New** — Advice Presentation calendar with a 3-day minimum notice
- [ ] **New** — Invitation + reminder emails written, booking link included
- [ ] **New** — Reminders stop as soon as the client books
- [ ] **New** — Booking hands off to Advice Presentation 5.1

### What exists today

- ⚠️ Fires the workflow, then nothing
- ❌ The move into Advice Presentation is manual
- ❌ Live-only stage; the definitions doc hands off from 4.5

### How it should run — Book the presentation

1. **Trigger** — Card enters **4.6**
2. **Send** — Invitation with the **Advice Presentation booking link** (calendar enforces the 3-day minimum)
3. **Chase** — Not booked after N days → reminder → adviser task (stop as soon as booked)
4. **Move** — Booking → **Advice Presentation 5.1**

Tags: `presentation-booked`

### Client receives

- Booking invitation
- Presentation reminders until booked

### Internal work

- Confirm prerequisites (SOA approved · docs uploaded)
- Monitor booking

Matrix refs: Not itemised · AD-008–010

