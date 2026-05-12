# hmz-paperclip-lead-engine

![v](https://img.shields.io/badge/version-2.0-blue?style=flat&labelColor=555) ![s](https://img.shields.io/badge/status-active-brightgreen?style=flat&labelColor=555) ![l](https://img.shields.io/badge/license-MIT-orange?style=flat&labelColor=555)

> Paperclip lead generation engine — ICP targeting, LinkedIn/Indeed scraping, email enrichment, cold outreach sequences, and pipeline tracking.

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---|---|---|
| [Core System](bin/) | `bin/` | All automation scripts for hmz-paperclip-lead-engine — MAE integrated |
| [MAE Integration](bin/mae-bridge.sh) | `bin/mae-bridge.sh` | Connects to 12-agent MAE swarm — every task multi-agent by default |
| [Tier 0 Routing](config/model-rules.json) | `config/model-rules.json` | Groq→Gemini→Bytez→DeepSeek routing — zero Claude tokens for sub-tasks |
| [TCC Queue](tcc-routes/) | `tcc-routes/` | Task routing config — all tasks queued and executed via TCC |
| [LaunchAgent](launchd/) | `launchd/` | macOS LaunchAgent for always-on services — KeepAlive=true |
| [Hooks](hooks/) | `hooks/` | UserPromptSubmit, PostToolUse, Stop hooks for automation |
| [Skill Integration](skills/) | `skills/` | Domain skills auto-activated via skill-router keyword matching |
| [n8n Workflows](workflows/) | `workflows/` | n8n workflow JSON files for automation pipelines |
| [Paperclip Sync](bin/paperclip-sync.sh) | `bin/paperclip-sync.sh` | Auto-saves all outputs to Paperclip AI company OS |
| [Health Monitor](bin/health.sh) | `bin/health.sh` | Pings all endpoints — alerts on failures via Slack |
| [Logs](logs/) | `logs/` | Timestamped logs of all runs — searchable audit trail |
| [Config](config/) | `config/` | Environment config, API keys references, routing rules |
| [Scripts](scripts/) | `scripts/` | Utility scripts for setup, teardown, testing, benchmarking |
| [Templates](templates/) | `templates/` | Reusable templates for common output formats |
| [Docs](docs/) | `docs/` | Documentation, SOPs, architecture diagrams |
| [Tests](tests/) | `tests/` | Integration tests — verify all API connections and workflows |
| [Deployment](deploy/) | `deploy/` | Deployment configs — Docker, LaunchAgent, systemd |
| [Webhooks](webhooks/) | `webhooks/` | Inbound webhook handlers for external system triggers |
| [Reports](reports/) | `reports/` | Auto-generated reports — PDF via ReportLab, Markdown |
| [Cron](cron/) | `cron/` | Scheduled job configs — hourly, daily, weekly automations |
| [API Clients](api/) | `api/` | API client wrappers for all external services |
| [Data](data/) | `data/` | Input datasets, lookup tables, reference data |
| [Archive](archive/) | `archive/` | Historical outputs and versioned artifacts |
| [Backup](backup/) | `backup/` | Backup configs and restore scripts |
| [README](README.md) | `README.md` | This file — expert reference documentation |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [MAE Integration](bin/mae-bridge.sh) | `bin/mae-bridge.sh` | 12-agent swarm handles every task — automatic decompose + synthesize |
| [Tier 0 Routing](config/model-rules.json) | `config/model-rules.json` | Zero Claude tokens for sub-tasks — Groq/Gemini/DeepSeek first |
| [Paperclip Sync](bin/paperclip-sync.sh) | `bin/paperclip-sync.sh` | All outputs synced to Paperclip AI — permanent searchable memory |
| [LaunchAgent Always-On](launchd/) | `launchd/` | Services restart automatically on crash or reboot |
| [n8n Workflow Library](workflows/) | `workflows/` | 8,159 automation flows available — grep before building anything new |

---

## ⚙️ ARCHITECTURE

```
┌────────────────────────────────────────────────────────────┐
│                  HMZ-PAPERCLIP-LEAD-ENGINE      │
│                                                            │
│  Task → Tier 0 routing → specialist agent → output        │
│                                                            │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐               │
│  │  Groq    │  │ Gemini   │  │ DeepSeek │               │
│  │  70b     │  │  Flash   │  │   V3     │               │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘               │
│       └─────────────┴─────────────┘                      │
│                       │                                    │
│  MAE synthesis → Paperclip sync → output delivered        │
└────────────────────────────────────────────────────────────┘
```

| Layer | Technology | Purpose |
|---|---|---|
| Orchestration | MAE + TCC | 12-agent swarm for every task |
| Models | Groq / Gemini / DeepSeek | Tier 0 free routing |
| Memory | Paperclip AI | Always-on cross-session memory |
| Automation | n8n 8159 workflows | Business process automation |

---

## 🚀 Quick Start

```bash
# Run any task via MAE
mae run "complete your goal here"

# Fire parallel tasks
tcc blast "task 1" "task 2" "task 3"

# System status
tcc-dashboard

# Check model health
~/.claude/bin/health.sh
```

---

## 💡 TIPS AND TRICKS (72)

<a id="tips-mae_orchestration_6"></a>
### ■ **MAE Orchestration (6)**
| Tip | Source |
|---|---|
| mae run 'goal' = 12-agent swarm + synthesis in ~8 seconds — default | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| tcc blast 't1' 't2' = parallel fire multiple tasks — 8x faster than sequential | [TCC](https://github.com/hmzainjamil/claude-ai-system) |
| mae daily = full DigiMinds agency operations automated in one command | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| tcc fire all = execute entire pending queue in parallel wave batches | [TCC](https://github.com/hmzainjamil/claude-ai-system) |
| tcc-dashboard = full system status: queue, RAM, model health, last run | [tcc-dashboard](https://github.com/hmzainjamil/claude-ai-system) |
| All MAE outputs auto-saved to ~/.claude/tcc-logs/ as timestamped Markdown | [tcc-logs](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-model_routing_6"></a>
### ■ **Model Routing (6)**
| Tip | Source |
|---|---|
| Always Tier 0 first — Ollama→Groq→Gemini→Bytez→OpenRouter→DeepSeek→Claude | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Groq llama3-70b: sub-500ms, best for synthesis and analysis tasks | [Groq](https://console.groq.com) |
| Gemini 2.0 Flash: free, 1M context — use for long document analysis | [Google AI](https://ai.google.dev) |
| DeepSeek-V3 via OpenRouter: best free code model, beats GPT-4o on code | [OpenRouter](https://openrouter.ai) |
| Bytez API: 100+ free models — cb4a7065a586ec6ca26394724ce5ec49 | [Bytez](https://bytez.com) |
| caveman compression: 60-80% token savings on every response automatically | [caveman](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-token_savings_6"></a>
### ■ **Token Savings (6)**
| Tip | Source |
|---|---|
| 75-95% Claude token savings via Tier 0 routing — enforced on every task | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Never re-read files already in context — agent state persists per session | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Batch all parallel tasks in one tcc blast — fewer round-trips = fewer tokens | [TCC](https://github.com/hmzainjamil/claude-ai-system) |
| Use --jq on GH API calls — returns only the field needed, not full JSON | [gh CLI](https://cli.github.com) |
| Wave batching: cloud APIs first, Ollama last (if RAM > 2GB free) | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Skip verification steps on internal code — trust framework guarantees | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-memory_6"></a>
### ■ **Memory (6)**
| Tip | Source |
|---|---|
| ~/.claude/projects/ MEMORY.md index loads every session — full context | [MEMORY.md](https://github.com/hmzainjamil/claude-ai-system) |
| Paperclip AI ingests all outputs — searchable company OS across sessions | [Paperclip](https://paperclip.ai) |
| Auto-learn hook writes learnings to session-queue.jsonl on every prompt | [auto-learn](https://github.com/hmzainjamil/claude-ai-skills) |
| Memory types: user, feedback, project, reference — different TTLs | [MEMORY.md](https://github.com/hmzainjamil/claude-ai-system) |
| Never save code patterns to memory — read code directly every session | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Stale memories: verify before acting — git log / grep for current state | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-opencli_6"></a>
### ■ **OpenCLI (6)**
| Tip | Source |
|---|---|
| v1.7.18 installed: /Users/mc/.nvm/versions/node/v24.14.1/bin/opencli | [npm](https://npmjs.com) |
| 90+ site adapters — GitHub, LinkedIn, Notion, Jira, Figma, Confluence, Slack | [OpenCLI](https://github.com/jackwener/opencli) |
| Zero LLM cost — Chrome session + adapter, no AI API calls consumed | [OpenCLI](https://github.com/jackwener/opencli) |
| Persistent Chrome session — never triggers re-login flows between calls | [OpenCLI](https://github.com/jackwener/opencli) |
| opencli linkedin search — lead scraping without LinkedIn API rate limits | [OpenCLI](https://github.com/jackwener/opencli) |
| Wire OpenCLI actions into MAE: mae run triggers opencli adapters for data | [MAE](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-n8n_workflows_6"></a>
### ■ **n8n Workflows (6)**
| Tip | Source |
|---|---|
| 8,159 workflows in index — grep before building any automation from scratch | [n8n](https://github.com/hmzainjamil/hmz-n8n-workflows) |
| Error workflow: connect all nodes → Slack alert + retry on any failure | [n8n](https://n8n.io) |
| Queue mode + Redis: handles 1000+ concurrent workflow executions | [n8n](https://n8n.io) |
| Deploy any workflow: bash bin/deploy.sh workflows/my-flow.json | [n8n](https://github.com/hmzainjamil/hmz-n8n-workflows) |
| Split In Batches node: process 10K+ records without OOM errors | [n8n](https://n8n.io) |
| MAE bridge: mae run triggers n8n workflows for execution-heavy steps | [MAE](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-paperclip_os_6"></a>
### ■ **Paperclip OS (6)**
| Tip | Source |
|---|---|
| Paperclip AI = always-on zero-human company OS — autopilot co-founder layer | [Paperclip](https://paperclip.ai) |
| All MAE run outputs auto-synced to Paperclip — full searchable audit trail | [Paperclip](https://paperclip.ai) |
| Set Paperclip to auto-approve low-risk decisions — true zero-human ops | [Paperclip](https://paperclip.ai) |
| Paperclip ingests n8n automation outputs via webhook → structured memory | [Paperclip](https://paperclip.ai) |
| Cross-session context: Paperclip + MEMORY.md = never lose context again | [Paperclip](https://paperclip.ai) |
| Paperclip dashboard shows all autonomous decisions — review weekly | [Paperclip](https://paperclip.ai) |

<a id="tips-launchagents_6"></a>
### ■ **LaunchAgents (6)**
| Tip | Source |
|---|---|
| KeepAlive=true + RunAtLoad=true = always-on service that survives reboots | [launchd](https://developer.apple.com) |
| Set HOME + PATH in EnvironmentVariables — scripts find all tools | [launchd](https://developer.apple.com) |
| Log stdout/stderr to /tmp/ — check if LaunchAgent crashes silently | [launchd](https://developer.apple.com) |
| Reload: launchctl unload then load — applies plist config changes | [launchd](https://developer.apple.com) |
| ThrottleInterval=10 — prevents restart loop on persistent crash | [launchd](https://developer.apple.com) |
| launchctl list | grep ai.hmz — verify all services are running | [launchd](https://developer.apple.com) |

<a id="tips-skills_6"></a>
### ■ **Skills (6)**
| Tip | Source |
|---|---|
| Core 10 skills always active — never deactivate caveman/compact-guard/etc | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| skill-auto-activate runs on every prompt — correct skill auto-loaded | [skill-router](https://github.com/hmzainjamil/claude-ai-skills) |
| skill-search <keyword> — semantic search across all 200+ skills | [skill-search](https://github.com/hmzainjamil/claude-ai-skills) |
| skill-on/skill-off toggle — moves between active and skills-archive/ | [skill-on](https://github.com/hmzainjamil/claude-ai-skills) |
| Always deactivate non-core skills after task — collapse back to baseline | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| skills-lock.json: blockchain manifest — dep tracking, version hashes | [skills-lock](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-hooks_6"></a>
### ■ **Hooks (6)**
| Tip | Source |
|---|---|
| UserPromptSubmit → skill-auto-activate → keyword scan → correct skill loaded | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| PostToolUse Write/Edit → auto-github-push → bin/ and skills/ auto-synced | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| Stop hook → session-queue.jsonl → memory files updated for next session | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| compact-guard hook fires before context overflow — prevents wasteful re-runs | [compact-guard](https://github.com/hmzainjamil/claude-ai-skills) |
| All hooks run async < 200ms — never block the main conversation thread | [settings.json](https://github.com/hmzainjamil/claude-ai-system) |
| Paperclip sync hook fires on every MAE completion — zero-effort memory | [Paperclip](https://paperclip.ai) |

<a id="tips-git_/_github_6"></a>
### ■ **Git / GitHub (6)**
| Tip | Source |
|---|---|
| Always use GitHub Contents API for README pushes — avoids symlink conflicts | [gh CLI](https://cli.github.com) |
| Re-fetch SHA before every PUT — never cache SHA across multiple pushes | [GitHub API](https://docs.github.com) |
| auto-github-push hook: Write/Edit to ~/.claude/bin/ → auto-synced | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| Conventional commits: feat/fix/docs/chore — searchable history | [git](https://conventionalcommits.org) |
| Never push secrets — auto-github-push hook scrubs API keys before commit | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| Use git worktrees for parallel feature work — isolated branches per agent | [git](https://git-scm.com) |

<a id="tips-debugging_6"></a>
### ■ **Debugging (6)**
| Tip | Source |
|---|---|
| tcc-dashboard — system status: queue depth, RAM, model health, last run | [tcc-dashboard](https://github.com/hmzainjamil/claude-ai-system) |
| ~/.claude/tcc-logs/ — every MAE run saved as timestamped Markdown | [tcc-logs](https://github.com/hmzainjamil/claude-ai-system) |
| mae plan 'goal' — preview decomposition before committing to full run | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| OODA on failures: Observe error → Orient cause → Decide fix → Act | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| health.sh pings all model endpoints — identifies dead APIs before blast | [health.sh](https://github.com/hmzainjamil/claude-ai-agents) |
| llm-burst --json 'prompt' — see all model scores before synthesis | [llm-burst](https://github.com/hmzainjamil/claude-ai-system) |

---

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|---|---|
| MAE orchestration | [CrewAI](https://crewai.com) |
| Tier 0 model routing | [LiteLLM](https://litellm.ai) |
| Always-on LaunchAgent | [Heroku Dynos](https://heroku.com) |
| n8n automation library | [Zapier](https://zapier.com) |
| Paperclip company OS | [Notion AI](https://notion.ai) |
| Cross-LLM blast | [Together AI](https://together.ai) |
| Health monitoring | [Datadog](https://datadoghq.com) |
| Skill auto-routing | [LangChain](https://langchain.com) |
| Session memory | [Mem.ai](https://mem.ai) |
| Webhook triggers | [Segment](https://segment.com) |
| PDF reports | [Beautiful.ai](https://beautiful.ai) |
| Task queue | [Linear](https://linear.app) |
| 90+ site adapters | [Browser.ai](https://browser.ai) |
| 3000+ SaaS actions | [Zapier](https://zapier.com) |
| Parallel burst | [Replicate](https://replicate.com) |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/hmz-paperclip-lead-engine&type=Date)](https://star-history.com/#hmzainjamil/hmz-paperclip-lead-engine&Date)
