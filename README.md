<div align="center">
  <h1>Hi, I'm Amit Bidlan 👋</h1>
  <p><strong>Full-stack engineer · founder · open-source-first</strong> · based in Japan 🇯🇵</p>
  <p>Building tools that make AI agents safe to run in production — observability, security, audit.</p>
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

Most LLM platforms split into two camps: **observability** tools (Langfuse, LangSmith, Helicone, Arize) tell you what your agent did after it did it; **security** tools (Lakera, NemoGuardrails) classify single prompts. Neither, alone, is enough to ship an AI agent into production.

**Lumin is both, in one self-hosted Docker container.**

### What it gives you

#### 📊 Full-trace observability
Every LLM call, tool invocation, retrieval step, embedding, cost, and eval — recorded and replayable in a Next.js dashboard with a span timeline. Drop-in alternative to Langfuse / LangSmith with local-only data.

#### 🛡️ OWASP LLM Top 10 guardrails — at runtime
| OWASP | Lumin protection |
|---|---|
| **LLM01 — Prompt Injection** | Pattern + LLM-judge prompt-injection detection on every input |
| **LLM02 / LLM06 — Sensitive Info Disclosure** | Microsoft Presidio NER scrubs PII, names, orgs, IDs, emails, phones, SSNs, credit cards, passports from prompts before they reach the model |
| **LLM03 — Supply-Chain** | Every tool call audited; tool allowlist + signed manifests |
| **LLM05 — Insecure Output Handling** | Output-filter chain (regex + structural) before responses leave the agent |
| **LLM08 — Excessive Agency** | Deny-by-default for shells (`exec`, `bash`, `python`, …) and network egress (`web_fetch`, `curl`, `http_*`). Per-user file sandbox |
| **LLM09 — Overreliance** | Policy engine with declarative rules + human approval queue |
| **LLM10 — Model Theft** | Tenant-isolation firewall: conversation-history reset on sender switch, structural blocking of cross-session leaks |

#### 🔐 Policy engine + approvals
Declarative rules for what your agent can read / write / call. Anything outside the rules goes to a human approval queue in the dashboard.

#### 🚨 Audit trail + alerts
Every block, redaction, policy hit recorded in `/violations`. Webhooks fire to PagerDuty / Slack / SIEM.

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
- 🔌 **Drop-in integrations** — LangChain, CrewAI, LlamaIndex, Anthropic (extended-thinking), OpenClaw, Mastra, VoltAgent, OTel/OTLP

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
