---
id: crm-build-pipeline-6
title: 6 · Implementation — stage build spec
type: system
status: review
confidence: verified (today) / inferred (to build)
source: CRM build inventory 18 Sep 2026 + Role Task Matrix flow + pipeline mapping conversation; board prospa-build-blueprint (Desktop) · local http://localhost:5645
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, pipeline, implementation]
---

# 6 · Implementation

execute with providers, peer review, compliance checklist, sign-off.

**8 stages** · today: 6 built · 2 part-built or empty · 0 not built · **25 things to build** (18 new · 4 fix · 3 decision-first).

Legend: ✅ works today · ⚠️ exists but weak / placeholder · ❌ missing. Build kinds: **New** = does not exist · **Fix** = exists, change it · **Check** = verify a setting · **Decide** = Prospa decision first (see `decisions-register.md`).

---

## 6.1 · Implement Advice

> Admin execute the advice with the product providers.

| | |
|---|---|
| Live stage name | `1 \|🙂Implement Advice` |
| Today | **Built** |
| To build | **3** — 2 new · 1 fix · 0 decision-first |
| Mapping recommendation | Strong automation — Major automation point |

### To build here

- [ ] **Fix** — "Lets go!" → "Let's go!"; list what the client must sign / pay / attend
- [ ] **New** — Task bundles per product lane: super · investments · insurance · pension · contributions — assigned to admin
- [ ] **New** — Lane-in-scope flags on the opportunity

### What exists today

- ✅ "Implementation - Lets go!" email — written (apostrophe missing)
- ✅ 3 tasks: ATP signed? · FTA? · Product provider forms?
- ⚠️ All to the contact's assigned user

### How it should run — Implementation kick-off

1. **Trigger** — Card enters **6.1**
2. **Send** — "Implementation has begun" with what the client must sign / pay / attend
3. **Tasks** — **Admin**: one bundle per product lane in scope (application → submit → track → confirm → file)
4. **Tasks** — ATP · FTA · provider forms — signed and on file
5. **Move** — Submissions ready → **Peer-Review & Submit**

Tags: `implementing`

### Client receives

- Implementation-start communication
- Signing, payment and medical requirements

### Internal work

- Product-specific task bundles: super · investments · insurance · pension · contributions
- Submissions to providers

Matrix refs: AD-080 · AD-094 · AD-106 · AD-121 · AD-131 · AD-108 · AD-132 · AA-075

---

## 6.2 · Peer-Review & Submit

> Associate checks the implementation work before submission. Hard gate.

| | |
|---|---|
| Live stage name | `2 \|👊Peer-Review & Submit` |
| Today | **Built** |
| To build | **2** — 1 new · 1 fix · 0 decision-first |
| Mapping recommendation | Automate — Automated assignment + hard gate · **hard gate** |

### To build here

- [ ] **Fix** — Reviewer = associate, not the admin who prepared it
- [ ] **New** — Gate enforced before submission

### What exists today

- ✅ Task: Peer-Review & Submit
- ⚠️ Whoever did the work checks it
- ⚠️ Not enforced — nothing waits for it

### How it should run — Peer-review & submit gate

1. **Trigger** — Card enters **6.2**
2. **Task** — **Associate**: review applications (complex ones flagged, AA-077)
3. **Gate** — Signed off → submit → **Follow up implementation**

Tags: `impl-reviewed`

### Client receives

- Usually none

### Internal work

- Associate review before submission

Matrix refs: AA-076 · AA-077 · AD-081 · AD-095 · AD-107 · AD-122

---

## 6.3 · Follow-up Implementation

> Chase providers, keep the client informed while applications process.

| | |
|---|---|
| Live stage name | `3 \|⏳Follow up implementation` |
| Today | **Built** |
| To build | **5** — 4 new · 0 fix · 1 decision-first |
| Mapping recommendation | Strong automation — Major automation opportunity |

