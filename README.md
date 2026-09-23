# hmz-paperclip-lead-engine

> > Claims in this README should remain evidence-backed and consistent with the current repository.

<p align="center"><a href="https://github.com/hmzainjamil/hmz-paperclip-lead-engine">Repository</a> · <a href="https://github.com/hmzainjamil/hmz-paperclip-lead-engine/commits/main">Commits</a> · <a href="https://github.com/hmzainjamil/hmz-paperclip-lead-engine/issues">Issues</a></p>

<p align="center"><img alt="Visibility" src="https://img.shields.io/badge/visibility-public-blue"> <img alt="Lifecycle" src="https://img.shields.io/badge/lifecycle-active-success"> <img alt="Documentation" src="https://img.shields.io/badge/documentation-deep%20editorial-lightgrey"></p>

<!-- HMZ DEEP README v1 -->

## At a glance

| Field | Current state |
|---|---|
| Visibility | public |
| Lifecycle | Active |
| Repository size | 17 KB |
| Default branch | main |
| Evidence basis | Current repository documentation and source-visible material |

## Why this exists

> Claims in this README should remain evidence-backed and consistent with the current repository.

This README separates documented capabilities from measured evidence and avoids converting roadmap ideas or external assumptions into implementation claims.

## 🧠 CONCEPTS

| Feature | Location | Description |
|---|---|---|
| [Paperclip-Lead-Engine Core](bin/) | `bin/` | Primary automation scripts and tools for hmz-paperclip-lead-engine |
| [MAE Integration](bin/mae-bridge.sh) | `bin/mae-bridge.sh` | 12-agent swarm on every task — automatic decompose, execute, synthesize |
| [Tier 0 Routing](config/model-rules.json) | `config/model-rules.json` | Groq→Gemini→Bytez→DeepSeek — zero Claude tokens for sub-tasks |
| [TCC Queue](tcc-routes/routes.json) | `tcc-routes/routes.json` | Task routing — 18 specialist agents, wave-batched for RAM safety |
| [LaunchAgent](launchd/) | `launchd/` | macOS always-on service — KeepAlive=true, RunAtLoad=true |
| [Hooks](hooks/) | `hooks/` | UserPromptSubmit, PostToolUse, Stop hooks wired for full automation |
| [Skill Router](skills/skill-router/) | `skills/skill-router/` | Keyword → skill auto-activation on every prompt submission |
| [n8n Workflows](workflows/) | `workflows/` | 8,159 workflow JSONs — grep before building anything from scratch |
| [Paperclip Sync](bin/paperclip-sync.sh) | `bin/paperclip-sync.sh` | All outputs auto-saved to Paperclip AI company OS |
| [Health Monitor](bin/health.sh) | `bin/health.sh` | Pings all endpoints — Slack alert + auto-restart on failure |
| [Logs](logs/) | `logs/` | Timestamped run logs — searchable audit trail across sessions |
| [Config](config/) | `config/` | API keys references, model routing rules, environment settings |
| [Scripts](scripts/) | `scripts/` | Setup, teardown, testing, and benchmarking utility scripts |
| [Templates](templates/) | `templates/` | Reusable output templates — PDF, Markdown, JSON, CSV |
| [Docs](docs/) | `docs/` | Documentation, SOPs, architecture diagrams, runbooks |
| [Tests](tests/) | `tests/` | Integration tests — verifies all API connections and workflows |
| [Deployment](deploy/) | `deploy/` | Docker, LaunchAgent, systemd deployment configurations |
| [Webhooks](webhooks/) | `webhooks/` | Inbound webhook handlers for external system triggers |
| [Reports](reports/) | `reports/` | Auto-generated reports — ReportLab PDF, Markdown summaries |
| [Cron](cron/) | `cron/` | Scheduled job configs — hourly, daily, weekly automation triggers |
| [API Clients](api/) | `api/` | Thin API client wrappers for all external service integrations |
| [Data](data/) | `data/` | Input datasets, lookup tables, static reference data files |
| [Archive](archive/) | `archive/` | Historical outputs and versioned artifacts — never deleted |
| [Backup](backup/) | `backup/` | Backup configs and restore scripts for all critical data |
| [CLAUDE.md](CLAUDE.md) | `CLAUDE.md` | Repo-specific rules injected into every Claude session context |

