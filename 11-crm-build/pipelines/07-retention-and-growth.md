---
id: crm-build-pipeline-7
title: 7 · Retention & Growth — stage build spec
type: system
status: review
confidence: verified (today) / inferred (to build)
source: CRM build inventory 18 Sep 2026 + Role Task Matrix flow + pipeline mapping conversation; board prospa-build-blueprint (Desktop) · local http://localhost:5645
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, pipeline, retention-and-growth]
---

# 7 · Retention & Growth

ongoing service, reviews, referrals, annual consent.

**10 stages** · today: 0 built · 0 part-built or empty · 10 not built · **29 things to build** (24 new · 2 fix · 3 decision-first).

Legend: ✅ works today · ⚠️ exists but weak / placeholder · ❌ missing. Build kinds: **New** = does not exist · **Fix** = exists, change it · **Check** = verify a setting · **Decide** = Prospa decision first (see `decisions-register.md`).

---

## 7.1 · Ongoing Service Active

> Client on an ongoing service agreement; the 12-month review clock starts.

| | |
|---|---|
| Live stage name | `1 \|⛑️Ongoing Service Active` |
| Today | **Not built** |
| To build | **3** — 2 new · 0 fix · 1 decision-first |
| Mapping recommendation | Strong automation — Date-driven automation backbone |

### To build here

- [ ] **New** — Five date fields, populated at Closed Won
- [ ] **New** — Date-driven triggers: review due − 3 months · consent − N weeks · review-ask interval · authority expiry
- [ ] **Decide** — Lead times + fee / consent / service events (D6)

### What exists today

- ❌ Not implemented — nothing in this pipeline is
- ❌ The review-due and consent-anniversary fields the definition assumes may not exist
- ❌ In the matrix all five date obligations are tracked by hand

### How it should run — Date engine

1. **Trigger** — Date fields on the contact: review due · consent anniversary · service agreement · fee arrangement · authority expiry
2. **Branch** — Review due − 3 months → **Review Preparation**
3. **Branch** — Consent anniversary − N weeks → **Annual Consent Due**
4. **Branch** — Set interval after implementation → **Request Review**
5. **Branch** — Authority expiring → admin task: new authority (AD-149 → AD-139)

Tags: `client-active`

### Client receives

- Ongoing-service communication

### Internal work

- Track review, service agreement, consent, fee and authority dates

### Decision needed

D6 · fee, consent and ongoing-service events; lead times for reviews and renewals (file 2, §8.3).

Matrix refs: AD-150 · AD-158 · AD-159 · AD-160 · AD-163 · AD-149 · AD-248–251

---

## 7.2 · Request Review

> Ask a satisfied client for an online review (not the annual review meeting).

| | |
|---|---|
| Live stage name | `2 \|👓Request Review` |
| Today | **Not built** |
| To build | **3** — 1 new · 1 fix · 1 decision-first |
| Mapping recommendation | Automate — Automate |

### To build here

- [ ] **New** — Review request with the Google link + one reminder
- [ ] **Decide** — Interval after Closed Won
- [ ] **Fix** — Rename to "Online review ask"

### What exists today

- ❌ Not implemented
- ⚠️ Name clashes with the annual review stages 7.6–7.8

### How it should run — Review ask

1. **Trigger** — Set interval after Closed Won
2. **Send** — Review request with the Google link · one reminder
3. **Action** — Response logged → **Request Referral**

Tags: `review-asked`

### Client receives

- Online review request

### Internal work

- Track request and status

Matrix refs: Not in sheet

---

## 7.3 · Request Referral

> Ask the client to introduce someone from their network.

| | |
|---|---|
| Live stage name | `3 \|👔Request Referral` |
| Today | **Not built** |
| To build | **3** — 3 new · 0 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate |
| Exit | referral → 1 · Prospect |

### To build here

- [ ] **New** — Referral request + a simple intro form
- [ ] **New** — Form → new Prospect lead with source = client referral
- [ ] **New** — Thank-you to the referrer

