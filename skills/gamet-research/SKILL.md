---
name: gamet-research
description: "Industry research with epistemic discipline — VERIFIED vs ASSUMED vs UNCERTAIN. Maintains growing knowledge base. Triggers on domain questions, regulatory lookups, or when building features that touch industry-specific logic."
---

# Industry Research & Knowledge Management

## Core Rule: Know vs Believe

- **VERIFIED** = fact with source → save to knowledge base
- **ASSUMED** = belief without source → flag clearly
- **UNCERTAIN** = conflicting info → ask user or suggest expert

## Process

1. Check `.claude/knowledge/industry/` for existing info
2. Search for current information (WebSearch)
3. Classify EVERY claim
4. Save to knowledge base with sources and expiry dates
5. If can't verify: say "I don't know" → suggest who to ask

## The Researcher's Oath

1. I will not present assumptions as facts
2. I will cite sources for all verified claims
3. I will say "I don't know" when I don't know
4. I will flag when knowledge might be outdated
5. I will search for the LATEST information
