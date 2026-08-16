---
id: s3-entity-model
title: S3 Entity Model - Prospa Financial Database Build
type: system
status: review
confidence: inferred
source: Prospa Financial public website + user build brief 2026-08-16
as_of: 2026-08-16
owner: Ariki Meroiti
tags: [entity-model, schema, approval-required, prospa-financial]
---

# S3 Entity Model — Prospa Financial

> **Approval gate:** This is the one-page schema/model for approval. Per the brief, no database content files should be written until this model is approved.

## Business in 3–5 plain sentences

Prospa Financial is a Melbourne-based boutique financial planning firm serving professionals, families, pre-retirees and business owners. It offers personalised financial advice across wealth, retirement, superannuation, investments, debt management, mortgage broking and protection-related advice. Its published delivery model is a three-step journey: goals discovery, research and advice delivery, then strategy implementation and regular review. The database must support compliant generation of funnels, website copy, newsletters, emails, SMS, ads, social content and sales scripts without inventing financial claims or using approval/guarantee language.

## Core nouns → database entities

| Entity | Folder / file home | Why it exists | Key relationships |
|---|---|---|---|
| Business / company | `01-company/company-profile.md` | Canonical facts about Prospa Financial: name, location, contact, mission, team, process. | Links to team, offers, compliance, source register. |
| Team member / adviser | `01-company/team/` | Adviser and support team facts, roles, bios, publishable authority. | Links to offers they support, proof/credentials, compliance approvals. |
| Process | `01-company/how-we-work.md` | Canonical 3-step method: Goals Discovery → Research & Advice → Implementation & Review. | Linked by offers, funnels, sales scripts. |
| Offer / service line | `02-offer-and-pricing/offers/` | One home per service: retirement planning, superannuation, investment, debt management, mortgage broking, TPD/protection etc. | Links to ICPs, FAQs, compliance rules, proof, playbooks. |
| Pricing / terms | `02-offer-and-pricing/pricing-and-terms.md` | Fees, inclusions/exclusions, call length, deal parameters. | Links to offers and compliance. Initially likely `assumed`/gap until provided. |
| ICP / audience | `03-audience-and-icp/icps/` | One file per priority segment. | Links to offers, objections, voice-of-customer, playbooks. |
| Disqualifier | `03-audience-and-icp/disqualifiers.md` | Who Prospa does not serve and how to decline safely. | Links to sales scripts and compliance. |
| Voice of customer | `03-audience-and-icp/voice-of-customer.md` | Verbatim client/prospect language. | Feeds messaging, banks, sales scripts. |
| Messaging pillar | `04-voice-and-messaging/messaging-pillars.md` | 3–5 arguments every asset maps back to. | Links to ICPs, objections, content banks, playbooks. |
| Brand voice | `04-voice-and-messaging/brand-voice.md` | Tone, rhythm, do/don’t, test sentence. | Loaded by all generation jobs. |
| Banned language | `04-voice-and-messaging/banned-language.md` | Category clichés and regulated/unsafe phrasing. | Must be loaded by every playbook after compliance. |
| Proof item | `05-proof-and-evidence/` | Testimonials, awards, experience claims, credentials, statistics. | Links to source files, offers, compliance claims policy. |
| Competitor | `06-competitors-and-market/competitors/` | Market teardown from competitor’s own words. | Informs positioning, ads, funnel contrast without attack copy. |
| Compliance rule | `07-compliance-and-guardrails/` | Highest-priority constraint layer for financial advice and mortgage/credit claims. | Outranks every other folder. |
| Channel playbook | `08-channels-and-playbooks/` | Executable generation spec for each asset channel. | Load order points into all upstream files. |
| Bank row | `09-content-banks/` | Hooks, subject lines, CTAs, proof lines, objection turns. | Each row links to pillar/offer/ICP and truth tier. |
| FAQ / objection | `10-faq-and-objections/` | Canonical answers and objection handling. | Playbooks paraphrase from here; they do not re-reason. |
| Source material | `99-source-material/` | Raw scrapes, transcripts, PDFs, exports. | Curated files cite back here; generation does not load directly unless auditing. |

## Proposed folder structure

