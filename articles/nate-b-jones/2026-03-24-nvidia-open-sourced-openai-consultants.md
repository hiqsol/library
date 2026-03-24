---
title: "Nvidia Just Open-Sourced What OpenAI Wants You to Pay Consultants For."
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=7AO4w4Y_L24
date: 2026-03-24 00:00
tags: ai, development, startups
---

# Nvidia Just Open-Sourced What OpenAI Wants You to Pay Consultants For.

## The Battle at the Heart of Agent World

There is a battle playing out between titans. On one side: Nvidia with NemoClaw. On the
other: OpenAI and Anthropic. They are all building agents — that is not the point. The
point is what they believe about the people who will use those agents.

Anthropic and OpenAI spent 2025 learning a painful lesson: the companies they worked with
did not have the expertise to actually apply the solutions they were delivering. They
launched Codex, Claude Code, and watched them suffer in production. Engineering teams at
real businesses could not adopt them at the speed Anthropic and OpenAI shipped internally.
The result: both labs publicly tied up with big consulting firms to bridge that gap.

## NemoClaw: Jensen's Agentic Play

Nvidia's NemoClaw came out of a different moment — the OpenClaw moment. Jensen watched
hundreds of thousands of developers pick up OpenClaw and said: the agentic operating
system is the future. His goal was to take that idea and bring it securely to the
enterprise, where raw OpenClaw is too open and too hard to lock down.

NemoClaw is built as an add-on to OpenClaw, not a replacement. It runs in OpenShell —
Nvidia's proprietary runtime — which wraps the OpenClaw instance with enterprise controls:

- *Policy-based guardrails* — YAML declarations the agent must follow
- *Model constraints* — validates safety and ensures Nvidia serves the model
- *Local-first compute* — designed to run efficiently on Nvidia chips

This is also a strategic business move. Jensen is shifting Nvidia from a chip layer play
to an agentic ecosystem play. Every OpenClaw contributor building in the open is
indirectly generating value in NemoClaw, which Nvidia can sell to enterprise.

## Two Philosophies on Enterprise Readiness

The key contrast: OpenAI and Anthropic concluded enterprises were not competent enough to
self-apply AI solutions and brought in consultants. Jensen walked on stage and said: you
developers are smart, you can figure this out — here is an open-source framework.

Nate argues Jensen's instinct is right, and roots it in something older: Rob Pike's five
rules of programming. Pike co-created Unix and Go. These rules are taught in CS programs
and by senior engineers for decades. They have not expired.

*Rule 1.* You cannot tell where a program will spend its time. Bottlenecks appear in
surprising places. Do not add speed hacks until you have proven that is where the
bottleneck is. This applies directly to agentic systems — it is very hard to predict
where things will break until you run them.

*Rule 2.* Measure. Do not tune for speed until you have measured, and even then only if
one part overwhelms the rest. Teams who do not baseline their agent performance before
making changes are flying blind. Measurement is not optional.

*Rule 3.* Fancy algorithms are slow when your number is small, and your number is usually
small. In agentic engineering: simple scales better than complex. A nuance here — LLMs
are increasingly absorbing the edge-case complexity that previously required fancy
algorithms, which means stable simple architectures scale even better now.

*Rule 4.* Fancier algorithms are buggier. Use simple algorithms with simple data
structures. The more you simplify, the easier debugging becomes. Complex agentic systems
are extremely hard to debug — is it the prompt? The context? The architecture? Simplicity
is your ally.

*Rule 5.* Data dominates. If you have chosen the right data structures and organized
things well, the algorithms will almost always be self-evident. Write dumb code, have
smart objects in your data system. This is the key insight for agentic engineering.
Data engineering quality determines agent quality.

## Five Hard Problems in Production Agent Deployment

Factory.ai's agent readiness framework evaluates codebases against eight pillars: style
and validation, build systems, testing, documentation, dev environment, code quality,
observability, and security/governance. Their core finding: consistently, the agent is
not the broken thing — the environment is.

