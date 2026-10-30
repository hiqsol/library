---
title: Why I Cancelled My Claude Code Subscription (And You Should Too)
author: Jordan Urbs
channel: Jordan Urbs
url: https://www.youtube.com/watch?v=yFvl2x8_9gI
date: 2026-09-06 19:38
tags: ai, development
---

# Why I Cancelled My Claude Code Subscription (And You Should Too)

[summary](../../summary/jordan-urbs/2026-09-06-why-i-cancelled-my-claude-code-subscription.md)

I was a Claude Max subscriber paying $200 per month, and I loved it. Over the past year,
Claude Code went from an interesting tool to something I felt I could not live without as a
builder and solopreneur. On peak days, I used hundreds of millions of tokens.

That dependence is precisely why I cancelled.

During two of my final 30 days as a subscriber, my usage exceeded 700 million tokens per day.
At public API prices, the uncached input and output would have cost more than $50,000. After
accounting for prompt caching, I estimate those two days would still have cost about $1,800,
against a total monthly subscription price of $200.

Something about those economics cannot last forever. Either API margins are enormous, venture
capital is subsidizing consumer inference, or some combination of the two is true. The exact
answer matters less than the risk: what happens to a workflow built around Claude Code if the
price, usage limits, or product changes?

## Convenience Creates Ignorance Debt

A flat-rate subscription lets heavy users stop thinking about the cost of individual requests.
You open Claude Code, use the strongest available model, and keep working. That is an
extraordinary deal, but it encourages a workflow in which neither token consumption nor model
selection receives much attention.

I used Claude Code for landing and sales pages, automated Meta ad campaigns, video and
presentation assets made with Remotion and Hyperframes, and parts of my content workflow such
as repurposing and metadata generation. It also sat at the center of a project with my son: we
created a fictional world, wrote a book, launched a YouTube channel, built a learn-to-read
game, and made our own Patreon-style site.

The subsidy made speculative projects possible. Without cheap inference, I might not have
built something that had no guarantee of earning money. Yet I also began opening Claude Code
before considering whether another tool could do the job. My tools, memory, context, and
workflows were already there.

That convenience accumulates into what I call ignorance debt. You stop questioning the tool
because it works, then discover that the cost of switching has become uncomfortably high.
Cancelling is no longer like dropping a subscription; it means rebuilding a meaningful part
of how you work.

## Replacing Claude Is the Wrong Question

My first instinct was to look for a single substitute. Is Codex better? Is Gemini CLI better?
That framing is mistaken. One model or model family does not need to perform every role.
Planning, coding, creative writing, routine transformations, and final audits have different
requirements.

Open-weight models have become capable enough to do serious work, while open-source agent
harnesses can connect to many providers. I chose OpenCode as a model-agnostic replacement for
the Claude Code interface because it remains compatible with my agentic workflows without
binding them to one model family.

My emerging division of labor looks like this:

- Kimi K3 handles planning and orchestration. It costs more, but I find it intelligent,
  friendly, and easier to work with than Anthropic's Fable model.
- GLM 5.2 handles much of the implementation. It is cheaper, capable at coding, and also a
  strong creative writer.
- DeepSeek V4 Flash takes simple, repetitive work. I would not ask it to plan a project, but
  its speed and very low price make it suitable for menial tasks.
- A frontier model can return for a difficult final review or audit when its extra capability
  justifies the cost.

The goal is therefore not a perfect clone of Claude Code. It is a portfolio of models and
providers that can deliver comparable overall results without making the whole workflow
dependent on any one of them.

## Privacy Extends Beyond the Output

There is another reason I want more control over model providers. Privacy is not only about a
finished piece of code or content. Long agent sessions expose the creative process: how a
person thinks, decomposes problems, changes direction, and makes decisions. I do not want that
process tied indefinitely to one proprietary provider.

The concern becomes sharper when agents interact with home systems. I have experimented with
home security and Raspberry Pis running game emulators on my local network. I do not want a
proprietary cloud agent deeply embedded there, while models I can host locally are not yet
capable enough for all of my needs.

For this experiment, I use Venice as the provider for open-weight models. Venice says it has
zero-data-retention arrangements with its inference providers. That separation is valuable to
me because it reduces the opportunity to store my prompts or connect a behavioral profile to
my identity.

## Smart Routing Belongs in the Workspace

Moving away from subsidized inference makes model routing essential. A strong model can decide
what a job requires, pass a clear plan to a cheaper implementation model, and delegate simple
non-coding work to an inexpensive model. The expensive model returns only when its judgment is
needed.

The workspace itself can encode this policy. An `AGENTS.md` file can explain which tasks go to
which models and providers. Skills preserve reusable instructions, while subagent profiles
give specialized workers the context appropriate to their roles. The agent can then route
work rather than treating the default model as the answer to every request.

Structure also changes token consumption even when the underlying model stays the same. A
fresh workspace with a vague instruction such as “figure this out” forces the model to infer
the process, discover conventions, and repeatedly recover context. A tight workspace with
explicit instructions, skills, and role definitions can reach the same result with fewer
tokens.

Claude Code can call other models too. But flat-rate, subsidized access gives its users little
reason to design that system. People who never learn how inference, caching, routing, and
context affect costs could be caught unprepared when subscription economics change.

## The $200 Venice Experiment

I cancelled Claude Max and started testing Venice Max. It also costs $200 per month, provides
$225 in service credits, and offers access to more than 300 models. Instead of receiving
effectively invisible subsidized usage, I now see every prompt consume a measurable budget.

This is less convenient by design. I must decide whether a task needs the strongest model,
whether large context can be cached, and whether repeated instructions belong in a reusable
skill or behavior file. Paying attention to those decisions reveals weaknesses in both my
workspaces and my habits.

I do not need to own the GPUs yet. The durable asset is the workspace: its instructions,
knowledge, skills, routing policy, and agent definitions. If those remain portable, I can
replace a model, harness, or inference provider without bringing the rest of my AI-assisted
work to a halt. Local inference may become practical later, but provider competition already
offers meaningful choice today.

## An Experiment, Not a Verdict

I do not yet know whether this setup will fully replace what I received from Claude Code. The
next few weeks will test whether open-weight models, an open-source harness, and smart routing
can preserve the results while making costs explicit. I may find serious gaps or eventually
resubscribe.

The point is to stop outsourcing responsibility for the architecture of my work. Renting
frontier reasoning is fine when it is valuable. The important thing is to own the rails the
work runs on, understand the cost of every prompt, and retain the ability to move when a deal
or provider changes.
