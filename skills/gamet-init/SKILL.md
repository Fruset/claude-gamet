---
name: gamet-init
description: Interactive project setup — asks questions about your business, users, and industry, then generates a complete persona-driven development system (GAMET panel, pipeline, research, i18n, learning loop). Run once per project with "/gamet-init". Like "claude init" but for building products that people actually want to use.
user-invocable: true
---

# GAMET Project Initialization

Set up a complete persona-driven development system for your project. This runs ONCE and generates all the skills, personas, and knowledge structures your project needs.

## The Process

### Phase 0: Detect Existing Project (automatic)

Before asking questions, SCAN the project:

```
1. Check for package.json / requirements.txt / Gemfile → detect tech stack
2. Check for .claude/ directory → already has skills/agents?
3. Check for CLAUDE.md → already has conventions?
4. Check for src/ or app/ → existing codebase structure?
5. Check for .env.example → what services are used?
```

**If existing project detected:**

- Dispatch `tech-advisor` agent to produce Tech Health Report
- Pre-fill Q7 (tech stack) from scan results
- Show user: "I detected [framework] v[X] with [database]. Is this correct?"
- Identify what GAMET skills are MISSING vs already set up
- Adapt: don't overwrite existing CLAUDE.md — extend it

**If bare/new project:**

- Proceed to Phase 1 (all questions)
- Offer tech stack recommendations via `tech-advisor`

### Phase 1: Understand the Business (AskUserQuestion)

Ask these questions interactively. Skip any the user already answered.

**Question 1: What does your system do?**

```
"Describe your product in 2-3 sentences. What problem does it solve? For whom?"
```

**Question 2: Who are the users?**

```
"List the different types of users (roles). For each:
- What do they do? (daily tasks)
- How often do they use the system? (daily/weekly/monthly)
- What device? (desktop/mobile/tablet)
- What's their technical skill level? (expert/intermediate/beginner)
- What would make them STOP using the system?"
Options: [Add roles one by one via multiSelect or free text]
```

**Question 3: What's the business model?**

```
"How does the business work?"
Options:
- SaaS subscription (users pay monthly)
- Multi-party platform (multiple parties must ALL use it)
- Internal tool (company-internal, adoption is mandatory)
- B2C product (consumers choose to use it)
- Other (describe)
```

**Question 4: What industry?**

```
"What industry or domain?"
Options:
- Facility Management / Property
- Healthcare
- E-commerce / Retail
- SaaS / Tech
- Finance
- Education
- Construction
- Logistics
- Other (describe)
```

**Question 5: Competitors?**

```
"What systems do your users currently use or compare you against?
(e.g., ServiceNow, Salesforce, Excel, paper, a competitor product)"
```

**Question 6: Regulatory requirements?**

```
"Are there regulations or compliance requirements?"
Options:
- Yes (describe: GDPR, industry-specific, environmental, financial)
- No
- Not sure
```

**Question 7: Tech stack?**

```
"What's your tech stack?"
Options:
- Next.js / React
- Vue / Nuxt
- Python / Django / Flask
- Ruby on Rails
- Java / Spring
- Other (describe)
```

**Question 8: Language/market?**

```
"What language(s) and market?"
Options:
- English only
- Swedish (with English code)
- Multi-language (specify)
- Other
```

### Phase 2: Generate Personas (Agent dispatch)

From the answers, generate 10-15 personas:

**For each user role identified, create 1-3 personas:**

- A power user (uses daily, wants speed)
- A beginner/reluctant user (uses rarely, needs simplicity)
- An executive/manager (wants overview, not detail)

**Always include these universal personas:**

- Sales/Demo persona (needs the product to look impressive)
- Edge-case/QA persona (what breaks?)

**Per persona, generate:**

```markdown
### N. Name — Role Title

**Age:** X | **Frequency:** Y | **Device:** Z | **Session:** W | **Where:** V

**Mantra:** "One-line philosophy"

**Daily workflow:**

1. Step one
2. Step two

**Motivates:** [what drives them]
**Frustrates:** [what makes them stop]
**Would love:** [dream feature]
**Tests:** [how they evaluate]
**Compares with:** [what systems they've used]
**Emotional baseline:** [calm/anxious/impatient/protective]
**Stress trigger:** [what pushes them over]
```

