<a name="readme-top"></a>

<div align="center">
  <h1 align="center" style="border-bottom: none">🤖 AI Agent Control Plane</h1>
  <p align="center">
    <strong>Enterprise Self-Hosted Autonomous AI Agent & Automation Platform</strong>
  </p>
  <p align="center">
    Orchestrate, observe , and automate autonomous AI coding agents (Claude, Codex, Gemini, DeepSeek) across local, Docker, and private cloud sandboxes.
  </p>
</div>

<div align="center">
  <a href="https://github.com/NadeemAhmad3/ai-agent-control-plane"><img src="https://img.shields.io/badge/Author-Nadeem%20Ahmad-blue?style=for-the-badge&logo=github" alt="Author"></a>
  <a href="mailto:engrnadeem26@gmail.com"><img src="https://img.shields.io/badge/Email-engrnadeem26%40gmail.com-red?style=for-the-badge&logo=gmail" alt="Email"></a>
  <a href="https://github.com/NadeemAhmad3/ai-agent-control-plane/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License MIT"></a>
  <a href="https://github.com/NadeemAhmad3/ai-agent-control-plane/actions"><img src="https://img.shields.io/badge/Status-Production%20Ready-brightgreen?style=for-the-badge" alt="Status"></a>
</div>

<hr>

## 📌 Executive Overview

**AI Agent Control Plane** is a production-grade, self-hosted developer control center engineered to turn AI models into an always-on autonomous software engineering team. 

Unlike closed commercial tools that upload source code to third-party servers, **AI Agent Control Plane** runs locally or on your private infrastructure. It equips autonomous agents with structured execution tools (bash shell, interactive file editing, headless browser testing, and git operations) operating inside isolated Docker sandboxes.

```text
               ┌────────────────────────────────────────────────────────┐
               │    Developer Dashboard (React UI & Control Center)     │
               └───────────────────────────┬────────────────────────────┘
                                           │ WebSocket / ACP Protocol
                                           ▼
               ┌────────────────────────────────────────────────────────┐
               │    AI Agent Control Server Engine                      │
               └───────────────────────────┬────────────────────────────┘
                                           │
         ┌─────────────────────────────────┼─────────────────────────────────┐
         ▼                                 ▼                                 ▼
┌──────────────────┐             ┌──────────────────┐             ┌──────────────────┐
│  Agent Execution │             │ Microsecond      │             │ System Safety    │
│  Sandbox (Docker)│             │ Telemetry Tracer │             │ Guards & Circuit │
└──────────────────┘             └──────────────────┘             └──────────────────┘
```

---

## 🔥 Key System Capabilities

### 1. 🤖 Autonomous Agentic Execution Loop
Implements the continuous **`Observe ➔ Reason ➔ Select Tool ➔ Execute ➔ Evaluate`** control loop. Agents autonomous analyze bug reports, inspect repositories, write code fixes, execute test suites (`pytest`, `vitest`, `npm test`), and commit verified changes.

### 2. 🐳 Isolated Docker Sandboxing
Prevents unsafe shell commands (`rm -rf`, arbitrary package installations) from damaging your host operating system. All bash execution, file mutations, and dependencies run inside lightweight, isolated Docker containers (`ghcr.io/openhands/agent-canvas`).

### 3. ⏱️ Microsecond Telemetry & Token Tracing
Monitors step-by-step agent telemetry in real time:
- Step duration and tool execution latencies (milliseconds).
- Prompt and completion token consumption per action.
- Dollar cost calculations per task ($/task).

### 4. 🛡️ Fault Tolerance & Safety Guards
- **Decision Loop Detection**: Monitors action signatures and aborts execution if identical tool calls repeat $\ge 3$ times.
- **Step Budgeting**: Enforces configurable execution ceilings (`MAX_STEPS=10`).
- **Distributed Circuit Breaker**: State machine (`CLOSED -> OPEN -> HALF-OPEN`) that isolates failing external API dependencies.

