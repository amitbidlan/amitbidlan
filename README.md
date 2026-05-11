<div align="center">
  <h1>Hi, I'm Amit Bidlan 👋</h1>
  <p><strong>Full-stack engineer · founder · open-source-first</strong> · based in Japan 🇯🇵</p>
  <p>Building the operational platform for LLM agents in production — observe, govern, defend, operate.</p>
</div>

---

## 🔭 Currently building

<p align="center">
  <a href="https://github.com/amitbidlan/zistica-lumin">
    <img src="https://raw.githubusercontent.com/amitbidlan/zistica-lumin/main/assets/lumin-banner.svg" alt="Lumin — local-first observability + security for LLM agents" width="100%" />
  </a>
</p>

<p align="center">
  <a href="https://github.com/amitbidlan/zistica-lumin/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-Apache_2.0-blue.svg" alt="Apache 2.0" />
  </a>
  <a href="https://github.com/amitbidlan/zistica-lumin/stargazers">
    <img src="https://img.shields.io/github/stars/amitbidlan/zistica-lumin?style=social" alt="GitHub stars" />
  </a>
  <a href="https://github.com/amitbidlan/zistica-lumin/commits/main">
    <img src="https://img.shields.io/github/last-commit/amitbidlan/zistica-lumin?labelColor=%20%2332b583&color=%20%2312b76a" alt="Last commit" />
  </a>
  <a href="https://hub.docker.com/r/zistica/lumin">
    <img src="https://img.shields.io/badge/docker-zistica%2Flumin-2496ed?logo=docker" alt="Docker" />
  </a>
  <a href="https://www.npmjs.com/package/@lumin-io/sdk">
    <img src="https://img.shields.io/npm/v/@lumin-io/sdk?label=npm&logo=npm&color=cb3837" alt="npm" />
  </a>
  <a href="https://youtu.be/hgTntZniuv4">
    <img src="https://img.shields.io/badge/▶_demo-52s-ff0000?logo=youtube&logoColor=white" alt="52s demo" />
  </a>
</p>

<p align="center">
  <a href="https://youtu.be/hgTntZniuv4">
    <img src="https://raw.githubusercontent.com/amitbidlan/zistica-lumin/main/assets/demo.gif" alt="Lumin demo — click to watch the 52s walkthrough on YouTube" width="100%" />
  </a>
</p>

<p align="center">
  <sub>▶ <a href="https://youtu.be/hgTntZniuv4">Watch the 52-second walkthrough on YouTube</a></sub>
</p>

### Why Lumin

Most LLM tooling picks one corner of the agent operations problem. **Observability** stacks (Langfuse, LangSmith, Helicone, Arize) tell you what your agent did after it did it. **Guardrail classifiers** (Lakera, NemoGuardrails) score single prompts in isolation. **Gateways** (LiteLLM, TensorZero) route traffic. **Static scanners** (Agentic Radar) audit code.

**Lumin covers all four corners in one self-hosted Docker container.** Four pillars, every major framework.

### 🏛️ Four pillars

#### 📊 Observe
Full-trace recording for every LLM call, tool invocation, retrieval, embedding, cost, eval. Multi-turn sessions. Real-time WebSocket dashboard with span timelines. Cost + token attribution across OpenAI, Anthropic, Ollama. Drop-in alternative to Langfuse / LangSmith — but local-only.

#### 📜 Govern
Policy engine with a typed DSL (`before_proxy_call` / `after_proxy_call` lifecycle hooks, priority, severity, conditions). Shadow / enforce modes — every rule starts as `shadow`, promote after reviewing the timeline. Versioning + rollback + audit. **Auto-suggester** mines patterns from your real traces; **replay** tests draft policies against historical traces; **drift detection** alerts on distribution shifts. Human approvals queue + decisions audit.

#### 🛡️ Defend — OWASP LLM Top 10 at runtime
8 detection methods layered: Presidio NER, Prompt Guard 2 (22M-param classifier), Llama Guard 4 (14 MLCommons hazards), LLM-judge, embedding similarity, indirect-prompt-injection detection, locally-trainable classifier, regex packs. **12 starter policy packs** ship: OWASP LLM Top 10, OWASP Agentic 2025, GDPR, HIPAA, PCI-DSS, cost guards, cross-session isolation, framework-specific. **Attack generator** for adversarial CI testing. PII vault. Tenant-isolation firewall for multi-tenant bots (5 structural layers).

| OWASP | Lumin protection |
|---|---|
| **LLM01 — Prompt Injection** | Prompt Guard 2 + pattern + LLM-judge on every input |
| **LLM02 / LLM06 — Sensitive Info Disclosure** | Presidio NER scrubs PII / names / orgs / IDs / emails / SSNs / credit cards from prompts |
| **LLM03 — Supply-Chain** | Every tool call audited; tool allowlist + signed plugin manifests |
| **LLM05 — Insecure Output** | Output-filter chain (Llama Guard 4 + regex + structural) before responses leave the agent |
| **LLM08 — Excessive Agency** | Deny-by-default for shells (`exec`, `bash`, `python`) and network egress (`web_fetch`, `curl`). Per-user file sandbox |
| **LLM09 — Overreliance** | Policy engine + human approval queue |
| **LLM10 — Model Theft** | Tenant-isolation firewall: conversation-history reset, structural blocking of cross-session leaks |

