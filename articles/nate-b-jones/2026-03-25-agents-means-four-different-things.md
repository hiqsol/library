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

# "Agents" Means 4 Different Things and Almost Nobody Knows Which One
They Need.

## The Problem: One Word, Four Species

We want agents, but we do not know what we really want. Saying "an AI
plus tools in a loop" is technically true but misses the point.
Sophisticated agents diverge into at least four distinct types, and
most people confuse them — then use the wrong kind for the wrong kind
of work. This video lays out the four species, explains why they are
different, and gives a cheat sheet for picking the right one.

The four species:

1. **Coding harnesses** — single-agent or multi-agent systems for
   producing software
2. **Dark factories** — fully autonomous pipelines that take a spec
   and output evaluated software with minimal human involvement
3. **Auto research** — LLM-driven optimization against a metric,
   descended from classical machine learning
4. **Orchestration** — multi-LLM workflows with specialized roles and
   handoffs

All four share the same primitive: LLM + tools + loop. The
construction around that primitive is what makes each species
fundamentally different.

## Species 1: Coding Harnesses

### Individual-Level Harnesses

The simplest agentic pattern. An agent takes the place of a developer
in an engineering process. The agent can read files, write files, call
tools, search — it has the same capabilities a developer would. The
human plays a managerial function; the agent does the coding.

Andre Karpathy runs agents 16 hours a day on single-threaded tasks.
That is not unusual in 2026. Peter Steinberger, building OpenClaw,
described managing multiple Codex agents simultaneously, each
completing a decomposed task in about 20 minutes before checking back
in.

The key enabler: **decomposition**. If you can break a gnarly problem
into well-defined chunks, you can hand each chunk to a single-threaded
agent and get far. Developers who are good at this spend their day as
managers of single-threaded agents.

### Project-Level Harnesses

When work exceeds what one developer can hold in their head — say, a
team of 8 or 16 or 20 — individual harnesses create bottlenecks.
Code review piles up. Humans struggle to manage four things at once.

Cursor demonstrated the project-level approach across real projects
(browsers, compilers, millions of lines of code). The architecture:

- A **planner agent** that acts as manager — tracking tasks, keeping
  memory, evaluating whether executor work is done well
- **Short-running executor agents** spun up by the planner to solve
  exactly one problem each

Cursor tried adding three levels of management. It did not work.
**Simple scales well with agents.** The planner-executor pattern with
one level of hierarchy is the sweet spot.

The counterintuitive shift: instead of framing everything around the
human at the center, frame it around making it easy for the agent to
do the work. Individual assistants speed up humans but preserve all
existing bottlenecks. Project-level harnesses remove those
bottlenecks.

## Species 2: Dark Factories

Dark factories push human involvement to the extreme ends: heavy at
the beginning (design, spec, intent) and heavy at the end (eval,
production readiness). The middle is fully automated.

Why? Agents push work through so fast that humans become bottlenecks
in the middle. Dark factories are designed to eliminate that strain.

The architecture:

- Put in a specification
- Agents iterate autonomously
- System hits an eval/test gate at the end
- Iterates back automatically until software passes
- Optionally: human reviews code before production

Amazon learned the hard way about skipping human review — they called
senior and principal engineers to Seattle to discuss AI-generated
incidents in production caused by junior engineers.

The spectrum from coding harness to dark factory is a gradient:

- **Individual harness**: human judgment is the quality gate
  throughout
- **Project harness**: human at beginning and end, some guidance in
  middle
- **Dark factory**: human only at spec and eval; middle is autonomous

Most companies that claim dark factory still have humans review the
eval output. That hybrid — mostly dark factory with human eval at the
end — is often the most practical approach.

## Species 3: Auto Research

Auto research is a fundamentally different bug. It is not about
producing software — it is about **optimizing a metric**.

It descends from classical machine learning: teach a machine to get
better and better at a target through experimentation (hill climbing).

Examples:

- **Toby Lütke (Shopify)**: optimized the Liquid template framework
  that powers millions of shops — metric was runtime performance
- **Andre Karpathy**: released auto research to optimize LLM training
  at GP-2 scale — proving the concept that you can auto-research your
  way through an LLM development chain
- **Conversion optimization**: optimizing landing page conversion
  rates, or any rate-shaped metric

The critical distinction: **if you do not have a metric, you are not
doing auto research.** Your problem is either software-shaped
(build it) or metric-shaped (optimize it). These are usually
intuitive once framed this way.

Auto research forks are already emerging that let you ask optimization
questions in plain English.

## Species 4: Orchestration

Orchestration handles multiple distinct jobs with specialized agents
and handoffs between them. Writer → editor, researcher → drafter,
ticket pickup → research → resolution → close.

This is different from the planner-executor pattern in coding
harnesses. Coding harnesses work toward one unified goal.
Orchestration gives agents genuinely different specialized roles.

Platforms: LangGraph, Crew AI.

The challenge: orchestration has many joints where humans must
intervene. The handoff management is expensive — prompts, context
management, coordination. It is the most complicated species to set
up.

**Scale determines viability.** For 10,000 customer success tickets,
orchestration is clearly worth the investment. For 100 tickets, it
probably is not. Always ask whether the coordination overhead is worth
the scale you are operating at.

## The Cheat Sheet

| If you are optimizing for…         | Use…                           |
|------------------------------------|--------------------------------|
| What is in front of you            | Coding harness (individual)    |
| Project-scale output               | Coding harness (project-level) |
| Autonomous spec-to-production      | Dark factory                   |
| A rate or metric                   | Auto research                  |
| Workflow routing between roles     | Orchestration                  |

## Common Mistakes

- Using auto research to build software — wrong species
- Using a long-running coding harness to write a novel —
  that is an orchestration problem (or a human task)
- Treating a single-agent harness as a dark factory — you need the
  full eval pipeline
- Mixing species without understanding which problem shape you have

## Key Insight

The four species look similar on the surface — they all use LLM +
tools + loop. The difference is in construction: how much human
involvement, where the human sits, what the optimization target is,
and how handoffs work. Getting this taxonomy right is the difference
between agents that work and agents that create big trouble.
