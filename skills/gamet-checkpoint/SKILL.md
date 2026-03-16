---
name: gamet-checkpoint
description: "Context health management — saves session state to files, recommends compact/clear when context grows heavy. Triggers at pipeline step boundaries, or on 'checkpoint', 'save progress', 'context is getting big'."
---

# Session Checkpoint

Save state to files so context can be compacted without losing progress.

## Triggers

- After each pipeline step completes
- At ~50% context: suggest checkpoint
- At ~70% context: recommend /compact
- At ~85% context: strongly recommend /clear

## Process

1. Save state to `docs/features/[name]/.session-state.md`
2. Commit uncommitted work
3. Assess context health
4. Recommend action (continue / compact / clear)

## Resume Protocol

After compact/clear, user says "continue":

1. Read .session-state.md
2. Read PROGRESS.md
3. Read learning log
4. State: "Resuming from checkpoint. Next step: [X]"

## Cleanup

- Remove stale task lists
- Flag temp files
- Check untracked git files
