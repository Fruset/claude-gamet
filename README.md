# GAMET — Persona-Driven AI Development System

GAMET transforms how you build software with Claude Code. Instead of jumping straight to code, every feature starts with **people** — who is affected, how their day changes, and what makes them choose to use your product.

## What is GAMET?

GAMET is an evaluation framework with 5 criteria:

- **G** — Guidning: Does the system lead the user to the right action?
- **A** — Adoption: Would this role CHOOSE to use this voluntarily?
- **M** — Mervärde: What value does this provide that doesn't exist elsewhere?
- **E** — Enkelhet: Can a first-timer understand this in 2 minutes?
- **T** — Trygghet: Does the user trust the system?

## What You Get

After running `/gamet-init`, your project gets:

- **GAMET Panel** — 10-20 expert personas who review every feature
- **Feature Pipeline** — 8-step workflow: Impact → Design → Architecture → AI Prep → Plan → Build → Review → Ship
- **Learning Loop** — System gets smarter with every feature you build
- **Industry Research** — Knowledge base that grows, with epistemic discipline (verified vs assumed)
- **Language Guidelines** — Per-persona language levels, i18n preparation
- **Session Checkpoints** — Never lose progress, even across context compacts

## Installation

### Option 1: Copy skills into your project

```bash
# Clone this repo
git clone https://github.com/YOUR_USERNAME/claude-gamet.git

# Copy skills into your project
cp -r claude-gamet/skills/* your-project/.claude/skills/

# Run the init
# Open Claude Code in your project and type:
/gamet-init
```

### Option 2: Symlink (for development)

```bash
# Symlink so updates to claude-gamet apply to all projects
ln -s /path/to/claude-gamet/skills/gamet-init your-project/.claude/skills/gamet-init
ln -s /path/to/claude-gamet/skills/gamet-panel your-project/.claude/skills/gamet-panel
# ... repeat for each skill
```

## How It Works

### 1. Initialize (`/gamet-init`)

The init skill asks you questions about your project:

- What does your system do?
- Who are the users? (roles, frequency, devices)
- What's the business model?
- What industry? What competitors?
- Any regulatory requirements?

From your answers, it generates:

- Custom personas tailored to YOUR users
- Domain knowledge for YOUR industry
- Language guidelines for YOUR market
- Pipeline configured for YOUR tech stack

### 2. Build Features (`/gamet-orchestrator`)

Every feature follows the 8-step pipeline:

```
You: "Build feature X"
    ↓
Step 1: Impact Analysis — who is affected? adoption risk?
Step 2: Design — brainstorm approaches with persona context
Step 3: Architecture — entities, APIs, security, with domain awareness
Step 4: AI Readiness — structure data for future ML
Step 5: Plan — implementation tasks annotated with affected personas
Step 6: Build — subagents with persona context, regression guard
Step 7: GAMET Review — panel evaluates, specialist fixes, re-review loop
Step 8: Ship — commit, push, update learning log
```

### 3. Learn & Improve

After each feature:
- Learning log updated with what worked and what didn't
- Next feature's impact analysis reads past learnings
- System gets measurably smarter over time

## Security

This plugin contains **NO secrets, credentials, API keys, or personal data**. It is purely instructions and templates. Safe to commit to public repos.

## Skills Reference

| Skill | Purpose |
|-------|---------|
| `gamet-init` | Interactive setup — generates all other skills configured for your project |
| `gamet-panel` | GAMET review with custom personas |
| `gamet-impact` | Persona impact analysis for new features |
| `gamet-orchestrator` | 8-step pipeline conductor |
| `gamet-discovery` | Proactive feature identification |
| `gamet-research` | Industry research with epistemic discipline |
| `gamet-i18n` | Language and localization guidelines |
| `gamet-checkpoint` | Context health management |
| `gamet-ai-prep` | AI/ML readiness evaluation |

## The GAMET Philosophy

1. **Start with people, not technology.** The first question is never "which database" — it's "whose day changes."
2. **Adoption is existential.** If any user in the chain stops using the system, it fails.
3. **Know vs believe.** Verified facts have sources. Assumptions are flagged. "I don't know" is always acceptable.
4. **Learn from every feature.** The learning log ensures you never repeat the same mistake.
5. **Predict, don't just describe.** Don't say "users are affected." Say "Kaj will abandon this flow 40% of the time because..."

## License

MIT
