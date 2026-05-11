# hmz-paperclip-lead-engine

> **Autonomous lead generation + enrichment engine | runs 7:30 AM daily | zero manual prospecting**

[![schedule](https://img.shields.io/badge/schedule-7%3A30AM_daily-blue?style=flat)](.) [![leads](https://img.shields.io/badge/output-qualified_leads-green?style=flat)](.) [![status](https://img.shields.io/badge/status-always_on-brightgreen?style=flat)](.) [![company](https://img.shields.io/badge/company-DigiMinds-orange?style=flat)](.)

[Overview](#overview) · [Pipeline](#pipeline) · [Sources](#sources) · [Output](#output) · [Config](#config) · [Tips](#tips)

---

## 🧠 OVERVIEW

Paperclip Lead Engine runs at 7:30 AM every morning. It scrapes qualified leads from LinkedIn, Apollo, and job boards — enriches them with company data — scores them against DigiMinds ICP — and drops them directly into the CRM pipeline. HMZ wakes up to a pre-filled, pre-scored lead list.

| Component | Value |
|---|---|
| Trigger | Daily 7:30 AM (LaunchAgent) |
| Sources | LinkedIn, Apollo, Indeed, job boards |
| ICP | PPC/Google Ads/Meta Ads businesses, $1K-$50K/mo spend |
| Output | Enriched leads → Paperclip CRM |
| Model | Groq Llama 3 (zero Claude tokens) |

---

## ⚙️ PIPELINE

```
07:30 AM trigger
    │
    ├─► Scrape LinkedIn (Apify actor: linkedin-jobs-scraper)
    ├─► Search Apollo: title=Marketing Manager, industry=ecommerce
    ├─► Pull Indeed: "google ads" + "meta ads" job postings
    │
    ├─► Enrich each lead: company revenue, ad spend signals, tech stack
    ├─► ICP score: 0-100 (80+ = hot, 50-79 = warm, <50 = cold)
    │
    └─► POST /api/leads → Paperclip CRM with score + enrichment
```

| Stage | Tool | Time |
|---|---|---|
| Scrape | Apify actors (LinkedIn, Apollo) | ~3 min |
| Enrich | Apollo bulk enrich API | ~2 min |
| Score | Groq Llama 3 (ICP rules) | ~1 min |
| Store | Paperclip CRM API | <30s |

---

## 🎯 ICP SCORING RULES

| Signal | Points |
|---|---|
| Active Google Ads spend detected | +30 |
| Active Meta Ads spend detected | +20 |
| Company size 10-200 employees | +15 |
| Industry: ecommerce, DTC, SaaS | +20 |
| Job post mentions PPC/CRO/ROAS | +25 |
| No agency relationship evident | +15 |
| LinkedIn ad library shows active creatives | +20 |

**Threshold:** 80+ = hot (direct outreach), 50-79 = warm (nurture), <50 = discard

---

## 💡 TIPS

■ **Lead Quality (5)**
| Tip | Source |
|---|---|
| Best leads come from companies posting PPC job roles — they have budget but no one to run it | Prospecting SOP |
| LinkedIn ad library signals are the strongest ICP indicator | DigiMinds playbook |
| Apollo bulk enrich is 10x faster than individual enrichment | Apollo docs |
| Discard all India/Pakistan/Bangladesh/Philippines/Israel geos | HMZ blacklist |
| Companies spending $5K+/mo on ads = perfect DigiMinds client | ICP definition |

■ **Operations (4)**
| Tip | Source |
|---|---|
| Engine runs even on weekends — leads accumulate for Monday review | Schedule SOP |
| If Apify actor fails, fallback to Apollo search only | Error handling |
| Check `/api/leads?date=today` to see today's batch | API ref |
| ICP scores are recalculated weekly as rules improve | Auto-learning |

---

## ☠️ TOOLS REPLACED

| Lead Engine | Replaced |
|---|---|
| Automated daily prospecting | Manual LinkedIn sourcing (2h/day) |
| ICP scoring | Gut-feel qualification |
| Lead enrichment | Manual Google/LinkedIn research |
| CRM entry | Copy-paste into spreadsheets |

---

## ⚠️ GOTCHAS

| Issue | Fix |
|---|---|
| Apify actor rate-limited | Engine auto-retries at 8:30 AM |
| Apollo credits exhausted | Falls back to basic LinkedIn data only |
| 0 leads scored above 50 | ICP rules too strict — review thresholds |
| Duplicate leads in CRM | Engine deduplicates by LinkedIn URL |
| Engine ran late (after 8 AM) | LaunchAgent StartCalendarInterval can drift — verify with `launchctl list` |

---

## 🚀 SETUP

```bash
# Check lead engine status
curl http://127.0.0.1:3100/api/leads?date=today

# View logs
tail -f ~/Library/Logs/paperclip-lead-engine.log

# Manual trigger
~/.claude/bin/paperclip-lead-engine

# See all hot leads (score 80+)
curl "http://127.0.0.1:3100/api/leads?score_min=80&date=today"
```

---

*Part of [DigiMinds AI Agency Stack](https://github.com/hmzainjamil) — Paperclip autonomous lead generation*
