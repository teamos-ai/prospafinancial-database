---
id: crm-build-pipeline-2
title: 2 · Engagement — stage build spec
type: system
status: review
confidence: verified (today) / inferred (to build)
source: CRM build inventory 18 Sep 2026 + Role Task Matrix flow + pipeline mapping conversation; board prospa-build-blueprint (Desktop) · local http://localhost:5645
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, pipeline, engagement]
---

# 2 · Engagement

welcome, fact find, engagement meeting, admin follow-up.

**4 stages** · today: 2 built · 2 part-built or empty · 0 not built · **22 things to build** (12 new · 8 fix · 2 decision-first).

Legend: ✅ works today · ⚠️ exists but weak / placeholder · ❌ missing. Build kinds: **New** = does not exist · **Fix** = exists, change it · **Check** = verify a setting · **Decide** = Prospa decision first (see `decisions-register.md`).

---

## 2.1 · Welcome + MyProsperity

> Welcome pack: fact find, FSG, engagement meeting booking.

| | |
|---|---|
| Live stage name | `1 \|🙋‍♂️ Email MyProsperity and Welcome client email` |
| Today | **Part-built** |
| To build | **8** — 4 new · 4 fix · 0 decision-first |
| Mapping recommendation | Strong automation — Major automation point |

### To build here

- [ ] **Fix** — Welcome email: adviser merge field instead of "Neil"; send from the adviser
- [ ] **Fix** — Welcome SMS: real copy
- [ ] **Fix** — FSG email: real body around the link; confirm FSG v5.1 is current
- [ ] **New** — Privacy consent + Terms of Engagement sent for signature
- [ ] **New** — Engagement meeting booking link in the pack
- [ ] **New** — Document-request email(s): super · investment · insurance · bank/loan
- [ ] **New** — Admin tasks on entry: SharePoint folder · verify record · onboarding status
- [ ] **Check** — Re-entry allowed · workflow published

### What exists today

- ✅ Welcome email — written; hard-codes "after speaking with Neil"; sends from the shared business address
- ⚠️ Welcome SMS — body is "test"
- ⚠️ "Before we get started" at 4 h — the FSG link only, no text
- ⚠️ Engagement-meeting email at ~2 d — blank, no booking link
- ✅ Chase task at ~3 d if the fact find is not done
- ❌ Nothing moves the card on

### How it should run — Onboarding pack

1. **Trigger** — Opportunity enters **Engagement 2.1**
2. **Tasks** — Admin: create SharePoint folder · verify record · onboarding status = started
3. **Send** — Welcome email + SMS (real copy, adviser merge field, from the adviser)
4. **Send** — FSG · privacy consent · Terms of Engagement · MyProsperity link + how-to
5. **Send** — Document requests: super · investment · insurance · bank/loan where in scope
6. **Send** — **Engagement meeting booking link** (built-in calendar)
7. **Monitor** — Wait → detect fact find + signed docs → chase (2.2) → escalate exceptions

Tags: `onboarding` · `fsg-sent` · `toe-sent`

### Client receives

- Welcome
- FSG
- Privacy consent
- Terms of Engagement
- Fact find / MyProsperity link + instructions
- Document requests: super, investment, insurance, bank/loan

### Internal work

- Create / verify the CRM record and SharePoint folder
- Record referral source
- Create onboarding tasks · start onboarding tracking

### Decision needed

D3 · chase timing and escalation for unsigned Terms of Engagement and privacy consent (the matrix has no chase for either).

Matrix refs: AD-039–043 · AD-013 · AD-044 · AD-046 · AD-048–053 · AD-234 · AD-237

---

## 2.2 · Engagement Checklist

> Advice assistants prepare the client file before the meeting.

| | |
|---|---|
| Live stage name | `2 \|🔭 Prepare Engagement Meeting Checklist` |
| Today | **Built** |
| To build | **5** — 3 new · 2 fix · 0 decision-first |
| Mapping recommendation | Automate — Automate tasks and chase sequences |

### To build here

- [ ] **Fix** — Assignee on every task — a role, not one person
- [ ] **Fix** — Remove the duplicate MyProsperity check
- [ ] **New** — Client chase sequence: fact find · ID · statements (intervals per D3 / D9)
- [ ] **New** — Escalation task to the adviser when critical info is still missing
- [ ] **New** — Notify the associate when the fact find lands

### What exists today

- ✅ 10 prep tasks on entry, due in 2 days (weekends skipped): folder · MP completed? · Fact Find · pack · FSG · TPA · TOE · uploads · Xplan export · certified ID
- ⚠️ Only 2 of the 10 name an assignee
- ⚠️ "MP completed?" duplicates the stage-1 chase task
- ❌ No chase sequence to the client
- ❌ No escalation when critical items are missing