### To build here

- [ ] **New** — Lane status fields: submitted · established · confirmed
- [ ] **New** — Weekly client progress email from those fields ("3 of 7 changes implemented")
- [ ] **New** — Provider chase intervals per lane
- [ ] **New** — Client chase for medicals / contributions
- [ ] **Decide** — Exception + escalation paths; provider turnaround before a chase starts (D9)

### What exists today

- ✅ Task: Follow Up implementation
- ❌ No progress updates reach the client, although the definition promises weekly updates
- ❌ No provider chase loops

### How it should run — Provider chase + progress

1. **Trigger** — Card enters **6.3**
2. **Chase** — Provider turnaround exceeded → chase task (super · platform · insurer · employer)
3. **Send** — Weekly client progress update from the lane statuses
4. **Send** — Client-owed items (medicals, contributions) → reminder → call task
5. **Escalate** — Provider problem → associate (AA-080)
6. **Move** — All confirmations received → **Complete Final Checklist**

Tags: `awaiting-provider`

### Client receives

- Missing-item requests
- Progress updates

### Internal work

- Provider chase tasks (8 loops in the matrix)
- Implementation tracker
- Escalations to the associate

### Decision needed

D9 · exception handling and escalation paths; expected provider turnaround before a chase starts.

Matrix refs: AD-082–090 · AD-096–103 · AD-109–113 · AD-123–128 · AD-133–135 · AD-022 · AA-078–080 · AD-245 · AD-246

---

## 6.4 · Final Checklist

> Compliance checklist for the client file. Hard gate.

| | |
|---|---|
| Live stage name | `4 \|👍Complete Final Checklist` |
| Today | **Built** |
| To build | **3** — 2 new · 1 fix · 0 decision-first |
| Mapping recommendation | Automate — Automated checklist + hard gate · **hard gate** |

### To build here

- [ ] **Fix** — Assign to admin
- [ ] **New** — Gate enforced on all 14
- [ ] **New** — Confirmations filed per lane

### What exists today

- ✅ 14 compliance tasks: KYC · client docs · PoA · risk profile · file notes · Xplan notes · SoA/RoA · PDS · signed ATP · signed forms · check & confirm · Xplan fees · new business sheet · FTA
- ⚠️ All to the contact's assigned user
- ⚠️ Not enforced — the card can move on early

### How it should run — Final checklist gate

1. **Trigger** — Card enters **6.4**
2. **Tasks** — **Admin**: the 14 checks as mandatory subtasks (keep them)
3. **Gate** — All 14 complete → **Check Final Implementation**; nothing advances early

Tags: `file-complete`

### Client receives

- Normally none

### Internal work

- KYC, SOA/ROA, ATP, PDS, confirmations, fees, notes, documents all recorded

Matrix refs: AD-091 · AD-101 · AD-119 · AD-129 · AD-136 · AD-114 · AD-092 · AD-104 · AD-137

---

## 6.5 · Check Final Implementation

> Associate verifies the implementation matches the advice.

| | |
|---|---|
| Live stage name | `5 \|⚡️Check Final Implementation` |
| Today | **Built** |
| To build | **2** — 1 new · 1 fix · 0 decision-first |
| Mapping recommendation | Assist — Internal task |

### To build here

- [ ] **Fix** — Associate assignee
- [ ] **New** — Discrepancy → back to 6.3

### What exists today

- ✅ Task: Check Final Implementation
- ⚠️ To the contact's assigned user

### How it should run — Associate verification

1. **Trigger** — Card enters **6.5**
2. **Task** — **Associate**: confirm no discrepancies (AA-081)
3. **Move** — Confirmed → **Final Check & Inform Client**

### Client receives

- None

### Internal work

- Verify implementation matches the advice · exceptions reviewed

Matrix refs: AA-081 · AA-082

---

## 6.6 · Final Check & Inform

> Adviser final review; completion confirmed to the client.

