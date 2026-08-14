# Windows Quickstart (PowerShell)

This doc contains **Windows-specific** command syntax for running **AI Agent Control Plane** with the **Docker sandbox**.

For main install options and overall architecture, see [README.md](./README.md).

---

## Quickstart with Docker Sandbox (Windows)

**Prerequisites**:
- Docker Desktop for Windows
- A host directory for `PROJECTS_PATH` containing your target coding projects.

```powershell
npm install -g @nadeemahmad3/ai-agent-control-plane
agent-control-plane

# Docker sandbox execution (Optional):
$env:PROJECTS_PATH = Join-Path $HOME "projects"
New-Item -ItemType Directory -Force -Path $env:PROJECTS_PATH, (Join-Path $env:USERPROFILE ".agent-control-plane") | Out-Null

docker run -it --rm `
  -p 8000:8000 `
  -v "$($env:USERPROFILE)\.agent-control-plane:/home/openhands/.openhands" `
  -v "$($env:PROJECTS_PATH):/projects" `
  ghcr.io/openhands/agent-canvas:latest
```

Open [http://localhost:8000](http://localhost:8000) in your browser.
