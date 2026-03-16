# Launch Post — For Reddit, Hacker News, Twitter/X

## Short version (Twitter/X, 280 chars)

We built GAMET — an open-source plugin for Claude Code that makes every feature start with understanding who uses it, not what tech to use.

9 skills, 10 AI agents, 5 evaluation criteria. MIT licensed.

github.com/Fruset/claude-gamet

---

## Medium version (Reddit r/ClaudeAI, r/programming)

**Title:** GAMET — We built a persona-driven AI development system for Claude Code (open source)

**Body:**

We kept shipping features that technically worked but people didn't use. The 77-year-old field technician couldn't tap the buttons. The franchise owner got one wrong notification and disabled all alerts forever. The contractor saw another company's data for half a second and never trusted the platform again.

These weren't bugs. They were adoption failures.

So we built GAMET — a system where every feature starts by understanding the humans who will use it:

**G**uidance — Does the system lead the user to the right action?
**A**doption — Would this person CHOOSE to use this over phone/Excel/paper?
**M**eaning — Does this have genuine purpose that can't exist without the system?
**E**ase — Can a first-timer figure this out in 2 minutes?
**T**rust — Does the user trust the system with their data and decisions?

What it does:

- `/gamet-init` asks 8 questions about your project → generates 10-15 custom personas with daily workflows, emotional states, and stress triggers
- Every feature goes through an 8-step pipeline: Impact Analysis → Design → Architecture → AI Prep → Plan → Build → GAMET Review → Ship
- 10 AI agents (product analyst, privacy guardian, philosophy mind, etc.) are dispatched based on what each feature needs
- A learning log captures what worked and what didn't — so every feature makes the next one better
- The `philosophy-mind` agent asks questions nobody else asks: "Who has power here? What if we're wrong? Is this the RIGHT thing to build?"

It came from building a real enterprise platform where technicians, dispatchers, facility managers, franchise owners, and CEOs all use the same system — but need fundamentally different experiences.

**9 skills. 10 agents. 9 templates. MIT licensed. No secrets, no credentials.**

GitHub: https://github.com/Fruset/claude-gamet

Would love feedback — especially from anyone who's struggled with "we built it and nobody came."

---

## Long version (Hacker News, Dev.to, personal blog)

**Title:** We stopped building features and started building for people — here's the system we created

We've been building enterprise software for years. Multi-party platforms where technicians, dispatchers, facility managers, franchise owners, regional directors, and C-level executives all need to use the same system.

Here's what we learned: **the most impactful decisions have nothing to do with technology.**

A 77-year-old field technician on a Samsung phone in a cold storage room cannot share the same UI defaults as a 38-year-old dispatcher with two monitors processing 100+ items per day. This isn't a responsive design problem — it's a fundamentally different cognitive context, different session length (30 seconds vs 8 hours), different emotional baseline (cautious vs impatient), and different definition of success (found the address vs triaged the queue).

When we ignored this, features technically worked but adoption failed:

- The technician called the office instead of using the app → 26 hours/week of wasted coordinator time
- The franchise owner disabled notifications after one irrelevant alert → missed critical quotation approval → work blocked
- The contractor saw another company's data during a loading state → permanently lost trust

So we built GAMET.

### The Framework

Five questions every feature must answer:

1. **Guidance** — Does the system lead the user to the right action at the right time? Or do they have to figure it out?
2. **Adoption** — Would this person CHOOSE to use this voluntarily? What do they gain over their current method?
3. **Meaning** — Does this feature have genuine purpose? Could this value exist without the system?
4. **Ease** — Can a first-timer understand this in 2 minutes? Can someone returning after 3 months re-orient?
5. **Trust** — Does the user trust the data? The actions? Do they feel safe clicking that button?

### The System

GAMET is a Claude Code plugin (9 skills + 10 agents) that transforms how you build:

**Before GAMET:** "Build feature X" → code → ship → discover nobody uses it

**After GAMET:** "Build feature X" → Impact Analysis (who is affected? adoption risk?) → Design (with persona context) → Architecture (with GDPR review) → Build (with regression guard) → GAMET Review (15+ personas grade G/A/M/E/T) → Fix loop until A → Ship → Learning log updated → Next feature starts smarter

The most interesting parts:

- **Epistemic discipline**: Every agent classifies claims as VERIFIED (sourced), ASSUMED (flagged), or UNCERTAIN (needs expert). Because in regulated industries, the difference between "I know" and "I think" can be a legal liability.

- **The philosophy-mind agent**: Asks "Who has power here? Who is invisible? What happens at scale? Is this the RIGHT thing to build — not just the profitable thing?" It presents ethical frameworks, not verdicts. The team decides.

- **Learning loop**: Every GAMET review feeds a learning log. Every new feature reads it. The system literally gets smarter with every feature you build. "We've scored below B on mobile UX three times — this is a systemic issue, not a per-feature bug."

- **Self-review on init**: When `/gamet-init` finishes generating your personas and skills, it reviews its own output, grades it, and iterates until quality reaches B or higher.

### Try It

```
/plugin marketplace add Fruset/claude-gamet
/plugin install gamet@claude-gamet
/gamet-init
```

Or just clone and copy:

```bash
git clone https://github.com/Fruset/claude-gamet.git
cp -r claude-gamet/skills/* your-project/.claude/skills/
cp -r claude-gamet/agents/* your-project/.claude/agents/
```

MIT licensed. No secrets, no credentials, no personal data. 34 markdown files.

GitHub: https://github.com/Fruset/claude-gamet

We'd genuinely love to hear from anyone who's dealt with similar adoption challenges — especially in healthcare, fintech, or other regulated multi-stakeholder domains where "technically correct" and "actually useful" are very different things.
