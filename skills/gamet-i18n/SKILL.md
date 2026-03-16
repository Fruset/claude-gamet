---
name: gamet-i18n
description: "Language and localization guidelines — persona-appropriate language levels, jargon handling, error message humanization, i18n architecture, UX writing principles. Triggers on 'language', 'translation', 'i18n', 'plain language'."
---

# Language & Localization

The system must speak the RIGHT language to the RIGHT person.

## Language Level Per Persona

(Configured by gamet-init based on project personas)

{{LANGUAGE_LEVELS_TABLE}}

## Principles

1. Code in English, UI in target market language
2. Never hardcode strings — use translation keys from day one
3. Technical terms: keep in English where users expect it (SLA, KPI, PDF)
4. Error messages: actionable, not technical ("Something went wrong" → "Check your connection and try again")
5. Confirmations: WHAT happened + WHO notified + WHAT next

## UX Writing Checklist

- [ ] No hardcoded strings
- [ ] Labels understandable by beginner persona
- [ ] Error messages tell user what to DO
- [ ] Button labels are verbs
- [ ] Numbers/dates formatted for target market
