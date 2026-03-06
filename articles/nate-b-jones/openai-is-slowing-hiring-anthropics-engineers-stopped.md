# OpenAI Is Slowing Hiring, Anthropic's Engineers Stopped Writing Code

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=dZxyeYBxPBA)
- **Author:** Nate B Jones
- **Date:** ~January 2026

---

## The Paradox: Capability Jumped, Adoption Has Not

Sam Altman confessed recently that despite being CEO of OpenAI, having the
best access to the most capable AI tools, and his own data showing AI now
beats human experts on 3/4 of well-scoped knowledge tasks — he still has
not really changed how he works. He admitted: "I know that I could be
using AI much more than I am."

Meanwhile, Andrej Karpathy, who helped build OpenAI, says his workflow
has inverted in just a couple of weeks: from 80% manual coding to 80% AI
agents. Ethan Mollick at Wharton puts it bluntly: "Projects from 6 weeks
ago may now already be obsolete."

The capability is there. The adoption is not.

## What Happened in December 2025

The shift was not one thing — it was a convergence of model releases,
orchestration patterns, and proof points crossing thresholds in the same
compressed window.

### The Models

In just 6 days, three frontier releases landed:

- Google's Gemini 3 Pro
- OpenAI's GPT 5.1 Codex Max (then 5.2 soon after)
- Anthropic's Claude Opus 4.5

All are explicitly optimized for sustained autonomous work over hours or
days rather than minutes. GPT 5.1/5.2 models are designed for continuous
operation over a day. Opus 4.5 introduced an effort parameter for dialing
reasoning up or down, priced 2/3 cheaper than its predecessor. Context
compaction from both OpenAI and Anthropic lets models summarize their own
work as sessions extend, maintaining coherence over longer timeframes.

Reports from the Cursor team and others: models can do a week of work
autonomously and code up to 3 million lines before coming back.

### The Orchestration Patterns

**RALPH** (named after the Simpsons character): Jeffrey Huntley, an
open-source developer in rural Australia, wrote a bash script that runs
Claude Code in a loop. Git commits and files serve as memory between
iterations. When the context window fills, a fresh agent picks up where
the last left off.

The insight is embarrassingly simple: a loop that keeps running until
tests pass is more reliable than carefully choreographed agent handoffs.
Venture Beat called it "the biggest name in AI right now."

**Gas Town** by Steve Yagi (January 1st): A maximalist workspace manager
spawning dozens of AI agents in parallel. Both patterns share the same
core insight — the bottleneck has shifted. Your productive capacity is
now limited only by your attention span and ability to scope tasks well.

**Claude Code's Task System** (late January): Native infrastructure that
made RALPH look like a clever workaround. Each task spawns its own sub-
agent with a fresh 200K-token context window, isolated from the main
conversation. 7-10 sub-agents running simultaneously. When a task
completes, blocked tasks automatically unblock.

Key innovation: dependencies are structural, not cognitive. Without them,
the model holds the entire plan in working memory where it degrades.
Externalizing the dependency graph means the graph never forgets and never
drifts.

## The Self-Acceleration Loop

At Davos, Dario Amodei described the most important dynamic in AI: the
self-acceleration loop. "I have engineers at Anthropic who tell me, I
don't write code anymore. I let the model write the code."

Anthropic is accelerating the production of the next AI systems using AI.
AI has entered a self-acceleration loop.

This is why OpenAI is slowing hiring. Altman announced plans to
dramatically slow hiring because of the capabilities and span AI gives
existing engineers. New hire expectations: "We're asking them to do
something that would normally take weeks using AI tools in 10 or 20
minutes."

## The GDP-Val Benchmark

OpenAI's GDP-val measures how often AI output is preferred over human
expert output on well-scoped knowledge work:

| Model             | Win Rate vs. Humans |
|--------------------|---------------------|
| GPT Thinking (fall)| 38%                 |
| GPT 5.2 Pro        | 74%                 |

On three-quarters of scoped knowledge tasks, AI is now preferred. As
Altman put it: "If you can assign your co-workers something that takes an
hour and get something better than what a human would do 74% of the time
in vastly less time, it's pretty extraordinary."

## The Capability Overhang

Capability has jumped far ahead of adoption. Most knowledge workers still
use AI at a ChatGPT-3.5/4 level: ask a question, get an answer. They are
not running agent loops overnight, assigning hour-long tasks, or managing
fleets of parallel workers.

Someone running task loops with RALPH is living in a different technical
reality than someone who queries ChatGPT four or five times a day — even
though they have access to the exact same underlying tools. This creates
a temporary arbitrage for those who figure out the new patterns first.

## Skills of Power Users

1. **Assign tasks, do not ask questions.** Shift from treating AI as an
   oracle to declarative specification: describe the end state, provide
   success criteria, let the system figure out how.

2. **Accept imperfection and iterate.** RALPH works because it embraces
   failure. The AI produces broken code, so you make it retry. It never
   gets tired. You go make lunch and come back to finished work.

3. **Invest in specification and review, not implementation.** Less time
   writing code. Much more time defining what you want. Much more time
   evaluating whether you got there. Most engineers spent years developing
   implementation intuitions that are now less useful. The new skills:
   describe systems precisely enough for AI to build them, write tests
   capturing real success criteria, and review AI code for subtle
   conceptual errors.

4. **Run multiple agents in parallel.** Some developers go from a few PRs
   per day to dozens. The constraint moves from coding to coordination.

5. **Let agents run all the time.** Define work, start the loop, go to
   bed. Proper guardrails needed, but productive hours become 24/7.

6. **Actually try it.** The main barrier. Most people have not run an
   agent loop for more than a couple of minutes. If you have not
   revisited your workflow since December, you are operating on stale
   assumptions.

## The Quality of Agent Errors

Karpathy noted that current model errors are not simple syntax mistakes.
They are the same conceptual errors a hasty junior developer would make:
wrong assumptions, running without checking, failing to surface
trade-offs. These are supervision problems, not capability problems. The
solution is better management skills, not doing the work yourself.

Maggie Appleton (designer): "When agents write the code, design becomes
the bottleneck." The questions that slow you down are less about code
syntax and more about architecture, user experience, composability.

## Speed as a Foot Gun

You can move extremely fast with AI agents and forget how much garbage
you are producing. If you are not thinking through what you want, the
speed leads to quickly building a giant pile of useless code. This is a
superpower everyone has been handed — we are about to see who can
actually think well.

## Where Engineers Should Stand Relative to Code

The answer depends on what you are building:

- **Low risk tolerance:** Watch the agent in an IDE, write evals
  carefully
- **Front-end code:** More complex than backend because defining visual
  output remains a challenge
- **Green-field prototypes:** You really can step back

Technical leaders should set explicit policy per codebase based on risk
profile, rather than leaving it as a free-for-all.

## The Shape of Work Is Changing

The December convergence established a new baseline: models maintain
coherence for days, orchestration manages agent fleets, and the economics
work. If Amodei is right that AI can handle end-to-end software
engineering within 6-12 months, the gap between current practice and full
automation has never felt larger.

> The future belongs to people who know how to handle the speed
> responsibly and be thoughtful with it. Every single agent you can run
> in parallel multiplies your productivity. If you are not running a
> dozen agents doing autonomous tasks for days at a time, you are behind.
