# GAMET

> **Every feature starts with people, not code.**

A persona-driven AI development system for Claude Code. GAMET doesn't just help you build software — it helps you build software that people actually want to use.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-9-blue)](skills/)
[![Agents](https://img.shields.io/badge/Agents-10-purple)](agents/)
[![Claude Code](https://img.shields.io/badge/Claude_Code-2.x-green)](https://code.claude.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/Fruset/claude-gamet/pulls)

---

## The Problem

You're building a feature. You write great code. You ship it. Then you discover:

- The field technician can't use it because the buttons are too small for his 77-year-old fingers
- The franchise owner stopped logging in because one irrelevant notification made him disable all alerts
- The contractor lost trust in the platform because he saw another company's data for 0.3 seconds during a loading state

These aren't bugs. They're **adoption failures** — and they happen because we build for ourselves, not for the people who actually use our software.

GAMET fixes this by making **humans the first input to every feature**, not the last reviewers.

---

## What is GAMET?

Five questions that every feature must answer:

|       | Criterion    | The Question                                                                                    |
| ----- | ------------ | ----------------------------------------------------------------------------------------------- |
| **G** | **Guidance** | Does the system lead the user to the right action — or do they have to figure it out?           |
| **A** | **Adoption** | Would this person CHOOSE to use this over their current method — phone calls, Excel, paper?     |
| **M** | **Meaning**  | Does this feature have genuine purpose that couldn't exist without the system?                  |
| **E** | **Ease**     | Can a first-timer understand this in 2 minutes? Can someone returning after 3 months re-orient? |
| **T** | **Trust**    | Does the user trust the data? Trust the actions? Feel safe clicking that button?                |

---

## Where It Comes From

GAMET was born from building a multi-party enterprise platform in production across the Nordic region — a system where **every party in the chain must want to use it** for it to work at all.

Field technicians, dispatchers, facility managers, franchise owners, regional directors, and C-level executives all use the same system. But a 77-year-old technician checking his phone between jobs in a cold storage room and a 38-year-old dispatcher with two monitors processing 100+ items per day cannot share the same experience.

We learned this the hard way:

- **If the technician finds the app annoying**, he calls the dispatcher instead. The dispatcher loses 8 minutes. Multiply by 200 technicians. That's 26 hours of wasted coordinator time per week.
- **If the franchise owner gets one wrong notification**, he disables all notifications. He misses the quotation approval. Work is blocked. The contractor calls. Everyone's frustrated.
- **If the contractor sees another company's data** — even for a split second during a loading state — trust is broken. Permanently.

The insight: **same system, different experience per role** isn't a nice-to-have. It's existential. And the only way to get it right is to start every feature by understanding who uses it, how their day changes, and what would make them stop.

---

## Quick Install

### Option 1: Plugin Marketplace (recommended)

Open Claude Code and run these two commands:

```
/plugin marketplace add https://github.com/Fruset/claude-gamet.git
```

Wait for "Successfully added marketplace: claude-gamet", then:

```
/plugin install gamet@claude-gamet
```

That's it. All 9 skills and 10 agents are now available. Run `/gamet-init` to set up your project.

To update later when new versions are released:

```
/plugin install gamet@claude-gamet
```

### Option 2: Copy into your project

```bash
git clone https://github.com/Fruset/claude-gamet.git
cp -r claude-gamet/skills/* your-project/.claude/skills/
cp -r claude-gamet/agents/* your-project/.claude/agents/
```

### Option 3: Personal skills (available in all your Claude Code projects)

```bash
git clone https://github.com/Fruset/claude-gamet.git
cp -r claude-gamet/skills/* ~/.claude/skills/
```

### Option 4: Claude Cowork / Claude.ai

Cowork doesn't auto-discover `.claude/skills/`. Instead:

1. **Via plugin marketplace** — if your organization has a private marketplace, add GAMET there
2. **Via zip upload** — zip individual skill folders and upload via Settings > Features > Custom Skills
3. **Via CLAUDE.md** — place a `CLAUDE.md` in the folder you share with Cowork that references GAMET principles

Note: Cowork has no terminal, no git, and limited code execution. Skills like `gamet-panel`, `gamet-impact`, and `gamet-discovery` work well (they analyze and advise). Skills like `gamet-orchestrator` and `gamet-init` that dispatch subagents and write files work best in Claude Code CLI.

| Skill              | Claude Code  | Cowork                             |
| ------------------ | ------------ | ---------------------------------- |
| gamet-init         | Full support | Limited (no file generation)       |
| gamet-panel        | Full support | Works (review + advise)            |
| gamet-impact       | Full support | Works (analysis + advise)          |
| gamet-discovery    | Full support | Works (analysis)                   |
| gamet-orchestrator | Full support | Limited (no subagent dispatch)     |
| gamet-research     | Full support | Limited (no knowledge base writes) |
| gamet-i18n         | Full support | Works (guidelines)                 |
| gamet-checkpoint   | Full support | Not applicable                     |
| gamet-ai-prep      | Full support | Works (analysis)                   |

### After installing

Run `/gamet-init` in Claude Code. It detects your project, asks questions about your business and users, and generates everything — personas, memory files, rules, and knowledge base.

---

## What You Get

### 9 Skills

| Skill                  | Trigger                                     | Purpose                                                                                                                                                                      |
| ---------------------- | ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **gamet-init**         | `/gamet-init`                               | Interactive setup — 8 questions about your business, users, industry. Generates personas, agents, memory, rules, knowledge base. Scans existing projects and adapts.         |
| **gamet-panel**        | `/gamet-panel` or "is this good enough?"    | Full GAMET review with YOUR custom personas. Journey threads across roles. Error state evaluation. Emotional impact prediction.                                              |
| **gamet-impact**       | "what would it take to build X?"            | Before any code: who is affected? How does their day change? What's the adoption risk? Dispatches parallel persona-analysis agents.                                          |
| **gamet-orchestrator** | `/gamet-orchestrator "feature"`             | The full pipeline: Impact → Design → Architecture → AI Prep → Plan → Build → Review → Ship. With improvement loop until quality reaches A.                                   |
| **gamet-discovery**    | "what should we build?"                     | Proactive — analyzes persona frustrations, learning log patterns, competitive gaps, regulatory deadlines. Surfaces what SHOULD be built, ranked by adoption impact.          |
| **gamet-research**     | domain-specific questions                   | Industry research with epistemic discipline. Maintains a growing knowledge base. Every claim classified: VERIFIED (sourced), ASSUMED (flagged), or UNCERTAIN (needs expert). |
| **gamet-i18n**         | "language", "translation", "plain language" | Different language for different people. The technician needs "Your next job: Building North." The CEO needs "SLA: 94% (target: 90%)." Both are correct.                     |
| **gamet-checkpoint**   | "checkpoint", "save progress"               | Context health — saves session state to files so you never lose progress. Recommends compact/clear at 50%/70%/85% context usage. Seamless resume.                            |
| **gamet-ai-prep**      | after architecture phase                    | Structure your data now for AI later. Auto-categorization, predictive alerts, smart suggestions — adding a field today saves restructuring 100k rows tomorrow.               |

### 10 Agents

| Agent                   | Model  | What They Do                                                                                                                                                                    |
| ----------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **product-analyst**     | opus   | Thinks about WHY a feature exists. Predicts adoption risk per persona with confidence levels. Maps workflow changes before → after.                                             |
| **gamet-review-panel**  | opus   | Coordinates the 3-dimension review (Purpose + Design + Reality). Synthesizes 15+ persona perspectives into actionable recommendations. Blocks domain-inappropriate suggestions. |
| **philosophy-mind**     | opus   | The conscience. Asks: Who has power here? Who is invisible? What happens at scale? What if we're wrong? Is this the RIGHT thing to build — not just the profitable thing?       |
| **industry-researcher** | sonnet | Follows the Researcher's Oath: never assumes, always cites, says "I don't know" when uncertain. Builds a growing verified knowledge base for your industry.                     |
| **backend-architect**   | sonnet | Designs data models with persona context. "This table needs contractor-scoped views because Sven must never see another company's data."                                        |
| **frontend-architect**  | sonnet | Every component decision answers: "Can the 77-year-old use this? Can the beginner understand this? Does this help the power user go faster?"                                    |
| **ux-writer**           | sonnet | Writes error messages humans understand. Not "Error 500" but "Something went wrong — your work is saved, try again in a moment." Different tone per persona.                    |
| **competitive-analyst** | sonnet | Knows what ServiceNow, Salesforce, and your niche competitors do well. Identifies switch triggers (why someone would choose you) and deal-killers (why they'd leave).           |
| **privacy-guardian**    | sonnet | GDPR compliance by design. Classifies every data field. Plans consent flows. Ensures right to erasure. Reviews every feature for data minimization.                             |
| **tech-advisor**        | sonnet | For new projects: recommends stack. For existing projects: scans codebase, produces health report, identifies outdated deps, suggests optimizations.                            |

---

## How It Works

### 1. Initialize

Run `/gamet-init`. For existing projects, it scans your codebase first. For new projects, it asks 8 questions.

From your answers, it generates **real personas** — not generic user types, but characters with names, ages, daily workflows, emotional baselines, frustration triggers, and dream features. Each persona knows what device they use, how long their sessions are, and what would make them stop using the system.

<details>
<summary>What gets generated</summary>

```
your-project/
├── .claude/
│   ├── skills/           ← 8 skills configured for YOUR domain
│   │   └── gamet-panel/
│   │       └── references/
│   │           ├── personas.md      ← YOUR users with daily workflows
│   │           ├── benchmarks.md    ← YOUR industry competitors
│   │           └── tensions.md      ← conflicts between YOUR personas
│   ├── agents/           ← 10 agents with YOUR project context
│   ├── rules/            ← path-scoped rules for YOUR tech stack
│   └── knowledge/
│       └── industry/     ← growing knowledge base
├── CLAUDE.md             ← extended with GAMET configuration
└── docs/features/        ← impact briefs and reviews saved here
```

Plus persistent memory files:

- Business model and adoption chain
- Learning log (grows with every feature you build)
- Market intelligence
- Epistemic discipline rules

</details>

### 2. Build

You describe what to build. GAMET handles the rest:

**Impact analysis** identifies who is affected and predicts adoption risk — before you write a single line of code. It dispatches parallel agents to analyze each persona's workflow change, emotional impact, and the one thing that would make them NOT use the feature.

**Specialist agents** are dispatched based on what's needed. A mobile UX issue gets the frontend-architect with Petra's (mobile persona) context. A data scoping issue gets the backend-architect with the privacy-guardian. A language concern gets the ux-writer with the i18n skill.

**GAMET review** runs 15+ personas through the 5 dimensions. When scores are below A, the **improvement loop** kicks in: triage findings by adoption chain impact, dispatch specialist fixes, verify no regressions, re-review. Loop until A or user says "ship anyway" (which gets logged — no judgment, but the system remembers).

### 3. Learn

Every feature makes the next one better:

- **Learning log** captures what worked and what didn't — with specifics, not vibes
- **Feature discovery** reads the log to surface systemic issues: "We've scored below B on mobile UX three times — this isn't a per-feature problem, it's a capability gap"
- **Impact analysis** checks past feature briefs before starting: "We built something similar 6 months ago — here's what we learned"
- **Iteration tracking** shows score improvement over time: "Kaj went from D to B+ after we added the dedicated mobile mode"

---

## Epistemic Discipline

Every agent in GAMET follows the **Researcher's Oath**:

> 1. I will not present assumptions as facts
> 2. I will cite sources for verified claims
> 3. I will say "I don't know" when I don't know
> 4. I will flag when knowledge might be outdated
> 5. I will search for the latest information, not rely on training data

This matters because the difference between "I know" and "I think" can be the difference between a compliant system and a regulatory violation.

| Status        | What It Means                                                          |
| ------------- | ---------------------------------------------------------------------- |
| **VERIFIED**  | Fact with source — "GDPR Article 17 requires right to erasure"         |
| **ASSUMED**   | Reasonable belief, explicitly flagged — "Most users prefer dashboards" |
| **UNCERTAIN** | Conflicting information — "Regulatory threshold unclear, ask DPO"      |

---

## The Philosophy Mind

Most development tools optimize for speed. GAMET also optimizes for **wisdom**.

The `philosophy-mind` agent is consulted when features touch power dynamics, data ethics, or societal impact. It asks:

- **Who has power here?** Does this feature give one party unfair advantage over another?
- **Who is invisible?** Are there affected people not represented by any persona?
- **What happens at scale?** If 1000 companies use this, what emergent behavior appears?
- **What if we're wrong?** If our assumptions about user behavior are incorrect, what's the harm?
- **Is this the RIGHT thing to build?** Not just profitable — genuinely good for the people who use it.

It presents ethical frameworks, not verdicts. The team decides.

---

## Security

This plugin contains **no secrets, credentials, API keys, or personal data**.

- All files are markdown instructions — no executable code
- Personas generated during init use fictional names and ages
- Business model data stays in local memory (never committed to git)
- The privacy-guardian agent actively recommends GDPR-compliant designs
- Safe to install in public and private repositories

---

## Requirements

- **Claude Code** 2.x or later
- **Opus model** recommended for panel reviews and product analysis
- **Sonnet model** sufficient for implementation, research, and specialist agents

---

## Contributing

The best contributions come from people who've used GAMET on a real project and found something missing:

- **Industry templates** — persona sets for healthcare, fintech, e-commerce, education, construction
- **Agent specializations** — DevOps, data engineering, marketing, customer success
- **Case studies** — how GAMET changed what you built and why
- **The thing we haven't thought of** — if you found a gap, others will too

---

## License

[MIT](LICENSE)

---

<p align="center">
  <strong>Built by humans who believe AI should understand people before writing code.</strong>
  <br><br>
  <a href="https://github.com/Fruset/claude-gamet">GitHub</a> · <a href="https://github.com/Fruset/claude-gamet/issues">Issues</a> · <a href="https://github.com/Fruset/claude-gamet/pulls">Contribute</a>
</p>
