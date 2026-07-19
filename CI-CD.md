# CI/CD

## GitHub Actions

### ci.yml (push trigger)
- Runs on every push to main
- 66 portable T0 invariants (Linux, `--ci-portable` flag)
- Unit tests (62 tests, 9 files)
- CHANGELOG validator
- Status: GREEN

### daily-full.yml (scheduled)
- Runs daily at 06:00 UTC
- 13 steps including full invariant suite
- Status: GREEN

## Local Verification

### pre-push-gate.py
- Runs before every `git push`
- 28 static T0 invariants
- py_compile on changed .py files
- Unit tests
- Blocks push if FAIL

### twin_pulse.py
- 102 T0 invariants (all PASS)
- Run manually: `python meta/twin_pulse.py`
- Run in CI: `python meta/twin_pulse.py --ci-portable`

## Cost Circuit-Breaker

- `cost_guard.py` blocks automated LLM spawns at HEAVY threshold
- Interactive sessions NOT blocked
- Toast notification on threshold cross
- Twin pulse invariant #7

## Wiki Sync Flow

```
Task completed
  → PM dispatches Tech-writer
  → Tech-writer reads wiki/ folder (in-repo specs)
  → Tech-writer writes human-readable summary
  → Tech-writer pushes to GitHub Wiki
  → Wiki up to date
```