```text
00-start-here/
  AI-INSTRUCTIONS.md
  INDEX.md
  quick-facts.md
  ENRICHMENT-ROADMAP.md
01-company/
  company-profile.md
  how-we-work.md
  site-map-and-routes.md
  team/
    peter-prvulj.md
    neil-mistry.md
    monik-palany.md
    dinal-de-silva.md
    fiona-rintoul.md
    james-larkworthy.md
    sam-ryan.md
    sanika-mane.md
02-offer-and-pricing/
  offer-overview.md
  pricing-and-terms.md
  offers/
    retirement-planning.md
    superannuation.md
    investment.md
    debt-management.md
    mortgage-broking.md
    total-and-permanent-disability.md
03-audience-and-icp/
  buyer-psychology.md
  disqualifiers.md
  voice-of-customer.md
  icps/
    business-owners.md
    professionals-and-families.md
    pre-retirees.md
04-voice-and-messaging/
  brand-voice.md
  messaging-pillars.md
  banned-language.md
  positioning.md
  origin-story.md
05-proof-and-evidence/
  proof-register.md
  testimonials.md
  awards-and-achievements.md
  credentials-and-experience.md
06-competitors-and-market/
  market-context.md
  comparison-matrix.md
  glossary.md
  competitors/
07-compliance-and-guardrails/
  guardrails.md
  claims-policy.md
  regulatory-context.md
  approval-rules.md
  confidentiality.md
08-channels-and-playbooks/
  website-copy-playbook.md
  funnel-playbook.md
  newsletter-playbook.md
  email-playbook.md
  sms-playbook.md
  ads-playbook.md
  social-playbook.md
  sales-scripts-playbook.md
09-content-banks/
  hooks-and-openers.md
  subject-lines.md
  ctas.md
  proof-lines.md
  objection-turns.md
  offer-angles.md
10-faq-and-objections/
  canonical-faq.md
  objections-by-audience.md
  chat-widget-agent-behaviour.md
99-source-material/
  website-scrape-register.md
  raw/
```

## Normalisation decisions

- Company contact details live only in `01-company/company-profile.md`; all playbooks and quick facts link there.
- The three-step process lives only in `01-company/how-we-work.md`; each offer links to it rather than rewriting it.
- Each service promise lives in its offer file; content banks can quote/link but must not redefine the offer.
- Compliance rules live only in `07-compliance-and-guardrails/`; channel playbooks reference them and do not duplicate policy.
- Testimonials and awards live only in `05-proof-and-evidence/`; ads/funnels link to proof-line bank entries that cite proof IDs.
- Audience claims live in ICP files; offer pages link to applicable ICPs.
- FAQ answers live only in `10-faq-and-objections/canonical-faq.md`; playbooks paraphrase them.

## Asset coverage check

| Asset needed | Load path this model supports | Status |
|---|---|---|
| Funnels | Compliance → quick facts → offer → ICP → messaging → proof → funnel playbook → banks | Covered, but needs offer/pricing and compliance confirmation. |
| Website copy | Compliance → company → offer → ICP → voice → proof → website playbook | Covered. |
| Newsletters | Compliance → quick facts → ICP → messaging → proof → newsletter playbook → banks | Covered, but needs newsletter cadence/topics. |
| Emails | Compliance → offer/ICP → objections → email playbook → subject/CTA banks | Covered. |
| SMS | Compliance → banned language → offer/CTA → SMS playbook | Covered, but needs consent/compliance rules. |
| Ads | Compliance → claims policy → ICP → offer → proof → ads playbook | Covered, but needs platform and approval process. |
| Social | Compliance → brand voice → messaging pillars → proof → social playbook | Covered. |
| Sales scripts | Compliance → offer → ICP → objections → sales scripts playbook | Covered, but needs sales call process and objections from client/interview. |

## Approval questions

1. Should the repo proceed from this schema if the `capital-unique-database` reference remains inaccessible, or do you want to provide the working path first?
2. Is the regulatory posture: **Australian financial advice + Australian credit/mortgage broking — no approval/guarantee/performance promise language unless explicitly sourced and compliant**?
3. Are the priority ICPs correct for v1: **business owners**, **professionals/families**, **pre-retirees**?
4. Should `mortgage-broking` remain a first-class offer even though the page says Prospa works with a trusted network of mortgage brokers?
5. Do you want placeholder files for all folders after approval, or only the files that can be grounded from current sources?

## Recommendation

Approve this schema with one condition: `07-compliance-and-guardrails/` should be written before any public-facing content playbook, because this business operates in regulated financial advice / mortgage-adjacent territory and the highest risk is accidental overclaiming.