### 1. Context Compression

Long-running agent sessions fill context windows, even million-token windows. Every
compression strategy is lossy. Factory tested three approaches:

- *Factory's anchored iterative summarization* — maintains a structured persistent summary
  with sections for session intent, file modifications, decisions, and next steps.
  Compression merges new truncated span with existing summary. Structure forces
  preservation.
- *OpenAI's compact endpoint* — opaque black-box compression optimized for faithful
  reconstruction but unverifiable.
- *Anthropic's Claude SDK built-in* — generates detailed structured summaries but
  regenerates the full summary every time, causing drift over repeated cycles.

Factory's incremental approach scored highest. All three struggle with tracking artifacts
(specific named files). Mitigation: organize work into milestones designed for
compression, and use multi-agent frameworks where agents die and refresh context without
losing state — enabling multi-week runs.

### 2. Codebase Instrumentation

This is a software hygiene problem, not an agent problem. Without a measured baseline —
latency, response quality, a golden test set — you cannot know if your agent is improving
or degrading. Engineers who build and maintain this baseline provide immense value even if
it is underappreciated. The discipline matters more now because autonomous agents have
significant power and are hard to audit without measurement.

### 3. Linting

Linting is static code analysis for style issues, inconsistencies, and potential runtime
bugs. Strict linting rules are how you enforce simple structures consistently. Agents are
lazy developers — they will take shortcuts and throw code off their plates if not
constrained. A strict linter that insists on simplicity is a primary safeguard. Factory
runs an obsessive linting regime that puts agent code in a straitjacket of best
practices. This is not new; it is an old discipline now essential for agentic quality.

### 4. Multi-Agent Coordination

The industry is converging on planners + executors as the pattern for long-running
multi-agent coordination. The principle: do not over-complicate it. Build the simplest
possible agentic pipeline. Measure whether it does the job before adding complexity. Do
not optimize prematurely. This is Pike's rules applied directly to orchestration
architecture.

### 5. Specifications and Fatigue

Teams consistently struggle to define specs clearly upfront. It is hard work, requires
precision and crystal-clear thinking, and demands discipline about not taking shortcuts.
The key insight: you have to keep your context graph clean so the agent can navigate a
hierarchy to find what it needs, rather than stuffing everything in the context window.
Humans have to be less lazy if they want agents to do good work. Agents are not labor
savers who let you drink coffee — that framing is disingenuous and sets teams up to
fail.

## The Consulting Problem

Consultants benefit from presenting AI complexity as entirely new. Complexity sells
engagements. Nate argues this is counterproductive because the actual hard problems in
agentic deployment rest on decades-old engineering best practices. Presenting them as
ancient truisms — which they are — lowers the barrier to adoption and anchors change in
things people already understand.

The right change management approach: anchor in what we know, then walk forward to show
how it applies today with specific detail. A PowerPoint deck about how AI is amazing does
not help engineers, product managers, and designers whose entire jobs are changing. You
have to get your shoes dirty and co-build.

Anthropic and OpenAI outsourcing change management to consulting firms risks losing
control of the AI narrative at exactly the moment when false rumors — about both what AI
can and cannot do — are already rampant.

## The Broader Signal

Nvidia's engineering culture — shaped by decades of optimizing close to the kernel and
the metal — produces engineers who take good principles seriously. That discipline is
visible in NemoClaw's design philosophy. Jensen's bet is that developers can self-apply
good engineering practices to build production agent systems, and that the right role for
a platform is to provide clear primitives and guardrails, not to abstract away
complexity.

This maps onto a broader pattern across Nvidia, Factory.ai, Anthropic's internal tooling,
and Microsoft's agent guidelines: a convergence on the same agentic rules of the road
that are Pike's rules rediscovered by people who know their fundamentals.

The takeaway: AI is just computing. The fundamentals are not changing. A new level of
abstraction has arrived, and the old engineering principles — measure before tuning, keep
data structures simple, let data dominate — are the right foundation to build on.
