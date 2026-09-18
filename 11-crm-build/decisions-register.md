---
id: crm-build-decisions-register
title: Decisions Prospa owns — CRM build
type: system
status: review
confidence: inferred
source: Pipeline mapping conversation + customer-journey discussion 18 Sep 2026; board prospa-build-blueprint (Desktop) · local http://localhost:5645
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, decisions, approval-required]
---

# Decisions Prospa owns

Business-process decisions, not build decisions. Each one blocks specific stages; settle them before automating those stages.

| # | Decision | Unblocks | Owner | Status |
|---|---|---|---|---|
| D1 | Engagement decline / lost path | 2.3 · 2.4 | Neil + Monik | open |
| D2 | What "Engagement complete" means | 2.4 → 3.1 | Neil + Monik | open |
| D3 | Chasing unsigned ToE + privacy consent | 2.1 · 2.2 | Monik | open |
| D4 | Waiting On Decision cadence | 5.5 | Neil + Monik | open |
| D5 | Adviser sign-off ownership | 3.4 · 4.4 · 5.3 · 6.6 | Neil | open |
| D6 | Fee, consent + ongoing-service events | 5.3 · 6.8 · 7.1 · 7.4 | Neil + Margaretta | open |
| D7 | System of record | Architecture · every CRM write | Neil + Raminder | open |
| D8 | Person or system moves the card | 1.4 · 2.4 · 3.6 · 4.6 · 5.3 · 6.8 | Neil + Monik | open |
| D9 | Exceptions + escalation | 2.2 · 6.3 · 7.6 | Monik + Raminder | open |
| D10 | Offboarding / exit | after 7.10 | Neil | open |
| Also open | From the as-built review | 1.1 · 1.5 · 1.6 | Neil + Monik | open |

## D1 · Engagement decline / lost path

The 10 Sep definitions end Engagement in Advice WON / Opportunity Lost; live ends in Engagement Meeting / Admin Follow up. There is no way out for a client who does not go ahead.

- **Unblocks:** 2.3 · 2.4
- **Owner:** Neil + Monik
- **Status:** open

## D2 · What "Engagement complete" means

The event that hands a client to Strategy Development: signed ToE? fact find in? adviser says so?

- **Unblocks:** 2.4 → 3.1
- **Owner:** Neil + Monik
- **Status:** open

## D3 · Chasing unsigned ToE + privacy consent

The matrix chases fact finds, ID and statements but never the two signed documents. Interval, attempts, who it escalates to.

- **Unblocks:** 2.1 · 2.2
- **Owner:** Monik
- **Status:** open

## D4 · Waiting On Decision cadence

How often the adviser follows up an undecided client, and when it escalates or closes as lost. The stage itself is not yet signed off.

- **Unblocks:** 5.5
- **Owner:** Neil + Monik
- **Status:** open

## D5 · Adviser sign-off ownership

The adviser is a dependency on 335 of 443 tasks but has no task list. Who signs off at each gate: strategy, SOA, presentation, final check.

- **Unblocks:** 3.4 · 4.4 · 5.3 · 6.6
- **Owner:** Neil
- **Status:** open

## D6 · Fee, consent + ongoing-service events

First service agreement, fee arrangement, advice-fee invoice, consent anniversary: none are in the matrix. These become the date fields the whole Retention lane runs on.

- **Unblocks:** 5.3 · 6.8 · 7.1 · 7.4
- **Owner:** Neil + Margaretta
- **Status:** open

## D7 · System of record

AdviserLogic is on 409 of 443 tasks; the new CRM is never mentioned. Which system owns contacts, stages, tasks, documents and key dates — per data type.

- **Unblocks:** Architecture · every CRM write
- **Owner:** Neil + Raminder
- **Status:** open

## D8 · Person or system moves the card

All six pipeline boundaries are manual today. At each gate: does a person move the card, or does the system when the gate is met?

- **Unblocks:** 1.4 · 2.4 · 3.6 · 4.6 · 5.3 · 6.8
- **Owner:** Neil + Monik
- **Status:** open

## D9 · Exceptions + escalation

16 manual chase loops (8 client, 8 provider) with no interval, attempts or escalation point. Provider turnaround before a chase starts.

- **Unblocks:** 2.2 · 6.3 · 7.6
- **Owner:** Monik + Raminder
- **Status:** open

## D10 · Offboarding / exit

Nothing covers a client leaving, stopping ongoing service, switching off fees, deceased estates, or archiving. Phase 8 is not in the sheet.

- **Unblocks:** after 7.10
- **Owner:** Neil
- **Status:** open

## Also open · From the as-built review

Not A Lead: close out or nurture · nurture tag + content · the front door (form / website / manual) · stage timelines (TBC Neil + Monik) · per-stage ownership (with Monik) · real win probabilities.

- **Unblocks:** 1.1 · 1.5 · 1.6
- **Owner:** Neil + Monik
- **Status:** open