### Phase 3: Generate Skills

Create these files in the project's `.claude/skills/` directory:

**1. Panel skill** (from `gamet-panel` template)

- Inject generated personas
- Set industry-specific benchmarks
- Configure tensions based on persona conflicts

**2. Impact skill** (from `gamet-impact` template)

- Configure persona quick-ref with generated personas
- Set adoption chain priority based on business model

**3. Orchestrator** (from `gamet-orchestrator` template)

- Configure tech stack references
- Set specialist dispatch table based on tech stack

**4. Research skill** (from `gamet-research` template)

- Configure industry domains to research
- Set regulatory topics based on answer to Q6

**5. i18n skill** (from `gamet-i18n` template)

- Configure language per persona
- Set market-specific formatting

**6. Checkpoint skill** (from `gamet-checkpoint` template)

- No customization needed — universal

**7. Discovery skill** (from `gamet-discovery` template)

- Configure with industry competitors
- Set regulatory calendar if applicable

**8. AI-prep skill** (from `gamet-ai-prep` template)

- No customization needed — universal

### Phase 3.5: Generate Agents

Create these files in the project's `.claude/agents/` directory:

```
.claude/agents/
├── gamet-review-panel.md     ← GAMET orchestrator (from template)
├── product-analyst.md        ← Market, personas, adoption (from template)
├── industry-researcher.md    ← Domain research, epistemic discipline (from template)
├── backend-architect.md      ← Data model, API, security (from template)
├── frontend-architect.md     ← Components, responsive, a11y (from template)
├── ux-writer.md              ← Per-persona language (from template)
├── competitive-analyst.md    ← Market positioning (from template)
├── privacy-guardian.md       ← GDPR, data classification (from template)
├── philosophy-mind.md        ← Ethics, bias, power dynamics (from template)
└── tech-advisor.md           ← Stack evaluation, optimization (from template)
```

Each agent gets project-specific context injected:

- `gamet-review-panel.md` gets the generated persona list
- `backend-architect.md` gets the detected tech stack conventions
- `privacy-guardian.md` gets the regulatory requirements from Q6
- `industry-researcher.md` gets the industry domains from Q4

### Phase 4: Generate Directory Structure

Create the COMPLETE file tree:

```
PROJECT ROOT/
├── .claude/
│   ├── skills/
│   │   ├── gamet-panel/
│   │   │   ├── SKILL.md               ← GAMET framework + persona summary
│   │   │   └── references/
│   │   │       ├── personas.md         ← Full persona definitions
│   │   │       ├── benchmarks.md       ← Industry competitors
│   │   │       └── tensions.md         ← Persona conflicts + resolution
│   │   ├── gamet-impact/
│   │   │   ├── SKILL.md               ← Impact analysis process
│   │   │   └── references/
│   │   │       └── persona-quick-ref.md ← Quick lookup table
│   │   ├── gamet-orchestrator/
│   │   │   └── SKILL.md               ← 8-step pipeline
│   │   ├── gamet-discovery/
│   │   │   └── SKILL.md               ← Feature discovery
│   │   ├── gamet-research/
│   │   │   └── SKILL.md               ← Industry research
│   │   ├── gamet-i18n/
│   │   │   └── SKILL.md               ← Language guidelines
│   │   ├── gamet-checkpoint/
│   │   │   └── SKILL.md               ← Context health
│   │   └── gamet-ai-prep/
│   │       └── SKILL.md               ← AI readiness
│   ├── agents/                        ← (10 agents listed above)
│   ├── rules/
│   │   ├── gamet.md                   ← Universal GAMET rules (no path scope)
│   │   └── [tech-stack].md            ← Tech-specific rules (path-scoped)
│   ├── knowledge/
│   │   └── industry/
│   │       └── _index.md              ← Empty, ready for research
│   └── PROGRESS.md                    ← Empty template
├── CLAUDE.md                          ← Generated from template (or extended if exists)
└── docs/
    └── features/
        ├── .gitkeep
        └── discovery/
            └── .gitkeep
```

