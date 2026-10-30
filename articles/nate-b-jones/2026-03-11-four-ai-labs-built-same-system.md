---
title: 4 AI Labs Built the Same System Without Talking to Each Other
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=LO0Ws-l6brg
date: 2026-03-11 00:00
tags: ai
---

# 4 AI Labs Built the Same System Without Talking to Each Other

[summary](../../summary/nate-b-jones/2026-03-11-four-ai-labs-built-same-system.md)

**Abbreviations:**
- **LLM** — Large Language Model
- **PRD** — Product Requirements Document
- **PM** — Product Manager

---

## The Jagged Frontier Was Never a Property of Intelligence

Everyone has assumed that AI capabilities follow a jagged pattern —
incredible at some tasks, terrible at others. Experts talk about it, and it
has become the organizing frame for how we deploy, teach, and think about
AI. But there is a fundamental error in that assumption.

The jagged frontier was never an inherent property of AI intelligence. It
was an artifact of how we were asking AI to work. When you ask a model for
one answer in one turn, all of the variance in task difficulty shows up as
jaggedness in outcomes. We have been asking a capable analyst to solve every
problem in 30 seconds with no notes, no colleagues, no ability to try
something, and no ability to retry.

## How the Jaggedness Started to Smooth

That mental model was initially true in 2022, but things have moved forward.
With inference computing — what you get with ChatGPT 5.2 thinking and 5.2
Pro — the model can take time to decide, try approaches that don't work,
correct mistakes, and come back with higher-quality results. Most of the
conversation has focused on better performance, but the jaggedness itself
has been smoothing out. You don't have issues with counting the Rs in
"strawberry" anymore.

The mental model that shaped three years of AI strategy needs to change.
The last 30 days have made clear that jaggedness is no longer the right
guiding paradigm for AI in the workplace. AI may still be extraordinary at
some things and merely very good at others, but the last time anyone solved
an international Olympiad math problem at work was never. In the practical
world — PRDs, code, customer service tickets — AI is not jagged anymore.

## Why Single-Turn Interactions Fail

When you present a problem and the model produces a single response:

- If it contains an error midway through, that error propagates through
  everything that follows.
- If the first approach is wrong, there is no mechanism to detect that and
  try something else.
- If the task requires more information than fits in a context window, the
  model cannot accumulate it incrementally.
- Every problem must be solved in one shot.

This is not how any competent human professional works. A lawyer
researching a case, an engineer designing a system, a scientist running an
experiment — all involve trying things, recognizing when they aren't
working, adjusting, accumulating information over time, getting intermediate
feedback, and revising. The review processes, sprint cycles, peer feedback
loops, and draft-revise-publish pipelines that we built around professional
work exist because humans struggle with one-shot cognition too. We deployed
AI into a paradigm that stripped away all those structures, then described
the resulting limitations as a property of AI itself.

## Two Curves: Intelligence and Fluency

Since 2022, two things have been improving simultaneously. First,
intelligence has been climbing through inference scaling and reinforcement
learning. Second, our fluency at using the tool has been getting better —
putting agents into harnesses, using tools in loops for practical work. A
harness is the state around the agent: the scaffolding, the task markdown
file, the memory store, the environment it operates within. We have been
tracking the intelligence curve but not the fluency curve.

The fluency curve may matter more than the intelligence curve for practical
work right now. Figuring out the scale at which we can operate intelligence
is a function of our ability to use tools with agents and build effective
harnesses.

## The Cursor Proof: From Code to Mathematics

On March 3, Cursor CEO Michael Trule announced that Cursor had discovered
a novel solution to Problem 6 of the First Proof — a research-grade
mathematics problem drawn from unpublished work of Stanford, MIT, and
Berkeley academics. The model didn't just solve it; it improved on the
official human-written solution with stronger bounds and better coverage.
Because the work was unpublished, you cannot reinforcement-learn on it.

Cursor used the exact same coding harness that six weeks earlier had built
a web browser from scratch. The harness ran for 4 days on the math problem
with zero hints, zero human nudges, and zero mid-course guidance.

This matters because Cursor is not a mathematics company. A system designed
to write code looked at a problem in spectral graph theory and produced
mathematics that the problem's own authors hadn't found. The system found
an approach involving the Marcus-Spielman SVA interlacing polynomial
method — going beyond what humans had achieved.

As Trule put it: "This suggests that our technique for scaling agent
coordination might generalize beyond coding." Jones goes further: it
suggests that putting agents into harnesses for long-running work will
work for any domain that is even reasonably verifiable — where we can
determine a correct answer. That opens up not just math and code, but
legal work, customer service, and a surprising number of business
problems.

## Inside the Cursor Harness

In January, Wilson Lynn published a Cursor blog post on scaling
long-running autonomous coding. The first attempt used flat coordination:
agents shared a single file and used locks to avoid collision. It failed
badly. Agents became risk-averse, avoided difficult tasks, and optimized
for small, safe changes — lots of activity, no real progress.

The breakthrough came from hierarchy and specialization:

1. **Planners** explore the codebase and create tasks, spawning
   sub-planners recursively.
2. **Workers** pick up individual tasks and grind until done, ignoring
   everything else.
