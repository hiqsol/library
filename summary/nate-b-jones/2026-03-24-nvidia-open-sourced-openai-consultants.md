---
title: "Nvidia Just Open-Sourced What OpenAI Wants You to Pay Consultants For."
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=7AO4w4Y_L24
date: 2026-03-24 00:00
tags: ai, development, startups
---

# Summary

[article](../../articles/nate-b-jones/2026-03-24-nvidia-open-sourced-openai-consultants.md)

*Core argument:* The hard problems in agentic AI deployment are rooted in decades-old
software engineering principles. Nvidia's NemoClaw understands this. OpenAI and Anthropic,
by partnering with consultants, risk losing control of the narrative.

## NemoClaw vs. OpenAI/Anthropic

- OpenAI and Anthropic spent 2025 learning enterprises couldn't self-apply their tools
  (Codex, Claude Code); both labs responded by partnering with consulting firms
- Nvidia launched NemoClaw: enterprise wrapper on OpenClaw with YAML policy guardrails,
  model constraints (Nvidia serves the model), and local-first compute on Nvidia chips
- Strategic play: Jensen moving from chips to agentic ecosystem; OpenClaw developers
  indirectly add value to NemoClaw's enterprise proposition
- Key contrast: Anthropic/OpenAI assumed enterprises needed consultants; Jensen assumes
  developers are smart enough to self-apply good primitives

## Rob Pike's 5 Rules (Still Applicable to Agents)

1. Can't predict bottlenecks — don't speed-hack without proof
2. Measure before tuning; measure before assuming performance issues
3. Don't get fancy when numbers are small (simple scales better with LLMs absorbing edge
   complexity)
4. Fancy algorithms are buggier — simplicity is the debugging advantage
5. Data dominates — right data structures make algorithms self-evident

## 5 Hard Production Agent Problems

*1. Context Compression*
- Factory's anchored iterative summarization (sections: intent, file changes, decisions,
  next steps; incremental merge) outperformed OpenAI's opaque compact endpoint and
  Anthropic's full-regeneration approach
- All three struggle with artifact tracking (named files)
- Fix: milestone-based organization + multi-agent handoff to refresh context on long tasks

*2. Codebase Instrumentation*
- Software hygiene problem, not an agent problem
- Baseline latency and response quality with a golden test set
- Especially critical as autonomous agents gain more power

*3. Linting*
- Strict linting rules put agent code in a straitjacket of best practices
- Agents are lazy developers — they need external enforcement of simplicity
- Factory's obsessive linting regime is the model

*4. Multi-Agent Coordination*
- Industry converging on planners + executors pattern
- Do not over-complicate; build simplest pipeline first, measure before adding complexity

*5. Specifications and Fatigue*
- Defining specs upfront is hard but produces real speedups
- Clean context graph (navigable hierarchy) beats stuffed context window
- Humans must be less lazy for agents to perform well; "agents as labor savers" is
  disingenuous

## Factory.ai Agent Readiness Framework

- 8 pillars: style/validation, build systems, testing, docs, dev env, code quality,
  observability, security/governance
- Core finding: the agent is not the broken thing — the environment is
- Fixing env compounds: better environment → more productive agent → more time to improve
  env → virtuous cycle

## Key Takeaways

- Consultants sell complexity as new; it is not — these are ancient data engineering
  practices applied to agents
- Right change management: anchor in known principles, walk forward to today's specifics;
  get shoes dirty and co-build, not PowerPoint decks
- Convergence happening across Nvidia, Factory.ai, Anthropic, Microsoft on the same
  agentic rules of the road — Pike's rules rediscovered
- AI is just computing; the fundamentals are not new; the abstraction layer is new