#### 🛠️ Operate
Webhook fanout to PagerDuty / Slack / SIEM. Backups + retention with one-click restore. Panic disable kill-switch. Prometheus-shape metrics + liveness / readiness. Resilient by design — a Lumin outage MUST never affect the agent. Local-first: single Docker, DuckDB + SQLite, no cloud dependency.

### How it compares

| | **Lumin** | Langfuse | Lakera | NemoGuard |
|---|---|---|---|---|
| Full trace recording | ✅ | ✅ | ❌ | ❌ |
| Cost + token attribution | ✅ | ✅ | ❌ | ❌ |
| Evals + scoring | ✅ | ✅ | ❌ | ❌ |
| Prompt-injection detection | ✅ | ❌ | ✅ | ✅ |
| PII redaction (Presidio NER) | ✅ | ❌ | ✅ classifier | ✅ classifier |
| Excessive-agency guard (deny exec / fetch) | ✅ | ❌ | ❌ | ❌ |
| Per-user file sandbox | ✅ | ❌ | ❌ | ❌ |
| Conversation history isolation | ✅ | ❌ | ❌ | ❌ |
| Policy engine + human approval | ✅ | ❌ | ❌ | ⚠️ partial |
| Self-hosted single Docker | ✅ | ⚠️ stack | ❌ SaaS | ❌ NIM endpoint |
| Open source | ✅ Apache-2.0 | ✅ MIT | ❌ | ✅ Apache-2.0 |

### Ships as

- 🐳 **Docker** — `docker run -p 3000:3000 -p 8000:8000 zistica/lumin:0.7.0`
- 📦 **npm** — `@lumin-io/sdk`, `@lumin-io/openclaw-diagnostics`, `@lumin-io/mastra`, `@lumin-io/voltagent`
- 🐍 **Python SDK** — `pip install -e .` (`@lumin.trace` decorator + framework integrations)
- 🔌 **16 framework integrations** — Python SDK, TypeScript SDK, LangChain, LangGraph, LlamaIndex, CrewAI, AutoGen, LiteLLM, OpenAI Agents, Pydantic AI, Anthropic (extended-thinking), OpenClaw (OTel + diagnostics plugin), Mastra, VoltAgent, OpenAI-compat HTTP proxy, OTLP receiver

<div align="center">

**[⭐ Star the repo →](https://github.com/amitbidlan/zistica-lumin)** · **[▶ Watch the demo](https://youtu.be/hgTntZniuv4)** · **[📦 Pull from Docker Hub](https://hub.docker.com/r/zistica/lumin)**

</div>

---

## 🛠 Tech I work with

<p>
  <img src="https://img.shields.io/badge/-Python-3776AB?style=flat&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/-TypeScript-3178C6?style=flat&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/-FastAPI-009688?style=flat&logo=fastapi&logoColor=white" alt="FastAPI" />
  <img src="https://img.shields.io/badge/-Next.js-000000?style=flat&logo=next.js&logoColor=white" alt="Next.js" />
  <img src="https://img.shields.io/badge/-React-61DAFB?style=flat&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/-Node.js-339933?style=flat&logo=node.js&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/-Docker-2496ED?style=flat&logo=docker&logoColor=white" alt="Docker" />
  <img src="https://img.shields.io/badge/-DuckDB-FFF000?style=flat&logo=duckdb&logoColor=black" alt="DuckDB" />
  <img src="https://img.shields.io/badge/-Google_Cloud-4285F4?style=flat&logo=googlecloud&logoColor=white" alt="GCP" />
  <img src="https://img.shields.io/badge/-PostgreSQL-336791?style=flat&logo=postgresql&logoColor=white" alt="Postgres" />
  <img src="https://img.shields.io/badge/-OpenTelemetry-FFB000?style=flat&logo=opentelemetry&logoColor=white" alt="OpenTelemetry" />
</p>

---

## 📈 GitHub

<p align="center">
  <a href="https://github.com/amitbidlan">
    <img src="https://github-readme-stats.vercel.app/api?username=amitbidlan&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true" alt="GitHub stats" />
  </a>
  <a href="https://github.com/amitbidlan">
    <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=amitbidlan&layout=compact&theme=tokyonight&hide_border=true" alt="Top languages" />
  </a>
</p>

---

## 📫 Connect

- 🌐 [zistica.com](https://zistica.com)
- 📧 [support@zistica.com](mailto:support@zistica.com)
- 💬 [GitHub Discussions](https://github.com/amitbidlan/zistica-lumin/discussions)
- ▶️ [YouTube — Lumin demo](https://youtu.be/hgTntZniuv4)

<div align="center">
  <sub>"Start where developers are. End where enterprises need you."</sub>
</div>