### What exists today

- ❌ Not implemented
- ❌ Referral source is recorded in the matrix, but referrers are never updated or thanked

### How it should run — Referral ask

1. **Trigger** — Follows the review request
2. **Send** — Referral request with a simple intro form
3. **Action** — Form submitted → new **Prospect · New Lead** with source = client referral
4. **Send** — Thank-you to the referrer

Tags: `referral-asked`

### Client receives

- Referral request

### Internal work

- Capture the referral
- Create the Prospect opportunity

Matrix refs: Not in sheet · AD-037

---

## 7.4 · Annual Consent Due

> The annual fee consent renewal is approaching.

| | |
|---|---|
| Live stage name | `4 \|🌏Annual Consent Due` |
| Today | **Not built** |
| To build | **3** — 2 new · 0 fix · 1 decision-first |
| Mapping recommendation | Automate — Automate |

### To build here

- [ ] **New** — Consent document + e-sign flow
- [ ] **New** — Reminder cadence until signed · escalate to the adviser
- [ ] **Decide** — What happens if consent is not renewed

### What exists today

- ❌ Not implemented
- ❌ Consent renewal dates are tracked by hand in the matrix (AD-159); Prospa lists them for automation

### How it should run — Consent renewal

1. **Trigger** — Consent anniversary − N weeks
2. **Send** — Consent documents for signature · reminders until signed
3. **Task** — Admin: renewal documentation (AD-161)
4. **Escalate** — Unsigned by the anniversary → adviser

Tags: `consent-due`

### Client receives

- Consent documents
- Reminders

### Internal work

- Generate and track the consent renewal

### Decision needed

D6 · what happens when a client does not renew consent.

Matrix refs: AD-159 · AD-161 · AD-162 · AD-250 · AD-251

---

## 7.5 · Consent Obtained

> Signed annual consent received and filed.

| | |
|---|---|
| Live stage name | `5 \|🥁Consent Obtained` |
| Today | **Not built** |
| To build | **2** — 2 new · 0 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate |
| Exit | back to 7.1 |

### To build here

- [ ] **New** — File the consent · consent anniversary + 12 months
- [ ] **New** — Return to Ongoing Service Active

### What exists today

- ❌ Not implemented

### How it should run — Consent filed

1. **Trigger** — Signed consent received (e-sign complete / upload)
2. **Action** — File to SharePoint · consent anniversary + 12 months
3. **Move** — → back to **Ongoing Service Active**

Tags: `consent-ok`

### Client receives

- Confirmation if required

### Internal work

- File the consent
- Reset the anniversary date

Matrix refs: AD-159 · AD-162

---

## 7.6 · Review Preparation

> Associates prepare the annual review pack; the client is invited to book.

| | |
|---|---|
| Live stage name | `6 \|🎯Review Preparation` |
| Today | **Not built** |
| To build | **4** — 3 new · 1 fix · 0 decision-first |
| Mapping recommendation | Strong automation — Major automation point |

### To build here

- [ ] **Check** — Annual Review calendar confirmed
- [ ] **New** — Invitation with the booking link + questionnaire / info request
- [ ] **New** — Prep tasks by role: associate analysis · admin pack
- [ ] **New** — Chase loop for review information

### What exists today

- ❌ Not implemented
- ❌ The Annual Review calendar the definition relies on needs confirming

### How it should run — Review prep

1. **Trigger** — Review due − 2–3 months
2. **Send** — Review invitation with the **Annual Review booking link** · questionnaire / info request
3. **Tasks** — **Associate**: annual review analysis (AA-084–095) · **Admin**: review pack
4. **Chase** — Questionnaire outstanding → reminders → call task
5. **Move** — Booked → **Review Scheduled**

Tags: `review-prep`

### Client receives

- Review invitation + booking link
- Updated-information request / questionnaire

### Internal work

