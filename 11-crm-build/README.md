---
id: crm-build-readme
title: CRM build blueprint — what exists, what to build
type: system
status: review
confidence: verified (today) / inferred (to build)
source: Four working files (Downloads/Prospa Matrix, 18 Sep 2026): 1 CRM build inventory · 2 Role Task Matrix flow analysis · 3 customer-journey discussion · 4 pipeline task & automation mapping. Generated from the board prospa-build-blueprint (Desktop) · local http://localhost:5645 by tools/export-database.cjs.
as_of: 2026-09-18
owner: Ariki Meroiti
tags: [11-crm-build, readme]
---

# CRM build blueprint

Prospa's live CRM, stage by stage: what exists today and what still needs to be built. The seven live pipelines are the spine; each of the 45 stages is an event that launches internal tasks, client communication and automated chasing.

**154 things to build** — 103 new · 29 fixes to what exists · 22 wait on a Prospa decision.
Today: 18 stages built · 9 part-built or empty · 18 not built. No pipeline boundary is automated; every hand-off is a manual move.

## Files

| File | What it holds |
|---|---|
| `pipelines/01-prospect.md` | 1 · Prospect — 6 stages, 22 to build |
| `pipelines/02-engagement.md` | 2 · Engagement — 4 stages, 22 to build |
| `pipelines/03-strategy-development.md` | 3 · Strategy Development — 6 stages, 18 to build |
| `pipelines/04-advice-production.md` | 4 · Advice Production — 6 stages, 20 to build |
| `pipelines/05-advice-presentation.md` | 5 · Advice Presentation — 5 stages, 18 to build |
| `pipelines/06-implementation.md` | 6 · Implementation — 8 stages, 25 to build |
| `pipelines/07-retention-and-growth.md` | 7 · Retention & Growth — 10 stages, 29 to build |
| `around-the-journey.md` | the 149 continuous tasks + newsletter nurture |
| `decisions-register.md` | the 10 decisions only Prospa can make, plus what is also open |
| `sketches/*.excalidraw` | six hand-drawn overviews (build map, funnel, user flow, architecture, site map, wireframes) — open at excalidraw.com |

## Per-pipeline summary

| Pipeline | Stages | Built | Part | Not built | To build | New | Fix | Decide |
|---|---|---|---|---|---|---|---|---|
| 1 · Prospect | 6 | 0 | 0 | 6 | **22** | 15 | 2 | 5 |
| 2 · Engagement | 4 | 2 | 2 | 0 | **22** | 12 | 8 | 2 |
| 3 · Strategy Development | 6 | 5 | 1 | 0 | **18** | 9 | 6 | 3 |
| 4 · Advice Production | 6 | 4 | 2 | 0 | **20** | 13 | 4 | 3 |
| 5 · Advice Presentation | 5 | 1 | 2 | 2 | **18** | 12 | 3 | 3 |
| 6 · Implementation | 8 | 6 | 2 | 0 | **25** | 18 | 4 | 3 |
| 7 · Retention & Growth | 10 | 0 | 0 | 10 | **29** | 24 | 2 | 3 |

## How to read a stage

- **What exists today** — pulled live from the account on 18 Sep 2026 (verified). ✅ works · ⚠️ weak / placeholder · ❌ missing.
- **To build here** — the delta, tagged New / Fix / Check / Decide (inferred from the mapping; review before build).
- **How it should run** — the target trigger → actions for the stage.
- **Client receives / Internal work** — the mapping's two columns, verbatim.

## Source of truth

The interactive board (`prospa-build-blueprint`) is the master. Edit `js/data.js` there and re-run `node tools/export-database.cjs` to refresh this section. Do not hand-edit these files.
