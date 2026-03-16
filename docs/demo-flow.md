# GAMET Demo Flow

Use this to create a screen recording or demo GIF.

## Script (2-3 minutes)

### Scene 1: Init (30 sec)

```
$ claude
> /gamet-init

GAMET: "I detected Next.js 16 + Prisma + MariaDB. Let me ask a few questions."

Q1: "What does your system do?"
> "Facility management for cooling systems"

Q2: "Who are the users?"
> "Coordinators (daily), technicians (mobile), facility managers (weekly), CEOs (monthly)"

GAMET: "Generating 14 personas..."
✓ Created: Tommy (Coordinator, 38, desktop, all day)
✓ Created: Kaj (Technician, 77, Samsung, 30 sec sessions)
✓ Created: Birgitta (Facility Admin, 58, laptop, weekly)
✓ Created: Helena (CEO, 49, mobile, 30 seconds)
...
✓ 14 personas generated
✓ 10 agents configured
✓ Learning log initialized
✓ Knowledge base ready

Setup grade: A-
"Ready. Try: 'build a contractor marketplace'"
```

### Scene 2: Impact Analysis (30 sec)

```
> build a contractor marketplace

GAMET Impact Analysis:
┌─────────────────────────────────────────────┐
│ Persona        │ Risk     │ Day Change      │
│ ─────────────  │ ──────── │ ──────────────  │
│ Sven (45)      │ HIGH     │ -20 min/day     │
│ Anders (42)    │ HIGH     │ -3 min/session  │
│ Tommy (38)     │ LOW      │ -15 min/day     │
│ Birgitta (58)  │ MEDIUM   │ -7 min/session  │
└─────────────────────────────────────────────┘

⚠️ Sven: "Protective about his business. If the system
    auto-assigns his technicians, he walks."
    → Resolution: suggest, never auto-assign

Proceed to design? [Y/n]
```

### Scene 3: Build + Review Loop (60 sec)

```
> Y

[Step 2: Design] 3 approaches evaluated...
[Step 3: Architecture] backend-architect + privacy-guardian dispatched...
[Step 6: Build] 4 subagents implementing...
[Step 7: GAMET Review]

┌─────────────────────────────────────────────┐
│ GAMET Scores                                │
│ G (Guidance):  B+  "Clear for Tommy,       │
│                     confusing for Anders"    │
│ A (Adoption):  C+  "Sven needs calendar     │
│                     view, not list"          │
│ M (Meaning):   A-  "Real value — replaces   │
│                     phone-based ordering"    │
│ E (Ease):      B   "Too many steps for      │
│                     first listing"           │
│ T (Trust):     B+  "Data scoping correct"   │
└─────────────────────────────────────────────┘

Average: B — Below target A

[Step 7.5: Fix Planning]
Fix 1: Simplify listing to 3 fields → frontend-architect
Fix 2: Add calendar view for Sven → frontend-architect
Fix 3: Reduce Anders to single-screen → ux-writer

[Step 7.6: Implementing fixes...]
[Step 7.7: Re-review]

GAMET Score: A-  ✓ Target reached

[Step 8: Ship]
✓ Committed: "feat: contractor marketplace"
✓ Learning log: "Calendar view raised Sven from C+ to A-"
✓ Pushed to remote
```

### Scene 4: Learning (15 sec)

```
> what should we build next?

GAMET Discovery:
1. Offline mode for Kaj (HIGH value — adoption chain #1)
   "Kaj scored D on connectivity. This is systemic."
2. Inspection scheduling (REGULATORY — EU deadline 2027)
3. Quotation line-item tooltips for Birgitta
   "Scored C on Trust — she doesn't understand what she's approving"

Based on learning log: mobile UX is our biggest gap.
Recommend: build offline mode next.
```

## Key Moments to Capture

1. The persona table appearing with real names and adoption risks
2. The ⚠️ warning about Sven being protective
3. GAMET scores showing specific persona-aware feedback
4. The fix loop: B → A- in one iteration
5. Discovery recommending based on learning log patterns
