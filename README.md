<a name="readme-top"></a>

<div align="center">
  <h1 align="center" style="border-bottom: none">🤖 AI Agent Control Plane</h1>
  <p align="center">
    <strong>The self-hosted developer control center for coding agents and automations.</strong>
  </p>
  <p align="center">
    Run autonomous AI agents (Claude Code, Codex, Gemini, Open-Source LLMs) across local, remote, and Docker backends.
  </p>
</div>

<div align="center">
  <a href="https://github.com/NadeemAhmad3/ai-agent-control-plane/actions"><img src="https://img.shields.io/badge/status-production-blue?style=for-the-badge" alt="Project status production"></a>
  <a href="https://github.com/NadeemAhmad3/ai-agent-control-plane/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="MIT License"></a>
</div>

<hr>

**AI Agent Control Plane** turns your coding agents into a self-hosted, always-on engineering team. It's an enterprise developer control center for starting agentic sessions and automating everyday engineering tasks — like auto-generating pull requests, running code reviews, and resolving GitHub issues automatically.

It runs locally on your machine by default, but can connect to multiple agent backends (running agents in Docker containers, on isolated VMs, or within your company infrastructure).

| Feature | Description |
| :--- | :--- |
| **Self-Host Your Way** | Run agents locally, in Docker containers, or on remote VMs with strict security isolation. |
| **Multi-Backend Orchestration** | Switch between local, remote, and cloud agents seamlessly from a unified control dashboard. |
| **Event-Driven Automations** | Automate workflows that integrate with GitHub, Slack, Linear, and Notion. |
| **Bring Your Own LLM** | Compatible with Anthropic Claude, OpenAI GPT-4o, Google Gemini, and local LLMs via Ollama/vLLM. |
| **Agent-Client Protocol (ACP)** | Built on standardized ACP architecture for extensible agent backends. |

---

## ⚡ Quickstart

### Installation via NPM

```bash
npm install -g @nadeemahmad3/ai-agent-control-plane
agent-control-plane
```

### Running with Docker Sandbox (Recommended)

**Prerequisites**: Docker Desktop (macOS/Windows) or Docker Engine (Linux).

```bash
export PROJECTS_PATH="$HOME/projects"
mkdir -p "$PROJECTS_PATH" "$HOME/.agent-control-plane"

docker run -it --rm \
  -p 8000:8000 \
  -v "$HOME/.agent-control-plane:/home/openhands/.openhands" \
  -v "${PROJECTS_PATH}:/projects" \
  ghcr.io/openhands/agent-canvas:latest
```

---

## 🏛️ Architecture Overview

```text
               ┌─────────────────────────────────────────┐
               │    Developer Control Center (React UI)  │
               └────────────────────┬────────────────────┘
                                    │ WebSocket / ACP
                                    ▼
               ┌─────────────────────────────────────────┐
               │   AI Agent Control Server Engine        │
               └────────────────────┬────────────────────┘
                                    │
               ┌────────────────────┴────────────────────┐
               ▼                                         ▼
   Local Process Boundary                    Docker Container Sandbox
  (Fast Bare-Metal Execution)               (Isolated OS & Filesystem)
```

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for details.
