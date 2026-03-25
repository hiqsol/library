---
title: >-
  "Agents" Means 4 Different Things and Almost Nobody Knows Which One
  They Need.
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=YpPcDHc3e9U
date: 2026-03-25 00:00
tags: ai, development, startups
---

# Summary

*Core argument:* "Agent" is an overloaded term covering four distinct
species. Using the wrong species for your problem is one of the most
common and costly mistakes in agentic AI deployment.

## The Four Agent Species

**1. Coding Harnesses**
- Simplest pattern: agent as standin for a developer (LLM + files +
  tools)
- Individual level: Karpathy runs agents 16 hrs/day; Steinberger
  managed multiple Codex agents on OpenClaw, ~20 min per task
- Key enabler: decomposition — break gnarly problems into
  well-defined single-agent chunks
- Project level (Cursor model): planner agent + short-running
  executor agents; one management layer only — three levels failed
- Insight: frame work around the agent, not the human; individual
  assistants speed up humans but preserve bottlenecks

**2. Dark Factories**
- Fully autonomous: spec in → agents iterate → eval gate → ship
- Human heavy at beginning (spec, intent) and end (eval, review);
  middle is automated
- Agents move too fast for humans to be useful in the middle
- Amazon incident: senior engineers called to Seattle over
  AI-generated production failures from junior engineer oversight gaps
- Practical hybrid: mostly dark factory + human eval review at the
  end

**3. Auto Research**
- Not about producing software — about optimizing a metric (hill
  climbing)
- Descended from classical ML techniques
- Examples: Toby Lütke optimized Liquid framework runtime; Karpathy
  released auto research for LLM training at GP-2 scale; conversion
  rate optimization
- Critical rule: no metric = not auto research
- Problem shape test: is it software-shaped (build) or
  metric-shaped (optimize)?

**4. Orchestration**
- Multiple specialized agents with role-based handoffs (writer →
  editor, researcher → drafter)
- Different from planner-executor: genuinely different roles, not
  one unified goal
- Platforms: LangGraph, Crew AI
- Most complex to set up; many human-intervention joints
- Scale determines viability: 10K tickets = worth it; 100 tickets =
  probably not

## Decision Framework

| Optimizing for…               | Species                  |
|-------------------------------|--------------------------|
| Task in front of you          | Coding harness (individual) |
| Project-scale output          | Coding harness (project)    |
| Spec-to-production autonomy   | Dark factory                |
| Rate / metric improvement     | Auto research               |
| Multi-role workflow routing   | Orchestration               |

## Key Warnings

- Do not use auto research to build software
- Do not use coding harnesses to write novels (orchestration or
  human task)
- Simple scales; complexity kills agent systems
- All four share LLM + tools + loop — the construction around that
  primitive is what differentiates them
