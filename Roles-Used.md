# Roles Used in Twin Project

## AI-SDLC Roles for dt-home-personal

| Role | When Used |
|------|-----------|
| senior-technical-pm | Every issue — orchestrates flow |
| senior-software-architect | Architecture decisions, ADRs |
| senior-fullstack-dev | Code implementation |
| senior-qa-engineer | Test plans, quality gates, T0 invariants |
| senior-code-reviewer | Code review before merge |
| senior-researcher | Literature review, technology evaluation |
| senior-ai-engineer | LLM/AI system design, RAG, prompt engineering |
| senior-optimization-engineer | Cost reduction, performance profiling |
| memory-architect | Memory system design, tiering, retrieval |
| senior-tech-writer | Documentation, wiki updates |
| senior-devops-engineer | CI/CD pipelines, environments, deployment |

## Role Diagram

```
                    ┌─────────────────────┐
                    │  Roman (triggers)   │
                    │  "issue #N, починай" │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │  senior-technical-pm │
                    │  (PM orchestrator)   │
                    └──────────┬──────────┘
                               │
            ┌──────────────────┼──────────────────┐
            │                  │                  │
   ┌────────▼───────┐ ┌───────▼────────┐ ┌──────▼─────────┐
   │  Architect     │ │  Researcher    │ │  DevOps        │
   │  (spec, ADR)   │ │  (investigate) │ │  (CI/CD, env)  │
   └────────┬───────┘ └───────┬────────┘ └──────┬─────────┘
            │                  │                  │
   ┌────────▼───────┐ ┌───────▼────────┐ ┌──────▼─────────┐
   │  Dev           │ │  AI-Engineer   │ │  Memory        │
   │  (implement)   │ │  (LLM design)  │ │  Architect     │
   └────────┬───────┘ └────────────────┘ └────────────────┘
            │
   ┌────────▼───────┐ ┌───────▼────────┐ ┌──────▼─────────┐
   │  QA            │ │  Code Reviewer │ │  Tech Writer   │
   │  (test, verify)│ │  (review)      │ │  (wiki, docs)  │
   └────────────────┘ └────────────────┘ └────────────────┘
            │
   ┌────────▼───────┐
   │  Optimization  │
   │  Engineer      │
   │  (cost, perf)  │
   └────────────────┘
```

## When DevOps is Called

- **New project setup** — CI pipeline, Docker environment, deployment
- **CI/CD issues** — Pipeline failures, flaky tests, caching
- **Environment provisioning** — Free-tier setup, secrets, protection rules
- **Deployment** — Staging, production, rollback procedures
- **Wiki initialization** — Enabling wiki, pushing initial pages

## Wiki Sync Responsibility

After each completed task:
1. PM dispatches Tech-writer
2. Tech-writer reads in-repo `wiki/` folder (specs, ADRs)
3. Tech-writer writes human-readable summary
4. Tech-writer pushes to GitHub Wiki (or public wiki repo for private repos)
5. Wiki stays up to date
