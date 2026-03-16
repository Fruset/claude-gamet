---
name: gamet-impact
description: "Persona impact analysis for new features — identifies affected users, maps workflow changes, predicts adoption risk, produces an Impact Brief. Triggers on feasibility questions or when explicitly invoked. For building features, prefer gamet-orchestrator which runs impact as Step 1."
---

# Feature Impact Analysis

Before writing code, understand WHO is affected and HOW their day changes.

## Process

1. **Understand** — What problem? Who asked? (AskUserQuestion if unclear)
2. **Identify personas** — Which roles affected? (AskUserQuestion multiSelect)
3. **Analyze per persona** — Current vs future state, adoption risk, emotional impact, day change
4. **Journey threads** — Which handoff points between roles are affected?
5. **GAMET pre-score** — G/A/M/E/T per persona
6. **Check past** — Search docs/features/ for similar features. Read learning log.
7. **Architecture** — New entities? RBAC? Multi-device? Offline?
8. **AI readiness** — Can this data drive ML later?
9. **Produce Impact Brief** — Save to docs/features/[name]/01-impact-brief.md
10. **Update learning log** — Add new insights
11. **Recommend next step** — Simple → orchestrator. Complex → brainstorm first.

## Impact Brief Template

See [references/impact-brief-template.md](references/impact-brief-template.md)

## Key Principles

1. Start with people, not technology
2. Adoption is existential — if ANY party stops using it, the chain breaks
3. Predict, don't just describe — "40% will abandon because..."
4. Learn from the past — always check the learning log