## ⚙️ ARCHITECTURE

```
┌────────────────────────────────────────────────────────────────┐
│                HMZ AI STACK — TIER 0 ARCHITECTURE              │
│                                                                │
│  Every Prompt → skill-router → Tier 0 model → MAE swarm       │
│                                                                │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐     │
│  │  Ollama  │  │  Groq    │  │ Gemini   │  │  Bytez   │     │
│  │ GPU local│  │  70b     │  │  Flash   │  │ 100+ LLM │     │
│  │  $0/run  │  │  free    │  │  free    │  │  free    │     │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘     │
│                         │                                      │
│             MAE 12-agent swarm (TCC queue)                     │
│             Groq-70B synthesis → final output                  │
│                         │                                      │
│  OpenCLI (90 adapters) · Composio (3000+ actions) · n8n       │
│  Paperclip OS · MEMORY.md · ~/.claude/tcc-logs/               │
└────────────────────────────────────────────────────────────────┘
```

| Layer | Technology | Cost |
|---|---|---|
| Local inference | Ollama + GPT4All (7 models) | $0 forever |
| Cloud burst | Groq + Gemini + Bytez | $0 free tiers |
| Orchestration | MAE + TCC + llm-burst | $0 (uses Tier 0) |
| Automation | n8n 8,159 workflows | Self-hosted |
| Memory | Paperclip AI + MEMORY.md | Zero-human |
| Site automation | OpenCLI 90+ adapters | $0 no LLM cost |
| SaaS actions | Composio 3000+ tools | Free tier |

## 🚀 Quick Start

```bash
# Run 12-agent MAE swarm on any goal
mae run "write a cold email sequence for B2B SaaS"

# Fire tasks in parallel
tcc blast "audit Google Ads" "spy Meta ads" "draft LinkedIn post"

# Full agency daily ops (all divisions automated)
mae daily

# OpenCLI — scrape any site without LLM cost
opencli linkedin search --query "SaaS founder"

# Composio — execute any SaaS action
composio execute hubspot create-contact --name "John" --email "j@co.com"

# System status
tcc-dashboard
```

## Usage

No verified runtime command was available in the current README. Commands should be taken from executable entry points and package configuration.

## ⚡ CONFIGURATION REFERENCE

| Variable | Location | Value / Purpose |
|---|---|---|
| `GROQ_API_KEY` | `~/.zshrc` | Groq llama3-70b — fastest free cloud LLM |
| `OPENROUTER_API_KEY` | `~/.zshrc` | OpenRouter — 100+ models via one endpoint |
| `GOOGLE_API_KEY` | `~/.zshrc` | Gemini 2.0 Flash — 1M context free tier |
| `BYTEZ_API_KEY` | `~/.zshrc` | <redacted secret> |
| `DASHSCOPE_API_KEY` | `~/.zshrc` | Alibaba DashScope — Qwen models |
| `LUMA_API_KEY` | `~/.zshrc` | Luma uni-1 image generation API |
| `ARCADS_API_KEY` | `~/.zshrc` | Arcads AI actor video generation |
| `AIRTABLE_API_KEY` | `~/.zshrc` | Airtable data automation API |
| `NODE_PATH` | `~/.zshrc` | <local path> |
| `OLLAMA_HOST` | `~/.zshrc` | http://localhost:11434 (always-on) |
| `OLLAMA_NUM_GPU` | `LaunchAgent` | 1 — Metal GPU acceleration |
| `N8N_HOST` | `~/.zshrc` | http://localhost:5678 (n8n server) |
| `COMPOSIO_API_KEY` | `~/.zshrc` | Composio tool actions API |
| `PAPERCLIP_URL` | `~/.zshrc` | http://127.0.0.1:3100 (company OS) |

## Validation and evidence

No dedicated test or evaluation section was available in the current README. Performance, production readiness, and outcome claims are not asserted here.

## Security

Keep credentials outside the repository, validate untrusted inputs at system boundaries, and grant external tools only the permissions they require.

## Limitations

- Planned functionality is not presented as completed functionality.
- Quantitative claims should be backed by reproducible repository evidence.
- External provider behavior, limits, and pricing are not inferred from repository documentation.



## Maintainer

[hmzainjamil](https://github.com/hmzainjamil)