3. **A judge** (LLM-as-judge) determines whether to continue; the next
   iteration begins fresh.

The judge's ability to restart cleanly — bringing in a new agent with
fresh context — turned out to be one of the system's most important
properties, solving the context-window problem.

Test cases included building a web browser from scratch in Rust (agents
ran for a week, producing 1 million lines of code), a Solid-to-React
migration, a Java language server, a Windows 7 emulator (1.2 million
lines), and an Excel clone (1.6 million lines).

Two lessons emerged:

- **Model choice matters for long-horizon tasks.** GPT 5.2 consistently
  outperformed Claude Opus, which tended to stop earlier and take
  shortcuts.
- **Removing complexity beat adding it.** Many improvements came from
  stripping out complicated coordination machinery, adding hierarchy,
  and letting agents work in clean isolation.

The deepest observation: the system's behavior is disproportionately
determined by the design of the prompt. Prompting still matters.

## Four Labs, One Architecture

Four organizations — Anthropic, Google DeepMind, OpenAI, and Cursor —
have independently built multi-agent coordination systems for long-horizon
work. None coordinated with each other. All four exhibit the same
structural pattern:

1. **Decompose** the work.
2. **Parallelize** the execution.
3. **Verify** outputs.
4. **Iterate** toward completion.

**Anthropic's approach:** An initializer agent sets up environment state
and a progress file. A coding agent makes incremental progress and leaves
structured artifacts for the next session. Without this structure, the
agent might one-shot the whole implementation, run out of context mid-build,
leave things worse than it started, or mark features complete without
testing.

**Google DeepMind's approach** (especially the Althea mathematics model):
Separates generation, verification, and revision into distinct roles — the
same principle underlying code review, legal adversarial proceedings, and
scientific peer review.

**OpenAI's Codex:** Runs tasks in parallel sandbox environments.

**Cursor's planner-worker-judge:** Structurally similar to how software
teams with engineers and a PM actually operate.

This convergence is not coincidental. It solves a real problem: how do you
get useful work from units of intelligence with finite context, finite
per-step reliability, and no persistent memory? The answer — for both
human organizations and agent systems — turns out to be organizational.
Create roles, handoffs, verification, and restart procedures. These are
management insights that generalize to autonomous agents as naturally as
they generalize to human teams.

## The Cost Objection

Multi-agent harnesses are expensive. They generate enormous volumes of
tokens that a single-turn interaction would not. The cost is real, and you
have to be ready to enable token burn.

But multi-agent systems provide structural diversity that single agents
cannot achieve for hard problems:

- Parallel workers explore different decompositions of the problem.
- Dead-end results inform the next planning cycle without contaminating
  another worker's context.
- Planners can spawn sub-planners to go deep on specific sub-problems.
- Partial progress accumulates across context windows rather than
  resetting.

Certain problem classes are structurally inaccessible to serial cognition —
not because the individual lacks capability, but because the problem
requires too many exploratory paths to hold in working memory
simultaneously. This is exactly why we structure human organizations with
roles, handoffs, and verification rather than relying on one very smart
person.

## Two Tiers of Domain Verifiability

What makes work delegatable to agentic systems comes down to verifiability:

**Tier 1 — Machine-checkable:** The code compiles or it doesn't. Tests
pass or fail.

**Tier 2 — Expert-checkable with clear criteria:** Mathematical proofs,
engineering designs, legal briefs. In almost every field, experts look at
something and reach near-consensus on whether it is correct or incorrect.
This extends further than we typically assume. If you bring a product
strategy to three or four product leaders with 15-20 years of experience,
their assessment will be remarkably consistent. Work we traditionally call
"soft" is more verifiable than we think.

## What This Means for Work

The Anthropic 2026 agentic coding trends report describes engineers
delegating tasks where they can easily "sniff-check" on correctness. This
principle extends far beyond engineering. The best organizations are
delegating the hard work too — not just the simple stuff — as long as they
can sniff-check the output.

The skill that survives this transition is not "I can do the work." It is
"I can tell if the work is correct." Everything is moving to meta-skills:

- Knowing whether architecture is maintainable.
- Recognizing a fragile solution.
- Understanding when tests cover the important cases.
- Evaluating whether a strategy is sound.

These meta-skills become more valuable as harnesses improve, not less. The
question for every knowledge worker — financial modelers, legal
researchers, clinical trial designers, product managers, customer success
— is: what does sniff-checking look like in my domain? Evaluation
competency sits above execution competency in value, and becomes even more
valuable as execution gets cheaper with agents.

## The Central Lesson

The relevant question is shifting from "Can AI do a specific task in my
job family?" to "Can my work be decomposed into verifiable sub-problems?"
The answer is yes far more often than most of us are comfortable with.

Organizations that figure out how to make this productive will need much
more talent thinking about agent infrastructure, much more training around
taste and correctness evaluation, and much more capability in problem
decomposition. Installing this is hard. It takes a lot of people.

The capabilities are not jagged at work. That was a misunderstanding. We
scaled our organizational intelligence — the tools we built for
coordinating human work — into AI over the last 2-3 years. It hit a
tipping point. Anything at work that can be decomposed, parallelized,
verified, and iterated on is now within reach. That turns out to be a
huge share of knowledge work.
