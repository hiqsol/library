---
title: The Truth About Developer Productivity in the AI Age (It's a Trap)
author: Steve Smith
channel: Modern Software Engineering
url: https://youtu.be/kDBeFOscZpc
date: 2026-03-11 00:00
tags: ai, development
---

# Summary: The Truth About Developer Productivity in the AI Age (It's a Trap)

[article](../../articles/steve-smith/2026-03-11-developer-productivity-ai-trap-activity-metrics.md)

- Gen AI triggers the worst organisational impulses: tripling down on Taylorism, measuring every
  line of code, treating activity counts as productivity progress.
- Industry is sliding backwards — from outcome metrics back to activity/output metrics — because
  they are easier to implement and easier to game.
- Goodhart's Law: "When a measure becomes a target, it ceases to be a good measure."
- Metric hierarchy: Activity (easy, low value) → Output (medium) → Outcome (hard, high value).
- DORA/Accelerate metrics are outcome metrics. AI usage metrics are activity metrics.
- History: Martin Fowler 2003 "can't measure productivity" → State of DevOps reports 2010s →
  Accelerate book (Forsgren) — statistically validated predictive model of org performance.
- Critique of DX "AI Assisted Engineering Q4 2025" report (135k devs, 400 companies, 3.5 months):
  - "90% AI adoption" — actually just tool usage, not strategic integration.
  - "3.6 hrs/week saved" — self-reported, depends on memory and subjective attribution,
    easily gamed.
  - "22% AI-authored code" — subjective definition ("no major human rewrites"), self-reported.
  - "Daily AI users ship 60% more PRs" — output metric; PR throughput ≠ delivery unit; no stat
    significance mentioned; easily gamed by abandoning unit tests.
- PR throughput tells you nothing about deployment throughput, service reliability, or business
  outcomes.
- Trunk-based development is a much better fit for CD than PRs.
- What to do: implement Accelerate metrics → ladder up to time-to-value + TCO → ladder up to
  business outcomes → only then correlate AI usage as leading indicator; be explicit
  correlation ≠ causation.
- Key capability leading indicators: trunk-based dev adoption, loose coupling of architectures, CI
  stability.
- Core message: the team is the unit of delivery, not the individual.
