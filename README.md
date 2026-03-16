# GAMET

> **Every feature starts with people, not code.**

A persona-driven AI development system that builds better products by understanding who uses them, how their day changes, and what makes them stay.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-9-blue)](skills/)
[![Agents](https://img.shields.io/badge/Agents-10-purple)](agents/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/Fruset/claude-gamet/pulls)

```
You: "Build a contractor marketplace"

GAMET: "5 personas affected. Sven has HIGH adoption risk — if the system
       auto-assigns his technicians, he walks. Recommending: suggest,
       never auto-assign."

       → Impact Brief → Design → Architecture → Build → Review (A-) → Ship
       → Learning log: "Calendar view raised Sven from C+ to A-"
       → Next feature starts smarter
```

---

## The Problem

You build a feature. Great code. Ship it. Then:

- The field technician can't use it — buttons too small for his 77-year-old fingers
- The franchise owner stopped logging in — one irrelevant notification, all alerts disabled forever
- The contractor saw another company's data for 0.3 seconds — trust broken permanently

These aren't bugs. They're **adoption failures**. They happen because we build for ourselves, not for the people who use our software.

---

## The GAMET Framework

Five questions every feature must answer:

|       | Criterion    | The Question                                                                               |
| ----- | ------------ | ------------------------------------------------------------------------------------------ |
| **G** | **Guidance** | Does the system lead the user to the right action — or do they have to figure it out?      |
| **A** | **Adoption** | Would this person CHOOSE this over phone calls, Excel, or paper?                           |
| **M** | **Meaning**  | Does this have genuine purpose that couldn't exist without the system?                     |
| **E** | **Ease**     | Can a first-timer understand in 2 minutes? Can someone returning after 3 months re-orient? |
| **T** | **Trust**    | Does the user trust the data? The actions? Feel safe clicking that button?                 |

---

## Getting Started

### Claude Code (full experience)

<details open>
<summary><strong>Option A: Plugin Marketplace (recommended)</strong></summary>

```
/plugin marketplace add https://github.com/Fruset/claude-gamet.git
```

Wait for "Successfully added marketplace", then:

```
/plugin install gamet@claude-gamet
```

Updates: run `/plugin install gamet@claude-gamet` again when new versions are released.

</details>

<details>
<summary><strong>Option B: Copy into your project</strong></summary>

```bash
git clone https://github.com/Fruset/claude-gamet.git
cp -r claude-gamet/skills/* your-project/.claude/skills/
cp -r claude-gamet/agents/* your-project/.claude/agents/
```

</details>

<details>
<summary><strong>Option C: Global install (all your projects)</strong></summary>

```bash
git clone https://github.com/Fruset/claude-gamet.git
cp -r claude-gamet/skills/* ~/.claude/skills/
```

</details>

After installing, run `/gamet-init` — it detects your project, asks 8 questions, and generates everything: personas, agents, memory, rules, knowledge base.

### Claude Cowork / Claude.ai

Cowork runs in a sandboxed VM without terminal or git. GAMET's advisory skills work well — the pipeline and file-generation skills need Claude Code.

| What works in Cowork                                    | What needs Claude Code                                  |
| ------------------------------------------------------- | ------------------------------------------------------- |
| **gamet-panel** — review features with GAMET personas   | **gamet-init** — generates files, agents, memory        |
| **gamet-impact** — analyze who is affected by a feature | **gamet-orchestrator** — 8-step pipeline with subagents |
| **gamet-discovery** — identify what to build next       | **gamet-checkpoint** — context health management        |
| **gamet-i18n** — language guidelines per persona        | **gamet-research** — writes to knowledge base           |
| **gamet-ai-prep** — evaluate AI/ML readiness            |                                                         |

**How to install in Cowork:**

1. Zip individual skill folders (each containing `SKILL.md`)
2. Upload via **Settings → Features → Custom Skills** in Claude.ai
3. Or place a `CLAUDE.md` referencing GAMET principles in the folder you share with Cowork

---

## What's Inside

### 9 Skills

| Skill                  | Trigger                          | Purpose                                                                                                                  |
| ---------------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **gamet-init**         | `/gamet-init`                    | Interactive setup — asks about your business, users, industry. Generates everything. Scans existing projects and adapts. |
| **gamet-panel**        | `/gamet-panel`                   | GAMET review with YOUR custom personas. Journey threads. Error states. Emotional impact.                                 |
| **gamet-impact**       | "what would it take to build X?" | Persona impact analysis — adoption risk, workflow mapping, GAMET pre-scores.                                             |
| **gamet-orchestrator** | `/gamet-orchestrator "feature"`  | 8-step pipeline with improvement loop, specialist dispatch, regression guard.                                            |
| **gamet-discovery**    | "what should we build?"          | Surfaces opportunities from persona frustrations, competitive gaps, regulatory needs.                                    |
| **gamet-research**     | domain-specific questions        | Industry research. Every claim: VERIFIED, ASSUMED, or UNCERTAIN.                                                         |
| **gamet-i18n**         | "language", "translation"        | Per-persona language levels. The technician and the CEO need different words.                                            |
| **gamet-checkpoint**   | "checkpoint"                     | Context health — saves state, recommends compact/clear. Seamless resume.                                                 |
| **gamet-ai-prep**      | after architecture               | Structure data now for AI later. Adding a field today saves restructuring tomorrow.                                      |

### 10 Agents

#### Strategic thinking (opus)

| Agent                  | Role                                                                                         |
| ---------------------- | -------------------------------------------------------------------------------------------- |
| **product-analyst**    | Predicts adoption risk per persona. Maps workflow changes before → after.                    |
| **gamet-review-panel** | Orchestrates 3-dimension GAMET review. Synthesizes 15+ perspectives. Blocks bad suggestions. |
| **philosophy-mind**    | The conscience. "Who has power? Who is invisible? Is this the RIGHT thing to build?"         |

#### Specialist execution (sonnet)

| Agent                   | Role                                                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **industry-researcher** | Follows the Researcher's Oath — never assumes, always cites, says "I don't know."                                               |
| **backend-architect**   | Data models with persona context. "This table needs scoped views because the contractor must never see another company's data." |
| **frontend-architect**  | Every component answers: "Can the 77-year-old use this? Can the beginner understand it? Does it help the power user go faster?" |
| **ux-writer**           | Not "Error 500" but "Something went wrong — your work is saved, try again in a moment." Different tone per persona.             |
| **competitive-analyst** | Switch triggers (why choose us) and deal-killers (why leave).                                                                   |
| **privacy-guardian**    | GDPR by design. Data classification. Consent flows. Right to erasure.                                                           |
| **tech-advisor**        | New projects: recommends stack. Existing: scans, reports, optimizes.                                                            |

---

## How It Works

### 1. Initialize

`/gamet-init` asks 8 questions about your business, users, industry, competitors, regulations, tech stack, and market.

From your answers it generates **real personas** — characters with names, ages, daily workflows, emotional baselines, frustration triggers, and the one thing that would make them stop using the system.

<details>
<summary>What gets generated</summary>

```
your-project/
├── .claude/
│   ├── skills/              ← 8 skills configured for YOUR domain
│   │   └── gamet-panel/
│   │       └── references/
│   │           ├── personas.md       ← YOUR users with daily workflows
│   │           ├── benchmarks.md     ← YOUR industry competitors
│   │           └── tensions.md       ← conflicts between YOUR personas
│   ├── agents/              ← 10 agents with YOUR project context
│   ├── rules/               ← path-scoped rules for YOUR tech stack
│   └── knowledge/
│       └── industry/        ← growing, verified knowledge base
├── CLAUDE.md                ← extended (not overwritten) with GAMET config
└── docs/features/           ← impact briefs and reviews saved here
```

Plus persistent memory:

- Business model and adoption chain
- Learning log (grows with every feature)
- Market intelligence
- Epistemic discipline rules

</details>

### 2. Build

You describe what to build. GAMET runs the pipeline:

```
Step 1  Impact       Who is affected? Adoption risk per persona
Step 2  Design       Brainstorm with persona context
Step 3  Architecture Data model, API, security, GDPR — with domain awareness
Step 4  AI Prep      Structure data for future ML capabilities
Step 5  Plan         Tasks annotated with affected personas
Step 6  Build        Subagents with regression guard and cleanup
Step 7  Review       GAMET panel grades G/A/M/E/T per persona
Step 7.5 Fix Loop    Triage → specialist dispatch → re-review → until A
Step 8  Ship         Commit, push, update learning log
```

### 3. Learn

Every feature makes the next one better:

- **Learning log** — captures what worked and what didn't, with specifics
- **Feature discovery** — reads the log: "We've scored below B on mobile UX three times — systemic issue"
- **Impact analysis** — checks past briefs: "We built something similar 6 months ago, here's what we learned"
- **Iteration tracking** — shows improvement: "Kaj went from D to B+ after the dedicated mobile mode"

---

## Where It Comes From

GAMET was born from building a multi-party enterprise platform in production across the Nordic region — where **every party in the chain must want to use it** for it to work.

Field technicians, dispatchers, facility managers, franchise owners, regional directors, and C-level executives all use the same system. But a 77-year-old technician checking his phone between jobs in a cold storage room cannot share the same experience as a 38-year-old dispatcher with two monitors processing 100+ items per day.

We learned this the hard way:

- **If the technician finds the app annoying**, he calls the dispatcher instead. The dispatcher loses 8 minutes. Multiply by 200 technicians — 26 hours of wasted coordinator time per week.
- **If the franchise owner gets one wrong notification**, he disables all alerts. Misses quotation approval. Work blocked. Everyone frustrated.
- **If the contractor sees another company's data** — even for a split second — trust is broken. Permanently.

The insight: **same system, different experience per role** is existential. The only way to get it right is to start every feature by understanding who uses it and what would make them stop.

---

## Epistemic Discipline

Every agent follows the **Researcher's Oath**:

> 1. I will not present assumptions as facts
> 2. I will cite sources for verified claims
> 3. I will say "I don't know" when I don't know
> 4. I will flag when knowledge might be outdated
> 5. I will search for the latest information, not rely on training data

| Status        | Meaning                                                        |
| ------------- | -------------------------------------------------------------- |
| **VERIFIED**  | Fact with source — "GDPR Article 17 requires right to erasure" |
| **ASSUMED**   | Reasonable belief, flagged — "Most users prefer dashboards"    |
| **UNCERTAIN** | Conflicting info — "Regulatory threshold unclear, ask DPO"     |

The `philosophy-mind` agent goes further:

- **Who has power here?** Does this feature give one party unfair advantage?
- **Who is invisible?** Are there affected people not represented by any persona?
- **What if we're wrong?** If our assumptions are incorrect, what's the harm?
- **Is this the RIGHT thing to build?** Not just profitable — genuinely good.

---

## Security

No secrets, credentials, API keys, or personal data. All files are markdown instructions. Personas use fictional names. Business data stays in local memory, never committed. Safe for public and private repos.

## Requirements

**Claude Code** 2.x or later. Opus recommended for reviews and analysis. Sonnet sufficient for specialist agents.

## Contributing

The best contributions come from people who've used GAMET and found something missing. [Industry templates](CONTRIBUTING.md), agent specializations, case studies, or the thing we haven't thought of.

## License

[MIT](LICENSE)

---

<p align="center">
  <strong>Built by humans who believe AI should understand people before writing code.</strong>
  <br><br>
  <a href="https://github.com/Fruset/claude-gamet">GitHub</a> · <a href="https://github.com/Fruset/claude-gamet/issues">Issues</a> · <a href="https://github.com/Fruset/claude-gamet/pulls">Contribute</a>
</p>
