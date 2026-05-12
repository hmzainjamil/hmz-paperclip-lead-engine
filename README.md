# hmz-paperclip-lead-engine
> Autonomous lead generation — Vibe Prospecting → Apollo → Excel → outreach. Part of the DigiMinds Paperclip automation engine suite.

[![paperclip](https://img.shields.io/badge/Paperclip-engine-blue?style=flat&labelColor=555)](https://github.com/paperclipai/paperclip)
[![mae](https://img.shields.io/badge/MAE-powered-green?style=flat&labelColor=555)](.)
[![tools](https://img.shields.io/badge/tools-Vibe-orange?style=flat&labelColor=555)](.)
[![tier0](https://img.shields.io/badge/tier0-zero--cost-purple?style=flat&labelColor=555)](.)
[![license](https://img.shields.io/badge/license-MIT-lightgrey?style=flat&labelColor=555)](LICENSE)

[concepts](#concepts) · [architecture](#architecture) · [tips](#tips) · [startups](#startups) · [star](#star)

---

## 🧠 CONCEPTS <a id="concepts"></a>

| Feature | Location | Description |
|---|---|---|
| [**Core Engine**](engine/) | `engine/` | Main orchestration loop — reads from Paperclip → executes → reports back |
| [**Paperclip Sync**](sync/) | `sync/` | Bidirectional sync with Paperclip API at localhost:3100 |
| [**MAE Integration**](mae/) | `mae/` | Routes tasks through MAE swarm — wave-batched, RAM-safe |
| [**Tier 0 Routing**](routing/) | `routing/` | Tools used: Vibe MCP · Apollo MCP · openpyxl |
| [**Output Storage**](outputs/) | `outputs/` | Results saved to `~/.claude/tcc-logs/` + synced to Paperclip |
| [**LaunchAgent**](launchagents/) | `launchagents/` | Optional persistent LaunchAgent — runs engine on schedule |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [**Zero-cost execution**](engine/) | `engine/` | All processing via Tier 0 models — Groq, Gemini, Kimi, Bytez |
| [**Auto-retry**](engine/) | `engine/` | Failed tasks auto-retry with fallback model via TCC retry mechanism |
| [**Paperclip goal sync**](sync/) | `sync/` | Reads outstanding goals from Paperclip every run cycle |

---

## ⚙️ ARCHITECTURE <a id="architecture"></a>

```
Paperclip CEO Layer (localhost:3100)
         │
         │ reads goals + tasks
         ▼
    Lead Engine Engine
         │
    MAE decompose
         │
    Tier 0 swarm (Vibe MCP · Apollo MCP · openpyxl)
         │
    synthesis + output
         │
         │ reports results
         ▼
Paperclip CEO Layer (updated goals)
```

| Phase | Model | Purpose |
|---|---|---|
| Decompose | Groq llama-3.1-8b-instant | Break goal into sub-tasks |
| Execute | Vibe MCP + more | Run specialist tasks |
| Synthesize | Groq llama-3.3-70b-versatile | Merge outputs |
| Report | Paperclip API | Update goal status |

---

## 💡 TIPS AND TRICKS (8) <a id="tips"></a>

[engine-ops](#tips-ops) · [paperclip-integration](#tips-pc)

<a id="tips-ops"></a>
■ **Engine Operations (4)**

| Tip | Source |
|---|---|
| Start: `python3 engine/main.py` or load LaunchAgent for persistent operation | [hmzainjamil](https://github.com/hmzainjamil) |
| `mae run "goal"` triggers this engine via TCC routing when keyword matches | [hmzainjamil](https://github.com/hmzainjamil) |
| All outputs go to `~/.claude/tcc-logs/mae-TIMESTAMP.md` — searchable history | [hmzainjamil](https://github.com/hmzainjamil) |
| `tcc watch` monitors engine task queue in real-time — see active/pending/done | [hmzainjamil](https://github.com/hmzainjamil) |

<a id="tips-pc"></a>
■ **Paperclip Integration (4)**

| Tip | Source |
|---|---|
| Paperclip must be running: `cd ~/installed-repos/paperclip && pnpm dev` | [Paperclip AI](https://github.com/paperclipai) |
| Company ID `c5066522-bacc-4a28-b700-6590cbe366ec` scopes all API calls to DigiMinds | [hmzainjamil](https://github.com/hmzainjamil) |
| Engine falls back to `llm-burst` if Paperclip API returns 404 | [hmzainjamil](https://github.com/hmzainjamil) |
| Set engine goals via Paperclip dashboard → engine picks up on next run cycle | [Paperclip AI](https://github.com/paperclipai) |

---

## ☠️ STARTUPS / BUSINESSES <a id="startups"></a>

| Feature | Replaced |
|---|---|
| **Autonomous engine loop** | [AutoGPT](https://autogpt.net), [AgentGPT](https://agentgpt.reworkd.ai), [BabyAGI](https://github.com/yoheinakajima/babyagi) |
| **Paperclip company OS** | [Notion AI](https://notion.so), [Monday.com](https://monday.com), [Asana](https://asana.com) |
| **Zero-cost Tier 0 execution** | [CrewAI Cloud](https://crewai.com), [LangSmith](https://smith.langchain.com) |
| **MAE swarm synthesis** | [LangGraph](https://langgraph.com), [AutoGen](https://github.com/microsoft/autogen) |

---

## Star History <a id="star"></a>

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/hmz-paperclip-lead-engine&type=Date)](https://star-history.com/#hmzainjamil/hmz-paperclip-lead-engine&Date)
