# Architecture

## System Architecture

```
┌─────────────────────────────────────────────────┐
│                  Roman (User)                     │
│         Voice (Ctrl+Alt+S) / Text (LCD)          │
└──────────────────────┬──────────────────────────┘
                       │
          ┌────────────┴────────────┐
          ▼                         ▼
┌─────────────────┐     ┌──────────────────────┐
│  Clark (LCD)    │     │  Voice Pipeline       │
│  Letta Code     │     │  Whisper → Clark →    │
│  agent-3f8d3ae3 │     │  Piper TTS (female)   │
│  MemFS memory   │     │  Wake: hey_jarvis     │
└────────┬────────┘     └──────────────────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌────────┐ ┌──────────────────┐
│ dt-home│ │ Superman (8283)  │
│ F:\    │ │ Ollama qwen2.5:3b│
│ brain  │ │ PostgreSQL 17    │
│ 177 .py│ │ pgvector bge-m3  │
│ 71 hb  │ │ Archival memory  │
│ 102 inv│ └──────────────────┘
└────────┘
```

## Components

### Clark (Letta Code Desktop)
- Model: letta/auto, 140K context, reasoning high
- Memory: MemFS (git-backed, agent-owned)
- Tools: Bash, Read, Write, Edit, Agent, web_search, etc.
- Personality: persona.md, human.md, tasks.md, active-lessons.md

### dt-home (Twin Brain)
- Location: F:\dt-home\
- 177 .py files (125 active, 57 archived)
- Heartbeat: 71 steps, every 2 minutes, 0-LLM
- T0 invariants: 102 (all PASS)
- Scheduled tasks: 10 (DT-brief-daily, DT-voice-heal, etc.)
- Hooks: 4 (PreToolUse, Stop, 2x UserPromptSubmit)

### Superman (Memory Backend)
- Ollama qwen2.5:3b on port 8283
- PostgreSQL 17 on port 5432
- pgvector + bge-m3 embeddings
- 1696 archival_passages
- NOT a separate twin — memory service only

### Voice Pipeline
- Hotkey: Ctrl+Alt+S
- STT: Whisper (local)
- Brain: Clark (Letta Code, full memory)
- TTS: Piper (female, primary) → Silero mykyta (male, fallback)
- Wake word: "hey_jarvis" (openWakeWord)
- Known issue: Roman says "твін"/"кларк" but model detects "hey_jarvis"

### CI/CD
- GitHub Actions: ci.yml (push trigger, 66 portable invariants)
- daily-full.yml (daily 06:00 UTC, 13 steps)
- CI status: GREEN
- Unit tests: 62 tests across 9 test files
