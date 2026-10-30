---
title: Google Just Proved More Agents Can Make Things Worse
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=2EXyj_fHU48
date: 2026-01-26 14:00
tags: ai
---

# Google Just Proved More Agents Can Make Things Worse

[summary](../../summary/nate-b-jones/2026-01-26-google-just-proved-more-agents-can-make-things-worse-heres.md)

## The Multi-Agent Scaling Problem

The pitch for multi-agent AI systems is seductive: 10 or 100 agents
working on a task instead of one. And it does work — Cursor runs
hundreds of agents on tasks simultaneously, Steve Yegge's Gas Town
orchestrates 20 to 30 agents on sustained development work. But the
systems that scale do not look like what the frameworks recommend.

Gartner predicts 40% of agentic AI projects will be cancelled by
2027. The teams that fail will be the ones who built what LinkedIn
posts and X threads told them to build. The practitioners who have
actually scaled have converged on a completely different architecture.

## The Google-MIT Study

In December 2025, a study from Google and MIT found that adding more
agents to a system can make it perform worse — not diminishing
returns, but actual degradation. More agents, worse outcomes.

Key findings:

- Once single-agent accuracy exceeds about 45% on a task, adding more
  agents yields diminishing or negative returns
- In tool-heavy environments (10+ tools), multi-agent efficiency
  drops by a factor of 2 to 6 compared to single agents
- The intuition that "10 agents should finish 10x faster" does not
  hold because coordination overhead grows faster than capability

When you add agents, you add entities that need to coordinate. Every
coordination point is where agents wait for each other, duplicate
work, or create conflicts needing resolution. Past a threshold, 20
agents produce less output than 3 — 17 are effectively standing in
line.

## The Core Insight

**Simplicity scales because complexity creates serial dependencies,
and serial dependencies block the conversion of compute into
capability.**

The conventional wisdom — specialized agents collaborating like human
teams, integrating many tools, operating continuously, setting their
own sub-goals — works at small scale but fails at large scale in ways
frameworks do not warn about.

## Five Rules for Scaling Multi-Agent Systems

### Rule 1: Two Tiers, Not Teams

Cursor tested giving agents equal status with coordination through
shared files. Agents could check what others were doing and claim
tasks. Results: agents held locks too long, forgot to release them,
and spent most time waiting. 20 agents produced the output of 2-3.

Worse, with no hierarchy, flat teams became risk-averse. Agents
gravitated toward small, safe changes. Hard problems sat unclaimed
because claiming meant risking failure while other agents racked up
easy wins. Diffused responsibility meant nobody took responsibility.

**What works:** Strict two-tier hierarchy. Planners create tasks.
Workers execute them. A judge evaluates results. Workers do not
coordinate with each other — they do not even know other workers
exist. Each picks up a task, executes in isolation, pushes a change,
and terminates.

Yegge arrived at the same structure independently with Gas Town.
His "polecats" are ephemeral workers that spin up, execute, hand into
the merge queue, and get decommissioned. The "mayor" sits above
them creating and assigning work.

Research confirms: two-level systems significantly outperform both
flat architectures and deeper hierarchies (3+ levels accumulate drift
as objectives mutate through delegation layers — a game of telephone
with agents).

### Rule 2: Workers Stay Ignorant

When Cursor's workers understood broader project context, they
experienced scope creep — deciding adjacent tasks needed doing,
reinterpreting assignments, creating conflicts with other workers.

**What works:** Minimum viable context. Workers receive exactly enough
to complete their assigned task and no more. A worker that only knows
to implement one specific function cannot decide to refactor the
whole module. Narrow scope eliminates coordination needs and enables
parallel execution.

### Rule 3: No Shared State

The Google-MIT study found that tools are shared state in multi-agent
environments. Multiple agents accessing the same resources creates
contention, which requires coordination.

Tool selection accuracy degrades as count increases regardless of
context window size. Research shows degradation curves past 30 to 50
tools even with unlimited context. The problem is not fitting tools
in the window — it is that selection accuracy drops when agents face
too many choices.

**What works:** Workers operate in isolation with small tool sets (3-5
core tools always available, others discoverable on demand through
progressive disclosure). Coordination happens through external
mechanisms designed for concurrent access — Git for code, task queues
for non-technical work. Merging is handled by a dedicated system (in
Gas Town, "the refinery"), not by workers.

### Rule 4: Plan for Endings

The consensus says agents should operate continuously, accumulating
context over time. But context accumulation creates a serial
dependency with the agent's own past. As histories grow, context fills
with irrelevant information. This is why the RALPH framework for
Claude Code was significant — it wiped conversation context and gave
Claude Code a fresh start.

Cursor found drift unavoidable during continuous operation. Quality
degraded within hours. Specifications mutated as agents misremembered
earlier choices. The system experienced entropy — losing coherence.

Yegge built this into Gas Town with GUPP (Gas Town Universal
Propulsion Principle): sessions are ephemeral. Workers are chains of
tasks stored externally. When an agent ends, the next session picks
up from the same state the worker wrote to. The agent can crash,
restart, and make mistakes — it does not matter because workflow
state tracks progress externally.

**What works:** Episodic operation. Every cycle runs for a period,
captures results to external storage, then terminates. The next cycle
starts fresh with clean context.

### Rule 5: Prompts Over Infrastructure

Cursor found that a surprising amount of behavior comes down to
prompting, not coordination infrastructure. 79% of multi-agent
failures originate from spec and coordination issues, not technical
bugs. Infrastructure problems account for only 16%.

Sophisticated coordination infrastructure often adds serial
dependencies rather than removing them (message queues serializing
tool access, state synchronization requiring agreement before
proceeding).

**What works:** Treat prompts like API contracts. Good prompts and
good isolation reduce the coordination infrastructure needed. An
isolated agent with clear boundaries, clear success criteria, and no
need to check with other agents is simpler to prompt correctly.

## Where Complexity Should Live

There is an apparent contradiction: simplicity scales, yet Gas Town
is complex (seven worker types, patrols, convoys). The resolution:
complexity can live in agents or in the orchestration layer. These
have very different scaling properties.

- **Complexity in agents** works at small scale (3-5 agents) but
  creates serial dependencies that break at larger scales
- **Complexity in orchestration** enables parallelism — Gas Town has
  separate agents for noticing stuck workers, merging conflicts,
  tracking progress

The intuition that making agents smarter pushes intelligence to
workers and scales capability is wrong. The architecture that scales
keeps workers dumb. The investment should go into orchestration, not
agent intelligence.

## The Implication for 2026

Teams that win will absorb the tremendous increase in available
compute by adding agents and getting proportional throughput gains
instead of coordination collapse. The goal is not one brilliant agent
running around for a week — it is 10,000 dumb agents, well
coordinated by the system, running for an hour at a time,
progressively completing work against tight goal definitions.

The teams who understand this will outproduce teams that do not by a
factor of 100.