- Review-prep tasks
- Information gathering
- Analysis and review pack

Matrix refs: AD-151–157 · AD-165 · AD-166 · AA-084–095 · AD-248

---

## 7.7 · Review Scheduled

> Client books their annual review meeting.

| | |
|---|---|
| Live stage name | `7 \|📅Review Scheduled` |
| Today | **Not built** |
| To build | **2** — 2 new · 0 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate |

### To build here

- [ ] **New** — Booking → confirmation + reminders
- [ ] **New** — Prep task: pack ready · record current

### What exists today

- ❌ Not implemented

### How it should run — Review booked

1. **Trigger** — Booking on the Annual Review calendar
2. **Send** — Confirmation + reminders
3. **Task** — Admin: pack ready · record current (AD-065)
4. **Move** — Meeting held → **Review Meeting Complete**

### Client receives

- Confirmation + reminders

### Internal work

- Meeting prep
- Workflow update

Matrix refs: AD-008–012 · AD-056 · AD-065

---

## 7.8 · Review Complete

> Review held; circumstances reassessed; change / no-change decision.

| | |
|---|---|
| Live stage name | `8 \|🔋Review Meeting Complete` |
| Today | **Not built** |
| To build | **3** — 3 new · 0 fix · 0 decision-first |
| Mapping recommendation | Assist — Automate admin around human decision |

### To build here

- [ ] **New** — File-note + record-update tasks
- [ ] **New** — Recap + action list email
- [ ] **New** — Decision recorded on the card: change / no change

### What exists today

- ❌ Not implemented

### How it should run — Post-review

1. **Trigger** — Card enters **7.8**
2. **Tasks** — File note · record updates · follow-ups
3. **Send** — Recap + action list
4. **Decision** — Adviser: **Change Required** or **No Change**

### Client receives

- Client recap / action list

### Internal work

- File notes
- Update facts and goals
- Follow-up tasks
- Change decision

Matrix refs: AA-057 · AD-068–079 · AD-156 · AD-167

---

## 7.9 · Change Required

> The strategy needs to change: a new advice opportunity.

| | |
|---|---|
| Live stage name | `9 \|⚙️Change Required` |
| Today | **Not built** |
| To build | **3** — 3 new · 0 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate loop to Strategy / Advice Production |
| Exit | new advice → 3 or 4 |

### To build here

- [ ] **New** — Branch rule: full strategy → Strategy 3.1 · limited change (ROA) → Advice Production 4.1
- [ ] **New** — New opportunity created with the review context
- [ ] **New** — Next-steps email

### What exists today

- ❌ Not implemented

### How it should run — New advice

1. **Trigger** — Card enters **Change Required**
2. **Branch** — Full strategy → new opportunity in **Strategy 3.1** · limited change (ROA) → **Advice Production 4.1**
3. **Send** — Next steps to the client

Tags: `new-advice`

### Client receives

- Next-step communication

### Internal work

- Create the new advice opportunity / task set

Matrix refs: AA-092 · PP-045–052 · AD-031

---

## 7.10 · No Change

> Existing strategy remains appropriate; back to ongoing service.

| | |
|---|---|
| Live stage name | `10 \|📍No Change` |
| Today | **Not built** |
| To build | **3** — 3 new · 0 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate |
| Exit | next cycle → 7.1 |

### To build here

- [ ] **New** — Review due + 12 months · close review admin
- [ ] **New** — Review-complete note to the client
- [ ] **New** — Loop back to 7.1

### What exists today

- ❌ Not implemented

### How it should run — Review closed

1. **Trigger** — Card enters **No Change**
2. **Action** — Review due + 12 months · close review admin (AD-167)
3. **Send** — Review-complete note
4. **Move** — → **Ongoing Service Active**

Tags: `client-active`

### Client receives

- Review-completion communication

### Internal work

- Close the review
- Reset the review date
- Return to active service

Matrix refs: AD-167 · AD-150