**Memory files** (in `~/.claude/projects/[project-path]/memory/`):

```
~/.claude/projects/[project-path]/memory/
├── MEMORY.md                          ← Index pointing to all memory files
├── project_business_model.md          ← From Q3 answers
├── project_learning_log.md            ← Empty template, ready to grow
├── project_market_intelligence.md     ← Seeded with Q5 competitors
└── feedback_epistemic_discipline.md   ← Universal (always created)
```

**CLAUDE.md** — Generated from `templates/CLAUDE.md.template`:

- If CLAUDE.md already exists: EXTEND it (add Skills section, don't overwrite)
- If no CLAUDE.md: create from template with project info from Q1-Q8

**Rules** — Generated from `templates/rules.md.template`:

- Universal GAMET rule file (no path scope): epistemic discipline, impact-first
- Tech-stack-specific rule file (path-scoped): from tech-advisor scan or Q7

### Phase 5: Verify & Report

```
"GAMET initialization complete! Here's what was created:

Personas: [N] across [roles]
Skills: [list]
Memory: [list]
Rules: [list]

To test: try saying 'build [a feature from your domain]'
The system should automatically run impact analysis first.

To discover what to build: run /gamet-discovery
To review existing features: run /gamet-panel
```

### Phase 6: Self-Review Loop

After generating everything, verify the setup is complete and high-quality:

```
1. INVENTORY CHECK:
   - All skills created? (panel, impact, orchestrator, discovery, research, i18n, checkpoint, ai-prep)
   - All agents created? (product-analyst, industry-researcher, gamet-review-panel, + tech-specific)
   - Memory files created? (business model, learning log, market intelligence, epistemic discipline)
   - Rules files created? (tech-stack specific)
   - Knowledge directory created?

2. CONNECTION CHECK:
   - Each skill references the skills it depends on?
   - Personas referenced consistently (no duplicated, no missing)?
   - Orchestrator can invoke each skill?
   - Agents know which skills/files to load?

3. QUALITY CHECK (dispatch skill-creator review agent):
   - Are personas realistic and diverse enough?
   - Do GAMET criteria make sense for this industry?
   - Are there obvious missing personas (check against user roles)?
   - Is the adoption chain logically ordered?
   - Are domain-specific benchmarks appropriate (not generic)?

4. TEST RUN:
   - Simulate: "build [a feature from this domain]"
   - Does gamet-impact trigger correctly?
   - Does it identify the right personas?
   - Does it produce a sensible Impact Brief?

5. GRADE & ITERATE:
   Grade the setup A-F on:
   - Persona completeness (do all user roles have personas?)
   - Domain awareness (would the panel give domain-specific, not generic, feedback?)
   - Pipeline coherence (do all 8 steps connect?)
   - Adoption chain accuracy (is the priority order correct?)

   If any dimension < B:
   → Identify the gap
   → Fix it (add persona, adjust skill, rewrite section)
   → Re-grade
   → Loop until all dimensions ≥ B

6. REPORT TO USER:
   "GAMET setup complete!

   Setup grade: [A/B/C]
   Personas: [N] covering [roles]
   Agents: [N] ([list])
   Skills: [N] ([list])

   [If < A]: Areas for improvement: [list]
   [If A]: System is ready. Try: 'build [suggested feature]'

   Next steps:
   1. Run /gamet-discovery to see what the system suggests building first
   2. Or describe a feature to start the pipeline"
```

## Template Files

Templates are in the `templates/` directory of this plugin. They contain placeholder markers like `{{PERSONAS}}`, `{{INDUSTRY}}`, `{{TECH_STACK}}` that get replaced during generation.

## Security Notes

- This skill generates FILES only — no network calls, no secrets
- Generated personas use fictional names and ages
- Business model info is saved to LOCAL memory only (not committed to git)
- No API keys, tokens, or credentials are ever created or stored
- The `.claude/knowledge/` directory should be gitignored if it contains proprietary research
