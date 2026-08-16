---
id: s1-source-register
title: S1 Source Register - Prospa Financial Database Build
type: source
status: review
confidence: verified
source: Prospa Financial public website scrape and user brief 2026-08-16
as_of: 2026-08-16
owner: Ariki Meroiti
tags: [source-register, intake, prospa-financial, database-build]
---

# S1 Source Register — Prospa Financial

## Build target

- **Project:** DB-Riman
- **Repo name:** `prospafinancial-database`
- **GitHub owner confirmed:** `teamos-ai`
- **Local folder confirmed:** `C:/Users/bmero/Desktop/Ben AI/prospafinancial-database`
- **Client / business:** Prospa Financial — financial advice, financial security and wealth management
- **Assets to support:** funnels, website copy, newsletters, emails, SMS, ads, social, sales scripts
- **Primary published source:** https://prospafinancial.com.au/
- **Gold-standard reference requested:** `~/1-Tumai-Second-Brain/1-projects/capital-unique-database`

## Tool / access notes

- Public website extraction worked via `web_extract`.
- Local search did **not** find `capital-unique-database` under `C:/Users/bmero` or `C:/Users/bmero/Desktop`.
- NAS vault access to the remembered `obsibrain-vault` path failed with Windows auth error, so the gold-standard reference has not yet been opened.
- `gh repo view` did not find `teamos-ai/capital-unique-database` or `FlashedBAM/capital-unique-database` from the currently authenticated GitHub context.
- Because the brief says the entity model must be approved before content files are written, this folder currently contains planning outputs only — no database content layer yet.

## Source register

| Source | Type | What it covers | Authority | Trust tier | Date / freshness | Notes |
|---|---|---|---|---|---|---|
| User brief in Discord document `message.txt` | Client instruction / build brief | Build rules, repo name, assets list, database architecture, schema, stages | Primary for build requirements | verified | 2026-08-16 | Governs the build. Contains placeholders for GitHub account/location that were clarified in-chat. |
| https://prospafinancial.com.au/ | First-party website home page | Positioning, mission, audiences, service list, CTA, testimonials, contact details, address, claimed experience | Primary public source | verified for published wording | Extracted 2026-08-16 | Main canonical published copy. Some links and duplicated sections appear messy; should be captured as source quirks. |
| https://prospafinancial.com.au/about-us/ | First-party website about page | About copy, team list, why choose us, claimed customers/experience, achievements images | Primary public source | verified for published wording | Extracted 2026-08-16 | Claims like `500+ Satisfied Customers` and `50+ Years of Experience` are published but need compliance review before marketing use. |
| https://prospafinancial.com.au/services/retirement-planning/ | First-party service page | Retirement planning offer copy, 3-step process, FAQs | Primary public source | verified for published wording | Extracted 2026-08-16 | Useful for offer/service file and FAQ. |
| https://prospafinancial.com.au/services/mortgage-broking/ | First-party service page | Mortgage broking offer copy, process, FAQs | Primary public source | verified for published wording | Extracted 2026-08-16 | Regulatory posture may include Australian credit rules; do not imply loan approval/guarantee. |
| https://prospafinancial.com.au/services/debt-management/ | First-party service page | Debt management offer copy, process, FAQs | Primary public source | verified for published wording | Extracted 2026-08-16 | Contains strong debt outcome language that needs guardrails before reuse. |
| Gold-standard `capital-unique-database` | Reference repo | Desired database structure and file shapes | Intended primary reference for build structure | not accessed | Pending | Blocked by local/NAS/GitHub lookup. Need user path or access confirmation. |

## Early verified facts from the public site

These are source-register notes only, not final database entries.

- Prospa Financial describes itself as a boutique firm in Melbourne, Australia specialising in personalised financial planning services.
- Published mission language: empowering professionals, families, pre-retirees and business owners with personalised financial advice to make smart financial choices, enhance financial security, increase confidence and build a more prosperous future.
- Published CTA: `Book a Free Call` / `Discuss your Financial Goal and Aspirations with a Senior Financial Adviser`.
- Published call duration: 15 minute call to learn about services and how Prospa helps clients.
- Published address: Level 1/36 Mills St, Albert Park VIC 3206, Australia.
- Published phone: +61 3 8807 8000.
- Published email: admin@prospafinancial.com.au.
- Published services seen: mortgage broking, debt management, retirement planning, superannuation, investment, total and permanent disability; homepage indicates a broader service list.
- Published audiences: business owners, professionals and families, pre-retirees.
- Published process repeated on service pages: Goals Discovery Meeting → Research & Advice Delivery → Strategy Implementation & Regular Review.
- Published team names/roles include Peter Prvulj, Neil Mistry, Monik Palany, Dinal De Silva, Fiona Rintoul, James Larkworthy, Sam Ryan, Sanika Mane.

## Gap list for interview / source harvest

High leverage gaps that the website does not answer cleanly enough:

1. **Regulatory posture:** Exact compliance requirements for financial advice, mortgage/credit language, claims, testimonials, disclaimers, approval workflow and banned phrasing.
2. **AFSL / credit licence / authorised representative details:** Not yet captured from the public scrape. Need official licence/source before any compliance file is approved.
3. **Current offers and pricing:** Website lists services, but not package boundaries, fees, inclusions/exclusions, onboarding process or eligibility.
4. **Who they turn away:** No clear disqualifiers yet.
5. **Best-fit ICPs:** Website gives broad audience groups, but not priority segments, trigger events, deal size, urgency, objections or pains in client language.
6. **Voice-of-customer:** Testimonials exist, but no call transcripts, lead forms, objections, sales notes or customer interviews captured yet.
7. **Proof permission:** Testimonials are published, but reuse permission and exact compliance-safe usage needs confirmation.
8. **Achievements:** Achievement images exist but text/award names are not extracted. Need image/OCR or original award source before claims can be used.
9. **Brand voice:** Public copy has a tone, but the client’s preferred/forbidden language is unknown.
10. **Funnels and campaign history:** No past campaigns, conversion data, newsletters, ads, SMS, GHL forms/pipelines/workflows or sales scripts harvested yet.
11. **Competitors and market:** Not researched yet.
12. **Asset-specific requirements:** Need confirm exact funnel pages, newsletter frequency, email/SMS sequence length, ad platforms, social channels, and sales-script use cases.
13. **GHL / CRM source:** User mentioned OS AI onboarding context earlier, but no Prospa GHL export/pipeline was pulled for this build yet.
14. **Gold-standard reference access:** Need a working path or repo access to `capital-unique-database` before modelling final file shapes.

## Recommended next action before content build

1. Get access/path to the gold-standard reference repo or confirm I should proceed from the prompt’s architecture alone.
2. Approve or edit the S3 entity model in `S3-ENTITY-MODEL.md`.
3. Answer one focused interview round against the gap list.
4. Then scaffold the private `teamos-ai/prospafinancial-database` repo and commit structure-only placeholders.
