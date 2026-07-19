# Digital Twin (Clark) — Project Wiki

## Overview

**Product:** Digital twin brain — Clark
**Repo:** [jagmstar/dt-home-personal](https://github.com/jagmstar/dt-home-personal) (private)
**Wiki:** This public repo (dt-home-personal is private on GitHub Free, wikis not available)
**Author:** Roman Krepych
**Framework:** [AI-SDLC v1.4](https://github.com/jagmstar/ai-sdlc)

---

## Quick Links

- [Architecture](Architecture)
- [System Status](System-Status)
- [Roles Used](Roles-Used)
- [CI/CD](CI-CD)

## What Is This?

Clark is a digital twin built on Letta Code. The twin brain lives at `F:\dt-home\` on Roman's Windows laptop. It uses a hybrid architecture: 80-90% Python scripts (0-LLM), with LLM calls only for high-level reasoning.

### Key Numbers
- 102 T0 invariants (all PASS)
- 71 heartbeat steps
- 10 scheduled tasks
- 4 Claude Code hooks (consolidated)
- 177 .py files in meta/ (125 active)
- CI: GitHub Actions GREEN

### Architecture
- **Clark (Letta Code Desktop):** Primary twin, full memory (MemFS), personality, partnership
- **Superman (Ollama qwen2.5:3b):** Memory backend service, NOT a separate twin
- **Voice pipeline:** Ctrl+Alt+S → Whisper → Clark → Piper TTS
- **Heartbeat:** 71 steps running every 2 minutes, 0-LLM

## Why a Separate Wiki Repo?

`dt-home-personal` is a private repo (contains personal data). GitHub Free tier doesn't allow wikis on private repos. This public repo serves as the wiki host. The actual code and issues stay private.
