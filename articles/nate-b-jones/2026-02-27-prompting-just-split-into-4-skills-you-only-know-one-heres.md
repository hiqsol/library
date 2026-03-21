---
title: Prompting Just Split Into 4 Skills — Here's Why You Need All of Them in 2026
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=BpibZSMGtdY
date: 2026-02-27 15:00
tags: ai
---

# Prompting Just Split Into 4 Skills — Here's Why You Need All of Them in 2026

## What Changed

The prompting skill that mattered since 2024 was conversational: sit in a
chat window, type a request, read the output, iterate, get better at phrasing.
That skill has a ceiling, and in early 2026 many people are hitting it because
models have stopped being chat partners and started being workers — workers
that run for days and sometimes weeks.

Opus 4.6, Gemini 3.1 Pro, and GPT-5.3 Codex have all shipped with autonomous
agent capabilities that make chat-based prompting functionally obsolete for
serious work. Between October 2025 and January 2026, the longest autonomous
Claude Code sessions nearly doubled, and they have doubled again since then.
Telus reports 13,000 custom AI solutions internally. Zapier reports over 800
agents internally.

Everything you relied on in conversation — catching mistakes in real time,
providing missing context when asked, course-correcting when things drift —
must now be encoded before the agent starts. This is a fundamentally different
skill, not a harder version of the same skill.

## The 10x Gap on a Random Tuesday

Two people sit down with the same model, same subscription:

**Person A (2025 skills):** Types a request for a PowerPoint deck. Gets back
something 80% correct. Spends 40 minutes cleaning it up. Happy because it
would have taken 2-3 hours.

**Person B (2026 skills):** Writes a structured specification in 11 minutes.
Hands it off to the same model used as an autonomous agent. Makes coffee.
Comes back to a completed deck hitting every quality bar. Does this for five
more decks before lunch — a week's worth of work in a morning.

Same model, same Tuesday, 10x gap.

## Toby Lutke on Context Engineering

Shopify CEO Toby Lutke maintains a personal folder of prompts he runs against
every new model release, systematically probing capabilities like a QA
engineer running unit tests. He uses the term "context engineering": the
ability to state a problem with enough context that the task becomes plausibly
solvable without the agent going out for more information.

Lutke observed that by being forced to provide AI with complete context, he
communicates better as a CEO — tighter emails, better memos, stronger decision
frameworks. His most provocative assessment: a lot of what people in big
companies call politics is actually bad context engineering for humans.
Shared context that people assume exists often doesn't, and that gap plays
out as grudges and politics.

## The Four Disciplines

These build on each other. If you skip one, you create the kind of failures
seen at scale in the enterprise. They operate at different altitudes and
time horizons. As you progress up the hierarchy, failure becomes more serious
— from wasting your morning to damaging your entire company.

### Discipline 1: Prompt Craft

The original skill. Synchronous, session-based, individual. Structure a query
with clear instructions, relevant examples, appropriate guardrails, explicit
output format, and clear ambiguity resolution.

Prompt craft has not become irrelevant — it has become table stakes. Like
knowing how to type with 10 fingers: once a differentiator, now just assumed.
If you cannot write a clear, well-structured prompt in 2026, you are the
person in 1998 who couldn't send an email.

Prompt craft was the whole game when AI interactions were synchronous and
session-based. You acted as the intent layer, the context layer, and the
quality layer. That model broke the moment agents started running for hours
without checking in.

### Discipline 2: Context Engineering

The set of strategies for curating and maintaining the optimal set of tokens
during an LLM task. Anthropic published the foundational piece in September
2025. LangChain's Harrison Chase said: "Everything is context engineering.
It actually describes everything we've done at LangChain without knowing the
term existed."

Context engineering is the shift from crafting a single instruction to
curating the entire information environment an agent operates within: system
prompts, tool definitions, retrieved documents, message history, memory
systems, MCP connections. Your 200-token prompt is 0.02% of what the model
sees. The other 99.98% is context engineering.

