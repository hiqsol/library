---
title: "Lovable Was the Most Copied AI Product of 2025. Then a Lobster Changed Everything."
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=b7IS4C9QALc
date: 2026-03-23 00:00
tags: ai, startups
---

# Lovable Was the Most Copied AI Product of 2025. Then a Lobster Changed Everything.

## The OpenClaw Moment

OpenClaw is the most consequential ChatGPT-level moment in the history of AI since ChatGPT
itself — which in AI terms is a long time, but in real life is about two years. Coverage of
the OpenClaw phenomenon has split into two predictable camps: the horse-race narrative
("who's copying OpenClaw fastest?") and the security-panic narrative ("how bad is the
dumpster fire?"). Both stories are real. Both are hiding what actually matters underneath.

The real story is that every major company responding to OpenClaw has made a *different* bet.
Different tradeoffs, based on their position on the board. Understanding those bets gives you
a superpower: you can look at any new agent product and immediately understand what it is
actually for, whether it works for you, and why you should care — instead of reacting to
every announcement with exhausted confusion.

## The Avalanche of Competitors

The scale of the response is hard to overstate. Every major player has entered the OpenClaw
ecosystem:

- *Nvidia* built NeMo Claw and Jensen Huang compared OpenClaw to Linux
- *OpenAI* acqui-hired Peter Steinberger and is actively planning an OpenClaw-style launch
- *Meta* spent $2 billion on Manus and immediately pivoted it toward the OpenClaw model
- *Lovable* — the most copied AI product of 2025 — is now becoming the copier, announcing
  an expansion beyond vibe coding into general-purpose agent execution

Beyond the big players, OpenClaw's open-source nature spawned a wave of forks, each
attacking a perceived weakness in the original:

- *ZeroClaw* rewrote OpenClaw in Rust
- *Moltbot* (formerly the OpenClaw predecessor) targeted enterprise Rust deployments
- *OpenFang* pitched itself as an agent operating system
- *Nanobot* from Hong Kong stripped OpenClaw down to just 4,000 lines of code

This is exactly what happened with Linux and Android. The original is messy, powerful, and
large — precisely because of that scale, it gets widely adopted, and the entire ecosystem
becomes a contest over gaps in the original implementation.

## The Three Axes That Actually Matter

The typical media framing places these products on a single spectrum of control. That framing
is not wrong — it is just incomplete in a way that leads to bad product decisions. The real
framework has three axes:

**1. Where does your agent run?**
Local, cloud, or hybrid. This determines your data privacy posture, your security surface
area, and accountability when something goes wrong. It is often a security and privacy
answer. Sometimes it is a convenience answer.

**2. Who orchestrates the intelligence?**
Is it one model doing everything? A multi-model harness that routes tasks to different
models? A model-agnostic setup where you plug in your own? This determines cost, quality,
and vendor lock-in. If you care about model quality and flexibility, you should look for
solutions that give you that control.

**3. What is the interface contract?**
Messaging app you already use, dedicated desktop app, or phone? This determines the product
experience in ways that are not trivial. These products make assumptions about your
behavior. Be honest with yourself: you are probably not changing your behavior to fit a new
interface.

## Profiling the Players

### OpenClaw: The Sovereignty Play

OpenClaw runs locally, on your machine, with your API keys and your data. It is a data
sovereignty play. You can plug in any LLM — Claude, ChatGPT, local models. You can plug in
any messaging platform — Telegram, WhatsApp, Signal, Slack. The whole design philosophy is
modular interoperability: OpenClaw belongs to the user.

That philosophy is also why OpenClaw has rattled corporate incumbents. Every major tech
product has assumed it should be whatever the company wants it to be. OpenClaw's thesis is
the opposite: you bring your own everything and you are in charge.

The security surface area is a genuine issue. Researchers have found over 30,000 publicly
exposed instances with weak or missing authentication in OpenClaw plugins. The skills
registry has been hit with a supply chain attack with over 800 compromised skills
documented. 250,000 GitHub stars.

*Who it is for:* Developers and technical power users who want maximum control over their
infrastructure, are comfortable with the security tradeoffs, and want to swap Lego bricks
in and out. Not for non-technical users.

### Perplexity Computer: The Delegation Play

Perplexity Computer takes the non-technical user weakness of OpenClaw and turns it into a
product. It runs entirely in the cloud. You describe the outcome; the system independently
decomposes it into subtasks, spins up agents, and returns results. Perplexity claims
support for very long-running tasks — tasks that last for months. The product costs $200
per month.

The strategic bet is the inverse of OpenClaw: instead of "you are sovereign and responsible
for everything," Perplexity says "we take that weight off you." Runs in a virtual sandbox.
They handle security. The tradeoff: you are paying for a cloud service and trusting
Perplexity with all your data.

The gravitational pull of OpenClaw is so strong that Perplexity is also planning a local
version — a secure container on your hard drive — for users who want delegation but also
care about data locality. This is the positioning agony of entering a category after someone
else has defined product-market fit.

*Who it is for:* Knowledge workers and enterprise teams who want outcome-level work and are
comfortable delegating infrastructure. Not for users who want model flexibility, full data
sovereignty, or a lower monthly commitment.

### Manus: The Distribution Play

Manus was already a massive win before Meta acquired it — the fastest company to $100
million at the time. The first launch post-acquisition is a different animal. Meta spent $2
billion and pivoted Manus toward the OpenClaw model, and the strategic logic is simple:
where are people's eyeballs? If the agent moment is viral and real, Zuckerberg wants people
spending that time inside the Meta ecosystem. At Meta's scale — three billion users —
monetization is a problem for later. The immediate goal is attention capture.

Manus is not making an enterprise-quality argument. It is making a scale argument: serve
customers at a scale no one else can match, using a mix of local Meta models and outside
models. The data question is the central one: before the acquisition, the concern was
trusting a company with Chinese roots; now it is trusting Meta.

*Who it is for:* Consumers and small businesses who want agent capability but are nervous
about the terminal, and who are already in the Meta ecosystem. Not for developers who want
model flexibility, enterprises that care about data governance, or individuals who are
skeptical of Meta's data practices.

### Anthropic Dispatch: The Safety Play

Anthropic launched Dispatch, which enables messaging into Claude Code from your phone.
The core argument: given widespread safety concerns about OpenClaw, use the safe option.
Use Claude. The model is simple and currently primitive: one instance, single-threaded,
no multi-conversation management. You message from your phone via Dispatch into Claude Code,
which runs a dedicated terminal session. There is also a Telegram option designed to be more
developer-friendly.

Given that Claude Code already runs as a full agent on your computer — browsing, editing
PowerPoints, managing calendars, handling email — the value proposition is real. The
limitation is that you do not get multi-model routing. If you want a simpler model for
easier queries and a more powerful model for complex agentic tasks, that is not the story
Anthropic is telling here.

The strategic insight is notable: where other companies fear disintermediation, Anthropic
sees it as brand reinforcement. If Claude is the safe, secure option — which has been their
positioning all along — then making Claude accessible everywhere strengthens that brand.

*Who it is for:* Non-technical professionals already invested in the Claude ecosystem who
want to drive their desktop agent from their phone. Not for users who want multi-model
orchestration or messaging-platform flexibility.

## The Irony of Lovable

This deserves to be a business school case study.

Lovable has been the most imitated product in AI through 2025. A vibe coding tool that
surpassed $300 million in ARR. It took the idea of building software through natural
language and made it genuinely accessible — not just for developers, but for anyone. The
interface was intuitive. The output actually worked. Real people built real businesses on
top of it.

Then, on March 19, 2026 — just days after Manus launched and Anthropic shipped Dispatch —
Lovable announced it was expanding beyond building websites. It would become an everything
tool for complex execution. The most copied product of 2025 is now copying someone else.

The underlying pressure is structural. Lovable's interface was architected around a
fundamental assumption: a human types a prompt. That assumption is dissolving. People now
want agents to handle complex multi-step tasks autonomously. The abstraction layer has
moved up. Even a product with $300M ARR and devoted millions of users has to walk the
tightrope from "powerful AI tool that humans mediate" to "powerful AI tool that is
agent-first." That is a difficult position when your fans love you exactly the way you are.

## The 2026 Thesis: Relentless Simplification

Agents are compressing the interface layer. Every vertical tool — app builders, analytics
platforms, document generators — is under pressure to collapse into a single conversational
agent that handles everything. The products that survive this compression will be the ones
that either:

- Go *deep enough* to have specific capability that does not exist anywhere else (Lovable's
  potential path), or
- Go *broad enough* to become a default delegation layer (Perplexity Computer's path,
  OpenClaw's path)

The middle is where you go to die. Tools that are good but not best-in-class. Tools that
are not general enough to serve as general-purpose agents. That is a recipe for product
death in 2026.

## A Framework for the Next OpenClaw Launch

There will be another one within 24 hours of any given video in this space. Use this
framework to evaluate it:

1. *Where does it run?* Local, cloud, hybrid. What does that tell you about security and
   privacy posture? What does it mean for who owns what when things go wrong?

2. *Who picks the model?* Do you want that control? Do you trust the company picking the
   model to act in your interest rather than theirs?

3. *What does the interface assume about you?* Are you already in Slack? Telegram? Signal?
   The product assumes something about your behavior. Be honest: you are probably not
   changing your behavior to fit it.

## Positioning the Players on the Map

Think of two axes: technical complexity/risk on one side, user control on the other.

- *OpenClaw* maxes out both. Maximum flexibility, maximum control, maximum risk, maximum
  security decisions to manage. Upper right.
- *Perplexity Computer* is lower left. Minimum technical risk, minimum user control. You
  trade control for a professional-grade managed solution.
- *Manus* sits in between — somewhat more configurable than Perplexity, somewhat less than
  OpenClaw, with the data tradeoff as its own axis.
- *Dispatch (Anthropic)* is a professional-grade middle option. Low technical complexity,
  more control than Perplexity because Claude skews toward technical users, with more
  messaging options coming.
- *Lovable* is nearly its own island: very low technical complexity, very high user control
  — because that is what Lovable has always been known for.

## The Bigger Picture

OpenClaw set the terms of the debate. It said: these are the axes that matter. We are going
to make the strongest possible sovereignty play — give users control over their agents and
their future. People responded in droves: 250,000 GitHub stars.

Now everyone else is playing on OpenClaw's terms, on a graph OpenClaw defined.

The question of 2026 is which niches in the OpenClaw ecosystem can other players carve out
and thrive in. Which bets will win by serving the subset of users who want an OpenClaw-style
experience but are not satisfied with something in the original — whether that is delegation,
safety responsibility, or the degree of control itself.

How we delegate agentic trust is the question of 2026. That lens is more useful than the
horse-race hype. It is more useful than the security panic. It is the lens that will help
you read the next announcement, the one that will drop in eight hours, and understand what
it actually means.

The 250,000 GitHub stars for OpenClaw assure one thing: this ecosystem is stable, it is
here, and it is not going anywhere. Agents are how commerce is going to be done. The wave
started. The question is who defines the niches inside it.
