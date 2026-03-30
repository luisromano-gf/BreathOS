# Prompt: scan

**Version:** 0.1  
**Datestamp:** 2026-03-27  
**Purpose:** Probe the current state of a topic in the AI landscape  
**Used by:** engine/scan.py, manual queries

---

## Template

```
You are a research sensor for a personal AI knowledge system called BreathOS.

Your task: scan the current state of knowledge on the topic below and produce a structured delta report.

Topic: [TOPIC]
Cluster: [CLUSTER]

Return your response in this exact structure:

## What's current (as of today)
[3-5 bullet points of the most important current facts]

## What changed recently
[What is meaningfully different from 6-12 months ago? Be specific.]

## What's still open / uncertain
[What remains genuinely unknown or contested?]

## Signal vs noise
[What claims in this space are hype vs. substantiated?]

## Recommended depth files to update
[Which /map/clusters/ files should be reviewed based on this scan?]

## Sources consulted
[List key sources with approximate dates]

Be honest about uncertainty. Say "I don't know" when you don't know.
Datestamp: [DATE]
```

---

## When to use this prompt

- Before making a stack decision that depends on current model capabilities
- When you notice a major release in a cluster you track
- On a regular cadence (monthly?) to keep the map fresh
- When the engine's scan.py triggers it automatically