| | |
|---|---|
| Live stage name | `6 \|🎯Final Check & Inform Client` |
| Today | **Built** |
| To build | **3** — 2 new · 0 fix · 1 decision-first |
| Mapping recommendation | Automate — Automate after approval |

### To build here

- [ ] **New** — Adviser approval task
- [ ] **New** — Completion email sent by the workflow, per-lane summary merged in
- [ ] **Decide** — Tell the client per lane, or once at the end? (file 2, Q8)

### What exists today

- ✅ Task: Final Check & Inform Client
- ⚠️ Informing the client is done by hand through the task
- ❌ In the matrix, completion notices go to the adviser / associate only — the client is never told

### How it should run — Completion

1. **Trigger** — **Adviser approves** the final check
2. **Send** — Completion email: what was implemented, per lane
3. **Task** — Admin: new business sheet updated
4. **Branch** — Wrap-up meeting wanted? → 6.7 · else → **Closed Won**

Tags: `implemented`

### Client receives

- Completion communication

### Internal work

- Adviser final review
- Record updates · new business sheet

### Decision needed

Should the client be told when each lane completes, or once at the end?

Matrix refs: AD-093 · AD-105 · AD-120 · AD-138 · AA-083 · AD-247

---

## 6.7 · Implementation Meeting

> Optional wrap-up meeting walking the client through what was implemented.

| | |
|---|---|
| Live stage name | `7 \|⌚Implementation Meeting` |
| Today | **Fires · nothing** |
| To build | **2** — 2 new · 0 fix · 0 decision-first |
| Mapping recommendation | Assist — Conditional automation |

### To build here

- [ ] **New** — Booking link → confirmation + reminders
- [ ] **New** — File-note task after the meeting

### What exists today

- ⚠️ Fires, then nothing — no task, no invite, no booking link

### How it should run — Wrap-up meeting

1. **Trigger** — Card enters **6.7** (optional stage)
2. **Send** — Booking link → confirmation + reminders
3. **Task** — File note after the meeting
4. **Move** — → **Closed Won**

### Client receives

- Confirmation + reminders
- Wrap-up

### Internal work

- Meeting / file-note tasks when required

Matrix refs: AD-008–012 · AD-068

---

## 6.8 · Closed Won

> Advice fully implemented; the client transitions to ongoing service.

| | |
|---|---|
| Live stage name | `8 \| ✅ Closed Won` |
| Today | **Part-built** |
| To build | **5** — 4 new · 0 fix · 1 decision-first |
| Mapping recommendation | Strong automation — Automate to Retention & Growth |
| Hands off to | 7 · Retention |

### To build here

- [ ] **New** — Date fields: review due · consent anniversary · service agreement · fee arrangement · authority expiry
- [ ] **New** — Won status set
- [ ] **New** — "Welcome to ongoing service" email — the next 12 months
- [ ] **New** — Automatic handoff into Retention & Growth
- [ ] **Decide** — Fee, consent + ongoing-service events (D6)

### What exists today

- ✅ "Implementation - Done and Dusted" email — written (content to confirm)
- ❌ Status is not set to won
- ❌ Nothing starts Retention & Growth

### How it should run — Closed won → ongoing service

1. **Trigger** — Card enters **Closed Won**
2. **Action** — Status = **won** · set **review due**, **consent anniversary**, service-agreement and fee-arrangement dates
3. **Send** — "Welcome to ongoing service" — what happens over the next 12 months
4. **Move** — **Create the Retention & Growth opportunity** at Ongoing Service Active

Tags: `client-active`

### Client receives

- Ongoing-service communication if desired

### Internal work

- Close implementation
- Set ongoing-service, review and consent dates

### Decision needed

D6 · exact fee, consent and ongoing-service events (the dates this stage must set).

Matrix refs: AD-150 · AD-158–160 · AD-208 · first review date not in sheet

