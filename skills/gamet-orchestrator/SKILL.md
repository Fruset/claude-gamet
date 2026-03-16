---
name: gamet-orchestrator
description: "Full feature development pipeline — chains Impact → Design → Architecture → AI Prep → Plan → Build → GAMET Review → Ship. Includes improvement loop with specialist agent dispatch, blocker tracking, regression guard, and cleanup. Run with '/gamet-orchestrator' for complete persona-driven development."
user-invocable: true
---

# Feature Development Orchestrator

Chains the 8-step persona-driven pipeline with improvement loop.

## Pipeline

```
Step 1: Impact     → 01-impact-brief.md     (gamet-impact + product-analyst)
Step 2: Design     → 02-design-brief.md     (ux-researcher + frontend-architect)
Step 3: Architect  → 03-architecture.md     (backend-architect + security-reviewer)
Step 4: AI Prep    → 04-ai-readiness.md     (gamet-ai-prep)
Step 5: Plan       → 05-plan.md            (writing-plans skill)
Step 6: Build      → code + tests           (code-implementer → code-reviewer)
Step 7: Review     → 07-gamet-review.md     (gamet-review-panel)
Step 7.5: Fix Plan → 07-fix-plan.md        (specialist dispatch per issue type)
Step 7.6: Fix      → code changes           (with blocker check + regression guard + cleanup)
Step 7.7: Re-review → loop until ≥ A        (max 3 iterations)
Step 8: Ship       → commit, push, learn    (update learning log + progress)
```

## Specialist Dispatch (Step 7.5)

| Issue Type | Agent | Skills |
|---|---|---|
| Mobile UX | frontend-architect | UI/UX skill |
| Data scoping | backend-architect + security-reviewer | Security + database skills |
| Language | ux-writer | i18n skill |
| Domain logic | product-analyst + industry-researcher | Domain + research skills |
| Performance | backend-architect | Framework skill |
| Accessibility | frontend-architect | UI/UX skill |
| Component design | frontend-architect | UI/UX skill |

## Safety Protocols (Step 7.6)

1. **Blocker check** — dependency ordering, external deps
2. **Regression guard** — typecheck + tests before AND after
3. **Cleanup** — dead code, console.logs, temp files, duplicates

## Modes

- **Full** (`/gamet-orchestrator "feature"`) — all 8 steps
- **Quick** (`/gamet-orchestrator --quick "bugfix"`) — skip 1,2,4
- **Review only** (`/gamet-panel`) — step 7 only
- **Impact only** (`/gamet-impact "idea"`) — step 1 only

## Checkpoint Integration

After each step, invoke `gamet-checkpoint` to save state.
If context > 70%, recommend compact before continuing.