### 5. ⚡ Event-Driven GitHub & Slack Automations
Listens for webhooks and cron schedules to automate everyday engineering tasks:
- **Auto-Fix GitHub Issues**: Listens for opened issues, reproduces bugs, writes fixes, and opens Pull Requests.
- **Automated PR Reviews**: Audits diffs against code formatting and security rules.
- **Incident Response**: Monitors Slack alerts, diagnoses stack traces, and reports root causes.

---

## 🌐 Supported AI Models ("Bring Your Own LLM")

AI Agent Control Plane supports multi-model LLM backends via LiteLLM and OpenAI API adapters:

| Provider | Model Family | Recommended Use Case |
| :--- | :--- | :--- |
| **Anthropic** | Claude 3.5 Sonnet / Claude Code | Primary choice for complex code refactoring and agentic tasks. |
| **OpenAI** | GPT-4o / Codex | Fast multi-modal reasoning and structured JSON extraction. |
| **Google** | Gemini 1.5 Pro / Flash | Long-context repo analysis and documentation synthesis. |
| **Local LLMs** | DeepSeek-R1 / Qwen 2.5 Coder / Llama 3 | Private offline execution via Ollama or vLLM. |

---

## 📂 Repository Architecture

```text
ai-agent-control-plane/
├── README.md                      # Primary platform documentation
├── README.windows.md              # Windows PowerShell quickstart guide
├── package.json                   # Package manifest (@nadeemahmad3/ai-agent-control-plane)
├── requirements.txt               # Python core dependencies
├── bin/
│   └── agent-control-plane.mjs    # Executable CLI binary entry point
├── control_plane/
│   ├── schemas/                   # Pydantic state & execution contracts
│   ├── core/                      # Autonomous agent execution engine
│   ├── sandbox/                   # Isolated Docker / process runner
│   ├── monitoring/                # Microsecond telemetry tracer
│   ├── guards/                    # Loop detector & circuit breakers
│   ├── api/                       # FastAPI control plane web server
│   └── workflows/                 # Event-driven GitHub automation runners
├── src/                           # Frontend UI dashboard & agent server tree
├── docker/                        # Docker sandbox container configurations
├── docs/                          # Architecture & self-hosting guides
└── tests/                         # Pytest unit & E2E integration test suite
```

---

## ⚡ Quickstart Guide

### Option 1: Global NPM CLI Installation

```bash
# Install globally
npm install -g @nadeemahmad3/ai-agent-control-plane

# Launch Control Center
agent-control-plane
```

### Option 2: Docker Sandbox Deployment (Recommended)

**Prerequisites**: Docker Desktop (Windows/macOS) or Docker Engine (Linux).

#### Linux / macOS:
```bash
export PROJECTS_PATH="$HOME/projects"
mkdir -p "$PROJECTS_PATH" "$HOME/.agent-control-plane"

docker run -it --rm \
  -p 8000:8000 \
  -v "$HOME/.agent-control-plane:/home/openhands/.openhands" \
  -v "${PROJECTS_PATH}:/projects" \
  ghcr.io/openhands/agent-canvas:latest
```

#### Windows (PowerShell):
```powershell
$env:PROJECTS_PATH = Join-Path $HOME "projects"
New-Item -ItemType Directory -Force -Path $env:PROJECTS_PATH, (Join-Path $env:USERPROFILE ".agent-control-plane") | Out-Null

docker run -it --rm `
  -p 8000:8000 `
  -v "$($env:USERPROFILE)\.agent-control-plane:/home/openhands/.openhands" `
  -v "$($env:PROJECTS_PATH):/projects" `
  ghcr.io/openhands/agent-canvas:latest
```

Open **`http://localhost:8000`** in your browser to access the control dashboard.

---

## 👤 Author & Maintainer Information

* **Author**: **Nadeem Ahmad**
* **GitHub**: [@NadeemAhmad3](https://github.com/NadeemAhmad3)
* **Email**: [engrnadeem26@gmail.com](mailto:engrnadeem26@gmail.com)
* **Repository**: [https://github.com/NadeemAhmad3/ai-agent-control-plane](https://github.com/NadeemAhmad3/ai-agent-control-plane)

---

## 📄 License

Distributed under the MIT License. See [`LICENSE`](./LICENSE) for full details.
