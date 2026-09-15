---
title: How Vercel Solved Agent Building
author: Andrew Qu
channel: AI Engineer
url: https://youtu.be/9dYcwOkpCE8?is=Qe3sSd4u8WeXL-3P
date: 2026-09-14 17:00
tags: ai, development
---

# How Vercel Solved Agent Building

Andrew Qu's account of agent development at Vercel is a story of removing structure, then adding
back only the structure that proved useful. The team moved from one enormous prompt to a rigid
multi-agent pipeline, then to one stateful agent, a filesystem agent in a sandbox, reusable skills,
and finally a convention-based framework called Eve.

The progression matters because each architecture solved the previous one's failure while exposing
another. Qu's larger thesis is that capable models and generic infrastructure are not enough. The
highest-value business agents depend on knowledge specific to one company: its data model,
relationships, terminology, procedures, and judgment about which source to query when.

## The infrastructure behind the experiment

Vercel began in web infrastructure, helping applications scale up to a million and down to zero.
Qu said the company then began applying the same simplification goal to agentic applications.
The AI SDK, whose name is garbled in the captions, reduced switching model providers from replacing
300-400 lines of provider-specific code to changing one line behind a shared model interface.

The surrounding platform addressed model fallbacks, secure code execution, lower-cost waiting,
durability, and resumability. Those pieces became relevant as the experiment grew from a local
prototype into agents that could run for many steps, recover from errors, and serve other teams.

## Stage one: the mega-prompt

Qu and Vercel's CTO wondered whether an agent could sit on every desk, not only in coding but also
in design, product management, marketing, sales, finance, and legal. Qu asked teams which parts of
their jobs they hated. The clearest opportunity came from the lean data team, which was repeatedly
interrupted to translate business questions into SQL, run analyses, and report recommendations.

The first data agent, later called D0 in the talk, was barely an agent. Qu put a Snowflake schema
dump and a question into a system prompt, copied the generated SQL, and ran it himself. This test
showed enough promise to continue, but it also showed that the model needed better context,
guardrails, and a way to perform the complete workflow rather than merely draft a query.

## Stage two: a multi-agent pipeline

Qu and the VP of Data decomposed a data scientist's work into specialized agents. A query passed
through planning, execution, SQL, and reporting stages. Each stage had a focused system prompt and
narrow tools. For example, one stage could read entity YAML and search schemas before passing a
small result or summary onward.

This pipeline completed the loop from question to answer, including execution and reporting. Its
weakness was information loss: later agents received only a summary and snippet from earlier work.
They could not inspect the full path, reflect on an error, or revise an earlier decision with all of
the evidence still available.

## Stage three: one stateful agent

The team replaced the chain with one agent holding the full context and managing its own state. The
same agent could plan, build, execute, and report in a single run with a maximum of 100 steps. When
a query failed to execute or a join was wrong, it could go back, inspect more context, and retry.

Internally, the team thought this version was strong. Qu said it passed about 30% of their evals.
Trusted users disagreed: their immediate verdict was that it was awful. They asked questions the
builders had not anticipated, and manually encoding every new scenario would not scale. The
failure revealed that a more elaborate handcrafted workflow was still too prescriptive.

## Stage four: a filesystem agent in a sandbox

Claude Code paired with Opus 4.5 changed the team's mental model. In Qu's telling, its key advantage
was not a large catalog of domain-specific tools but a filesystem and a small, familiar toolset:
It could list and read files or run Bash, then explore, execute work, and leave artifacts where
needed instead of following a path designed in advance.

Vercel rebuilt D0 in that style. A sandbox received the complete semantic layer. The agent could
use Bash and read or write files, while a few extra tools exposed Vercel-specific capabilities. A
Bash helper from npm connected the agent to the sandbox, where attached files could be read,
written, and executed securely.

Qu described this as the largest leap. According to him, the eval score roughly doubled after the
move to the purpose-built filesystem agent. He also said a blog post about the approach generated
70% of vercel.com traffic during its publication week. These are Qu's reported figures, not
independently verified measurements.

## Stage five: distilling repeated work into skills

Once Vercel released the data agent more broadly, Qu said employees sent thousands of queries per
day about customer metrics, sales metrics, numerical metrics, npm downloads, products, and billing.
Many requests had the same underlying shape: aggregate a measure, look up a product, or retrieve
billing information.

A recurring job began reviewing recent queries and distilling repeated solutions into skills. Qu
said the library reached roughly 100 skills, spanning generic aggregation and lookups about
specific people or data. The skills folder gave each new run accumulated context rather than
forcing the agent to begin with only a semantic layer and system prompt. Qu also mentioned
Vercel's Skills.sh as a way to find and run agent skills.

## Stage six: conventions instead of bespoke wiring

Other Vercel teams kept forking D0 at different points in its evolution. That repetition suggested
a framework should let builders start with the latest lessons rather than rediscover them. The
analogy was Next.js: put files in conventional locations and let the framework infer deployment
and infrastructure.

Qu introduced Eve, available at eve.dev, as a "Next.js for agents." An Eve project declares system
instructions and conventional skills, tools, and channels folders. The framework composes those
files into an agent, while builders add company knowledge, custom tools, and integrations for the
channels their users already inhabit. Projects can start from a template, deploy to Vercel, or be
self-hosted.

Qu's model divides an agent into a runtime and channels. The runtime needs durable execution,
isolation, model access, and connections. Eve was designed for open-source adapters, including
PostgreSQL, the OpenAI Responses API, Docker, and other connectors. On Vercel, the corresponding
stack uses Vercel Workflows for durability, Vercel Sandbox for secure execution, and Vercel Connect
for short-lived OIDC tokens. A Vercel deployment also exposes agent runs, tool calls, individual
steps, estimated costs, and possible optimizations through built-in observability.

## A customer example

Qu said beta customer Aura rebuilt an agent that behaves like a small Claude Code for testing
services: it visits websites, installs the services, and tries to use them. He reported that Aura's
Eve-based agent used fewer steps and produced better success and insight than its off-the-shelf
Claude Code approach. This comparison is Aura's result as presented by Qu, not an independently
verified benchmark.

## Why company-specific knowledge is the moat

Before D0, Vercel tested funded vertical-agent products that connected to Snowflake. Qu's conclusion
was that generic access to the warehouse did not capture enough of how Vercel works. A web company
needs an agent to understand customers' sites and web properties, how entities connect, and which
table or source is appropriate for a particular question.

That is why Qu favors building agents around proprietary operating knowledge rather than expecting
an off-the-shelf vertical agent to understand the business. He said Vercel had roughly 20 agents
with decent product-market fit, covering marketing retrospectives, recommendations about whom to
contact, first-pass contract redlines, and data-science queries. He further claimed that these
agents saved substantial time and let the data team improve Snowflake, add sources, and fill gaps
instead of spending its days writing one-off queries.

The framework is therefore the endpoint of a learning loop, not the whole solution. A common
runtime, sandbox, adapters, channels, and filesystem conventions reduce engineering friction.
Distilled skills preserve repeated solutions. But the part that makes an internal agent unusually
useful is the context only its company can supply.

## Source caveat

This article is based on auto-captions for Andrew Qu's conference talk. Obvious names such as
Vercel, AI SDK, Claude Code, D0, Next.js, and OIDC have been normalized cautiously. The framework
name is rendered as Eve because the talk repeatedly pairs it with eve.dev. Performance, adoption,
and customer outcomes above are claims made by Qu and have not been independently verified.