This discipline produces CLAUDE.md files, agent specifications, RAG pipeline
design, memory architectures. People who are 10x more effective are not
writing 10x better prompts — they are building 10x better context
infrastructure.

### Discipline 3: Intent Engineering

Context engineering tells agents what to know. Intent engineering tells agents
what to want. It is the practice of encoding organizational purpose — goals,
values, trade-off hierarchies, decision boundaries — into infrastructure that
agents can act against.

The Klarna case is the proof. Their AI agent resolved 2.3 million customer
conversations in the first month, but optimized for resolution speed instead
of customer satisfaction. Klarna had to rehire human agents and is still
dealing with the customer trust aftermath.

Intent engineering sits above context engineering the way strategy sits above
tactics. You can have perfect context and terrible intent alignment. You
cannot have good intent alignment without good context.

### Discipline 4: Specification Engineering

The practice of writing documents that autonomous agents can execute against
over extended time horizons without human intervention. This is about thinking
of your entire organizational document corpus as agent-readable.

Anthropic's team struggled with Opus 4.5 building a production web app. A
high-level prompt like "build a clone of claude.ai" caused the agent to do
too much at once, run out of context mid-implementation, and leave the next
session guessing. The fix was not a better model — it was specification
engineering: a laser agent sets up the environment, a progress log documents
what's been done, and a coding agent makes incremental progress against a
structured plan each session.

The smarter models get, the better you need to get at specification. Your
corporate strategy is a specification. Your product strategy is a
specification. Your OKRs are a specification. Everything becomes a
specification your agent can use.

One-person businesses have the greatest advantage: just convert your Notion
to be agent-readable and you're off to the races.

## Five Primitives to Learn

### 1. Self-Contained Problem Statements

Can you state a problem with enough context that the task is plausibly
solvable without additional information? This surfaces hidden assumptions
and makes you articulate constraints normally left implicit.

**Practice:** Take a conversational request ("update the dashboard to show
Q3 numbers") and rewrite it as if the receiver has never seen your dashboard,
doesn't know what Q3 means in your context, and has no access to anything
you don't include.

### 2. Acceptance Criteria

If you cannot describe what "done" looks like, an agent cannot know when to
stop. "Build a login page" vs. "Build a login page that handles email/password,
social OAuth via Google and GitHub, progressive disclosure of 2FA, session
persistence for 30 days, and rate limiting after five failed attempts."

**Practice:** For every delegated task, write three sentences an independent
observer could use to verify output without asking you questions.

### 3. Constraint Architecture

What the agent must do, must not do, should prefer when multiple valid
approaches exist, and should escalate rather than decide. These four
categories form the constraint architecture that turns a loose specification
into a reliable one.

The best CLAUDE.md files are concise, extremely high-signal constraint
documents. Every line must earn its place.

### 4. Decomposition

Large tasks broken into components that can be executed, tested, and
integrated independently. Anthropic's long-running agent harness splits
projects into environment setup, progress documentation, and incremental
coding sessions — each independently verifiable.

**Practice:** Take a multi-day project, decompose into sub-tasks each taking
less than 2 hours, with clear input/output boundaries and independent
verification. Your job increasingly is not to write the sub-tasks but to
provide the break patterns a planner agent can use to decompose reliably.

### 5. Evaluation Design

How do you know the output is good? Not "does it look reasonable" but "can
you prove measurably, consistently, that this is good?" Build 3-5 test cases
with known good outputs for every recurring AI task. Run them periodically,
especially after model updates.

## The Human Communication Benefit

The best human managers already operate with this clarity: complete context
when delegating, specified acceptance criteria, articulated constraints. AI
is enforcing a communication discipline the best leaders always practiced
intuitively — and now everyone needs it.

The skill of providing high-quality input to intelligent systems turns out
to be translatable for AIs and humans alike. The prompt by itself is dead.
The specification, the context, the organizational intent — that is where
the value is moving. Because agents work for longer periods and increasingly
look like junior employees, the specification done right turns out to be
just what clear thinking has always looked like, made explicit because
machines don't let us be lazy about it.
