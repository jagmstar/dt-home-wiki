# System Status

## Current State (as of 2026-07-20)

| Component | Status | Details |
|-----------|--------|---------|
| Clark (LCD) | OK | Letta Code Desktop, letta/auto |
| Heartbeat | OK | 71 steps, all alive |
| T0 Invariants | 102 PASS | 0 FAIL, 0 needs_decision |
| CI/CD | GREEN | ci.yml + daily-full.yml |
| Unit Tests | 62 PASS | 9 test files |
| Voice | OK | Piper TTS, wake word workaround |
| Superman | OK | Ollama qwen2.5:3b, port 8283 |
| PostgreSQL | OK | 1696 archival_passages |
| Google Sync | OK | OAuth complete, every 15 min |
| Telegram | BLOCKED | Waiting for api_id/api_hash |
| M365 | BLOCKED | Mac-only, token expired |

## Cost

| Metric | Value |
|--------|-------|
| Daily cost (token-equiv) | $414.20 baseline |
| Cost circuit-breaker | Active (blocks at HEAVY) |
| Letta Code | Free tier ($20 balance) |
| 0-LLM changes preferred | Yes |

## Known Issues

1. **Wake word mismatch** — Model detects "hey_jarvis", Roman says "твін"/"кларк"
2. **M365 stale** — Token expired, needs login on Mac
3. **Telegram** — Waiting for Roman's api_id/api_hash from my.telegram.org
4. **private repo wiki** — GitHub Free doesn't allow wikis on private repos
