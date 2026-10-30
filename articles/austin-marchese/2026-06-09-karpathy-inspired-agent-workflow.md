---
title: "A Better Way to Work With AI Agents—Without Inventing a “Karpathy Method”"
author: Austin Marchese
channel: Austin Marchese
url: https://youtu.be/7zZy1QTvokM?is=VWe3HfSD_NFgsRxg
date: 2026-06-09 16:00
tags: ai, development
---

# A Better Way to Work With AI Agents—Without Inventing a “Karpathy Method”

[summary](../../summary/austin-marchese/2026-06-09-karpathy-inspired-agent-workflow.md)

Austin Marchese’s video offers a useful way to organize work with AI agents.
Its three parts—specification, verification, and environment—form a practical operating model.
But the title, “Stop Prompting Claude. Use Karpathy’s Method Instead,” overstates its source.
Andrej Karpathy did not tell viewers to stop prompting Claude.

He did not name a “Karpathy method,” define those three layers, or promise a 10× gain.
The framework is better understood as Marchese’s synthesis, inspired by Karpathy’s ideas.
That distinction does not make the workflow less useful.
It makes it easier to judge each part on its merits.

## What Karpathy actually argued

At Sequoia AI Ascent 2026, Karpathy described a shift from casual “vibe coding” to
professional “agentic engineering.”
The professional remains responsible for whether the system is coherent, secure, and useful.
In his own [edited account of the talk](https://karpathy.bearblog.dev/sequoia-ascent-2026),
he says agents are fallible and stochastic and need human oversight.
He also argues for working with an agent to produce a detailed specification.
That is more substantial than asking for a plan and then treating the plan as settled.

His point is not that Claude’s plan mode is worthless.
He explicitly calls it useful while saying the deeper task is collaborative specification.
A second authentic theme is uneven, or “jagged,” capability.
Karpathy’s car-wash example asks whether to walk or drive to a car wash 50 metres away.

A model may answer “walk” because the destination is close while missing that the car must go.
The anecdote illustrates a real class of failure: fluent reasoning can omit obvious context.
It does not establish that every current model fails, or that context is beyond AI in general.
Marchese says Claude, Gemini, Grok, and ChatGPT all answered incorrectly in his test.

The video does not provide model versions, settings, full prompts, or captured outputs.
That makes the test an anecdote, not a reproducible comparison.
Karpathy’s broader claim is more careful.
In his essay on [verifiability](https://karpathy.bearblog.dev/verifiability), he argues that
AI advances fastest where answers can be checked cheaply and repeatedly.

Code can be tested.
Games expose scores.
Many mathematical results can be checked mechanically.
Everyday judgment often lacks an equally crisp feedback signal.

Training priorities and available data also matter, so verifiability is not the whole story.
A third theme is the danger of anthropomorphism.
In [“Animals vs. Ghosts”](https://karpathy.bearblog.dev/animals-vs-ghosts), Karpathy describes
LLMs as engineered statistical distillations rather than animal minds.
Pleading with a model or threatening it is not a substitute for evidence and feedback.

Marchese’s “robot librarian” analogy is his own simplification, not Karpathy’s terminology.
Finally, Karpathy emphasizes understanding.
In the talk, he repeats a line he attributes to a tweet that affected him deeply:

> You can outsource your thinking, but you can’t outsource your understanding.

The line should not be presented as his original coinage.
His application of it is still important: people must know what they are building and why.

## The attribution problem

The video turns those observations into a tidy three-layer architecture.
That architecture consists of a spec, a verifier, and an environment.
It is a coherent editorial package, but it is not a framework Karpathy presented by that name.
The “stop prompting Claude” command is also Marchese’s packaging.

Karpathy’s talk concerns agents and agentic engineering broadly, not a rejection of prompting.
The claimed “10×” improvement has no benchmark, baseline, or controlled comparison behind it.
Karpathy says agentic work can move faster, but does not report that multiplier.
Speed also is not equivalent to delivered value.

A system can produce more drafts or code while increasing review, rework, or operational risk.
Any productivity claim must include the quality bar, full workflow cost, and outcome measured.
The same caution applies to the video’s “2–3× quality” claim.
Boris Cherny did write that a feedback loop can “2-3x” Claude’s result quality in a
[practitioner thread](https://www.threads.com/@boris_cherny/post/DTBVvvhEnnW/).

But the statement is experience-based advice, not a published experiment with a defined metric.
Treat the number as a heuristic pointing toward feedback, not a universal expected return.

## Layer one: turn intent into a specification

Marchese’s first layer begins with a sound observation: a task is not necessarily the goal.
“Create an end-of-month report” identifies an output.
It does not identify the decision the report should support or the audience it must persuade.
His suggested remedy is to have the agent interview the user before drafting.

That interview can surface purpose, constraints, source material, exclusions, and trade-offs.
This is Marchese’s implementation advice, not a prompt quoted from Karpathy’s talk.
A useful specification might answer:

- What decision or user outcome should this work support?
- Who will use it, and under what conditions?
- Which evidence and systems are authoritative?
- What is explicitly outside scope?
- Which choices require human approval?
- What tests or review criteria define acceptance?

The interview is not a transfer of responsibility.
A model can propose goals, but the accountable stakeholder must confirm the intended one.
The next move is to divide work into reviewable increments.
Marchese calls this “agile spec’ing”: narrow the scope, stop, inspect, adjust, and continue.

That label and procedure are his synthesis.
Still, the loop is useful when an early wrong assumption would contaminate later work.
Small checkpoints make hidden disagreements visible before they become expensive to unwind.
They also create opportunities to revise the spec as genuine new information appears.

Not every task needs many checkpoints.
Excessive fragmentation can add overhead and make the agent lose the shape of the whole.
Use checkpoints where a decision is consequential, ambiguous, or hard to reverse.
The final practice in this layer is explicit approval of key decisions.

The agent can list assumptions and ask the user to confirm the important ones.
That is stronger than asking it to “be careful,” because it produces inspectable choices.
The specification should remain a living agreement, not a decorative preamble.

## Layer two: build verification around the real objective

Marchese’s second layer asks a better question than “Does this look good?”
What evidence would justify accepting the result?
A report rubric might require three sections and a recommendation after each one.
Those rules are testable, but they verify structure rather than truth or decision quality.
A passing rubric can still certify the wrong thing.

Good evaluation therefore mixes several kinds of evidence:

- deterministic checks for syntax, schemas, calculations, and invariants;
- comparison with primary sources or approved reference material;
- execution in the target system rather than self-reported success;
- expert review for judgment, taste, safety, and context;
- user-facing tests tied to the actual intended outcome.

Marchese also recommends using a second model as a critic.
There is some conceptual support in Karpathy’s talk for multiple LLM judges.
OpenAI also publishes a [Codex plugin for Claude Code](https://github.com/openai/codex-plugin-cc)
that can perform regular or adversarial review.
A critic model can find omissions, generate counterexamples, and challenge assumptions.

Agreement between two models, however, is not verification.
They may share training data, conventional assumptions, or the same blind spot.
Ask the critic to cite evidence and test claims, not merely vote on the answer.
External signals are stronger than model self-assessment when the signals match the objective.

For a deployment, inspect the exact revision and run health and smoke tests.
Check logs and user-visible behavior, not only whether a deployment command returned success.
For a report, compare figures with the source system and format with approved examples.
No single connection creates certainty.

A check can be stale, partial, misconfigured, or aimed at the wrong target.
Verification earns confidence in proportion to the coverage and independence of its evidence.

## Layer three: design a persistent working environment

The third layer moves recurring context out of one-off prompts and into maintained systems.
For Claude Code, one mechanism is `CLAUDE.md`.
Anthropic’s [memory documentation](https://code.claude.com/docs/en/memory) describes these files
as persistent instructions loaded by session and scope.
They are not necessarily reinjected in full on every prompt, as the video claims.

They are also context, not an enforcement boundary.
A concise project file can document repository structure, commands, conventions, and rules.
Long procedures are better placed in focused skills or scoped rules.
Anthropic’s [skills documentation](https://code.claude.com/docs/en/skills) recommends reusable
skills for workflows and checklists that would otherwise be pasted repeatedly.

A skill does not improve merely because it runs.
Improvement requires someone to capture a failure, revise the procedure, and test it again.
Marchese also connects the environment to a personal knowledge base.
Karpathy’s actual [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
keeps raw sources, an LLM-maintained linked Markdown wiki, and an instruction/schema layer.

Files used as retrieval context are not “training data” in the model-weight sense.
The distinction matters because retrieval does not teach the base model or guarantee recall.
A maintained knowledge system can improve traceability and reuse.
Its value depends on source quality, update practices, permissions, and retrieval accuracy.

## Instructions are not guardrails

One of the strongest practical distinctions in the video is soft guidance versus enforcement.
Writing “never edit this folder” in `CLAUDE.md` expresses an instruction.
It does not make writing technically impossible.
Anthropic documents [PreToolUse hooks](https://code.claude.com/docs/en/hooks) that can deny
matching tool calls before they execute.

That can be a useful control, but it is only as strong as its coverage and integrity.
A hook may miss shell writes, alternate tools, symlinks, or paths it does not canonicalize.
Its configuration may itself be editable unless protected outside the agent’s authority.
Hard boundaries should combine narrow credentials, OS permissions, sandboxing, and fail-closed
controls where the cost of error warrants them.

Marchese’s “always do / ask first / never do” buckets are a useful starting policy.
They are his risk model, not a Karpathy taxonomy.
“Always do” should cover low-impact, reversible, observable actions.
“Ask first” should cover costly, external, ambiguous, or difficult-to-reverse actions.

“Never do” should be enforced outside the prompt whenever violation would be unacceptable.

## A safer implementation of the workflow

Start with a short intent interview.
Write the accepted objective, constraints, sources, exclusions, and owner of each decision.
Break the work only at points where review can change the trajectory.
Define acceptance checks before execution, including checks for substance and not just format.

Give the agent access only to the tools and data required for the current scope.
Run deterministic tests and inspect external state after consequential actions.
Use another model to search for defects, not to declare the result true by consensus.
Route high-impact decisions to a named human reviewer.

Store stable project knowledge in maintained files with provenance and update dates.
Turn repeated procedures into versioned skills, then revise them when failures reveal gaps.
Enforce prohibited actions at the tool, permission, or sandbox layer.
Measure outcomes such as correctness, rework, incidents, user impact, and total cycle cost.

Do not infer value from token volume, code volume, task count, or speed alone.

## What to keep—and what to discard

Keep Karpathy’s insistence on detailed specifications and human responsibility.
Keep his emphasis on verifiability, empirical familiarity, and skepticism toward fluent output.
Keep the warning that these systems are not motivated colleagues in software form.
Keep Marchese’s practical prompts, checkpoints, critics, references, skills, and guardrails where
those techniques fit the task and risk.

Discard the idea that model agreement equals truth.
Discard the claim that a tool connection produces certainty.
Discard the suggestion that instruction files are hard security controls.
Discard the 10× promise unless a defined workflow is measured against a real baseline.

Most importantly, discard the false choice between “prompting” and “the Karpathy method.”
The practical shift is from isolated requests to managed work systems.
Those systems combine intent, evidence, tools, review, memory, and enforceable limits.
That is Marchese’s useful synthesis of several ideas, not a method Karpathy named.
Clear attribution preserves the lesson rather than weakening it.

## Caption caveat

The supplied transcript comes from automatic captions and may contain recognition errors,
omissions, lost capitalization, and incomplete text for prompts shown only on screen.
Notable risks include the event name, personal names, `CLAUDE.md` capitalization, and missing
words in several transitions.
Quotations and technical details above were therefore checked against the primary sources below.

## Sources

- [Karpathy’s Sequoia AI Ascent 2026 summary](https://karpathy.bearblog.dev/sequoia-ascent-2026)
- [Original Sequoia talk recording](https://www.youtube.com/watch?v=96jN2OCOfLs)
- [Karpathy on verifiability](https://karpathy.bearblog.dev/verifiability)
- [Karpathy on animals and ghosts](https://karpathy.bearblog.dev/animals-vs-ghosts)
- [Karpathy’s LLM Wiki design](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- [Anthropic: Claude Code memory](https://code.claude.com/docs/en/memory)
- [Anthropic: Claude Code hooks](https://code.claude.com/docs/en/hooks)
- [Anthropic: Claude Code skills](https://code.claude.com/docs/en/skills)
- [OpenAI: Codex plugin for Claude Code](https://github.com/openai/codex-plugin-cc)
- [Boris Cherny on feedback loops](https://www.threads.com/@boris_cherny/post/DTBVvvhEnnW/)
- [Austin Marchese’s video](https://www.youtube.com/watch?v=7zZy1QTvokM)