### How it should run — Pre-meeting file check

1. **Trigger** — Fact find completed (MyProsperity) **or** card enters 2.2
2. **Tasks** — Admin checklist with **named assignees** per role
3. **Chase** — Fact find / ID / statements outstanding → client reminder at day X, Y · then task to call
4. **Gate** — Critical items missing before the meeting → escalate to the adviser (AD-055)
5. **Handoff** — Associate: fact find ready for review

Tags: `file-complete`

### Client receives

- Chase incomplete / missing information

### Internal work

- Check fact find, ID, statements and supporting docs
- Identity verification
- Folder in place · missing information listed
- Presentation pack, TPA, Terms of Engagement, certified ID

Matrix refs: AD-014–017 · AD-049 · AD-054 · AD-055 · AD-057–066 · AA-006–022 · AD-243

---

## 2.3 · Engagement Meeting

> Adviser holds the meeting; the client commits to advice.

| | |
|---|---|
| Live stage name | `3 \|🏁 Engagement Meeting` |
| Today | **Part-built** |
| To build | **4** — 2 new · 1 fix · 1 decision-first |
| Mapping recommendation | Assist — Automate surrounding admin; human adviser decision |

### To build here

- [ ] **New** — Engagement meeting calendar → confirmation + reminders
- [ ] **Fix** — Strategy booking email + SMS rewritten, link included
- [ ] **New** — File-note task after the meeting (AI transcript summary candidate)
- [ ] **Decide** — Decline path out of Engagement (D1) — build once decided

### What exists today

- ✅ Task: "Push post meeting Req's & MAY" (term to confirm)
- ⚠️ "Book Strategy meeting" email — blank
- ⚠️ "Book Strategy meeting" SMS — no link
- ❌ No confirmation or reminders for the meeting itself
- ❌ No decline path out of Engagement — the definitions doc had Advice WON / Opportunity Lost here; live does not

### How it should run — Engagement meeting

1. **Trigger** — Engagement meeting **booked** → confirmation + reminders
2. **Trigger** — Meeting **held** → file-note task
3. **Send** — Book-the-strategy-meeting email + SMS **with the link**
4. **Decision** — Adviser records: proceed · declined (path undefined, D1)

Tags: `engaged`

### Client receives

- Confirmation + reminders
- The meeting
- Possible recap

### Internal work

- Capture goals, instructions, notes / transcript
- Follow-ups captured with owners

### Decision needed

D1 · the Engagement decline / lost path. D2 · what constitutes Engagement completion.

Matrix refs: AD-009 · AD-010 · AD-056 · AA-050–059 · AD-239

---

## 2.4 · Admin Follow-up

> Post-meeting admin, then the handoff to Strategy Development.

| | |
|---|---|
| Live stage name | `4 \|🤝Admin Follow up` |
| Today | **Built** |
| To build | **5** — 3 new · 1 fix · 1 decision-first |
| Mapping recommendation | Strong automation — Strong automation point |
| Hands off to | 3 · Strategy |

### To build here

- [ ] **Fix** — Rename "Create SP folder" → "Send TPA to provider"; assign every task
- [ ] **New** — Recap + client action list email (AI recap draft candidate)
- [ ] **New** — Chase loop for agreed client actions
- [ ] **New** — Gate: tasks complete + ToE signed → automatic handoff to Strategy 3.1
- [ ] **Decide** — What "Engagement complete" means (D2) · person or system moves the card (D8)

### What exists today

- ✅ 5 back-office tasks on entry, due 2 days: TPA to provider · Xplan record · notify AE · upload research · fact find to client
- ⚠️ No assignee on any of them
- ⚠️ "Create SP folder" is misnamed — its body says "Send TPA to provider"
- ⚠️ The completed fact find goes to the client by hand
- ❌ Nothing moves the card to Strategy Development

### How it should run — Post-meeting + handoff

1. **Trigger** — Card enters **Admin Follow up**
2. **Tasks** — Admin: TPA to provider · Xplan record · notify AE · upload research · completed fact find to client
3. **Send** — Recap + client action list · documents promised in the meeting
4. **Chase** — Client-owed actions overdue → reminder → call task
5. **Gate** — All follow-up tasks complete + ToE signed → **move to Strategy 3.1**

Tags: `toe-signed`

### Client receives

- Client action list
- Requested documents
- Chase agreed actions

### Internal work

- File notes · update data
- Create / allocate tasks with due dates
- Update workflow stage · Strategy handoff
- TPA to provider · Xplan set up · notify Advice Evolution · research uploaded

Matrix refs: AD-068–079 · AA-062 · AD-238 · AD-240 · AD-241

