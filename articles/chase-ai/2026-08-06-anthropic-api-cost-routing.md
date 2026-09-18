---
title: Cutting Anthropic API Costs with Caching, Batching, and Routing
author: Chase AI
channel: Chase AI
url: https://youtu.be/V0XbuApxlhg?is=zi5wLNsZpME--xI6
date: 2026-08-06 04:43
tags: ai, development
---

# Cutting Anthropic API Costs with Caching, Batching, and Routing

## What the source supports—and what its title overstates

Chase AI's source video is titled “You're Paying Anthropic 20x MORE Than You Need To.”
That is a sensational ceiling, not evidence that every Anthropic user is overpaying by 20x.
The supported thesis is narrower: in Chase AI's example, a warm prompt-cache read costs
one-twentieth of a one-hour cache write, so avoidable cold reads of long histories can be
about 20 times as expensive as warm reads. The other methods offer smaller or unquantified
savings and depend on the workload.

The 18:59 video was published on August 6, 2026, by Chase AI. It discusses Claude Code,
while this article organizes its lessons for API-cost thinking. It does not present or price
Anthropic's asynchronous Message Batches API. Here, “batching” means grouping related work
inside a warm-cache session and batching handoffs or resets at deliberate boundaries. It
must not be read as a claim about an API batch discount.

> Caption caveat: the source is an automatic transcript and may contain transcription
> errors, especially in model, tool, repository, and command names. Labels such as “Fable,”
> “Luna,” “Terra,” “Ponytail,” and “Caveman” are reproduced as heard, not independently
> verified. All prices, savings, performance results, and causal claims below are attributed
> to Chase AI rather than asserted as current Anthropic documentation.

## Why conversation cost compounds

Chase AI uses a deliberately simplified rule of thumb: treat each word as one token. In the
example, “How are you doing today?” is five input tokens, and “I'm doing great, thanks” is
four output tokens. Chase AI says output tokens generally cost about five times as much as
input tokens, although the exact rate depends on the model.

Those nine tokens enter the context window. Chase AI describes the window as a budget and
says Opus, “Fable,” and Sonnet have one-million-token budgets. A follow-up such as “Build me
an app, no mistakes” appears to add only six tokens, but the request also carries the prior
conversation. Chase AI calls the second input 16 tokens, although the listed five, four,
and six add to 15; this appears to be a spoken or caption arithmetic inconsistency.

The operational point is more important than the toy count. Every follow-up includes the
history needed for context. A long session can therefore cause 5,000, 10,000, or 100,000
input tokens to be processed on each message, according to Chase AI. Users pay for that
processing unless the repeated prefix is served at a cache-read rate.

## 1. Keep prompt caches warm

Chase AI explains the cache as a document containing the conversation up to the current
point. Claude still reads that history, but repeated cached tokens are billed more cheaply
than newly written tokens. A new message is written at the higher rate; on the next turn,
that message joins the cached prefix.

In Chase AI's account, a subscription session uses a one-hour cache. The hour measures
inactivity, not total age: each message refreshes the timer. A message at minute 59 starts a
new hour. After at least an hour without activity, the cached document disappears, and the
next request must process the long history at the full write rate.

Chase AI gives these model and token prices:

- “Fable” output: $50 per million tokens.
- Opus output: $25 per million tokens.
- Base input: commonly described as $10 per million tokens.
- One-hour cache write: $20 per million tokens, or twice that base-input figure.
- Cache read or hit: $1 per million tokens.
- A five-minute cache-write option appears for API users, but the video gives no price.

Chase AI says output pricing does not change with this caching distinction. The 20x claim
compares the $20 one-hour cache-write rate with the $1 cache-read rate, not total bills,
all models, or every token category.

His 500,000-token example makes the distinction concrete. Reading a warm 500,000-token
history at $1 per million costs $0.50. If a new message adds 1,000 tokens at $20 per
million, Chase AI estimates about $0.02 for that new write and cautions that his mental
math may be off. On the following call, those 1,000 tokens become part of the cached
history. If the user waits an hour and the cache goes cold, Chase AI puts the same
500,000-token history near $10 instead of $0.50.

Chase AI also says the cache resets when the user:

- switches models, such as moving from “Fable” to Opus;
- changes the effort level or enables fast mode;
- connects or disconnects an MCP server;
- changes plugins or denies tools;
- compacts the conversation; or
- upgrades Claude Code.

The trade-off is timing versus interruption. Keeping a session active can preserve a cheap
read path, but sending meaningless keep-alive work is not recommended by the source and
would itself consume tokens. The defensible tactic is to group genuinely related work
while the cache is warm and avoid configuration changes in the middle of that batch.

## 2. Batch work around clean boundaries

Because the source does not cover Anthropic's Message Batches API, the practical batching
pattern here is temporal and architectural:

1. Start with stable model, effort, tools, plugins, and MCP configuration.
2. Group related prompts into a focused session while its one-hour inactivity timer is warm.
3. Avoid model and configuration switches until the related batch is finished.
4. Before a long break, choose a clear, compact, or handoff boundary.
5. Resume from the smallest sufficient context rather than blindly reheating a huge history.

This pattern follows Chase AI's causal claim that repeated warm prefixes cost less and that
switches can invalidate the cache. It is not an API batching benchmark, and the video does
not quantify throughput, latency, or discounts for concurrent or asynchronous requests.

### Clear: cheapest context, least conversational continuity

Use `/clear` to wipe the conversation and start over. Chase AI calls this the nuclear
option, but says it is often adequate for a codebase because completed work remains visible
in project files. Claude Code can inspect those artifacts and reconstruct what happened.
The trade-off is that decisions or constraints that exist only in chat may be lost.

### Compact: native summary inside the conversation

Claude Code can auto-compact after a token threshold, but Chase AI recommends not waiting.
He says context rot begins to matter around 600,000, 700,000, or 800,000 tokens, even with
larger, more capable models. Running `/compact` manually summarizes the old discussion,
effectively clears it, and begins a new context with the summary stored in message history.

Compaction preserves more continuity than clearing, but it resets the cache and can omit
information during summarization. Chase AI recommends it when the codebase alone cannot
explain the prior work. He also advises against routinely operating at 400,000, 500,000,
or 600,000 tokens.

### Handoff: a durable summary on disk

A custom handoff skill writes a Markdown summary to disk. Start a fresh conversation, then
ask Claude Code to read that handoff document. Unlike compact, whose summary remains a
message in one conversation, handoff creates a reusable file that can become a living
document and be updated over time.

The setup is to obtain or create a handoff skill, choose what its Markdown file should
capture, run it before resetting, start a new conversation, and point Claude Code to the
file. Chase AI mentions his own handoff tool in his free community. The trade-off is extra
file maintenance in exchange for portability, inspectability, and explicit control.

## 3. Route each task to the least expensive adequate model

Chase AI asks whether every task needs “Fable.” His answer is no: simpler tasks can go to a
smaller, cheaper, less capable model. Options include other Anthropic models, GPT models,
and local models. The quality and privacy trade-offs are task-dependent and are not
benchmarked in the video.

### Advisor/executor architecture

In advisor mode, a stronger model such as “Fable” or Opus makes the plan. A smaller model
such as Sonnet executes it. If the executor gets stuck, it shares its context with the
advisor and asks for help. Chase AI says this architecture has reported better outcomes at
lower cost. He also says the advisor and executor maintain separate prompt caches at the
same time, so cache behavior must be managed for both streams.

### External and local routing

A Codex plugin can be installed in Claude Code so “Fable” can delegate from the same
interface to GPT models, approximating advisor mode with a non-Anthropic executor. Chase AI
also mentions “Fable advisor” repositories and says building a custom delegation skill is
fairly trivial.

Chase AI specifically recommends the captioned GPT models “Luna” and “Terra,” saying their
prices were reduced significantly and that Anthropic had no equivalent at that price point.
No exact prices are supplied. Local models can reduce external use further when a task is a
good fit, but the video gives no setup steps, hardware requirements, or measured savings.

A practical routing setup is therefore:

1. Classify work into planning, execution, and escalation.
2. Assign the stronger model to planning and difficult decisions.
3. Assign a cheaper Anthropic, GPT, or local model to routine execution.
4. Let the executor send context to the advisor only when blocked.
5. Track the advisor and executor caches independently.
6. Compare real quality and cost on the project's own tasks before broad adoption.

## 4. Reduce configuration bloat

Chase AI does not say everyone must delete `CLAUDE.md`. Instead, run `/doctor`. He says
newer “five series” models need less instruction than models from three, six, or nine months
earlier. Old, highly prescriptive files may now add latency and token cost without helping.

According to Chase AI, `/doctor` trims unnecessary `CLAUDE.md` instructions and inspects
context bloat from skills and MCP servers. His cleaned setup still began a new conversation
with 40,000 tokens already occupied by items such as skills, the system prompt, and memory
files. `/doctor` can identify unused skills and MCPs for removal.

Chase AI calls the savings marginal rather than huge, but the setup is simple:

1. Run `/doctor`.
2. Review proposed reductions to `CLAUDE.md`.
3. Remove unused skills and MCP integrations.
4. Consolidate overlapping skills, such as multiple front-end design skills.
5. Recheck the starting context with the context view.

He says pruning also helps skills fire more reliably by reducing ambiguity about which one
to call. The caveat is that deletion can remove useful instructions or integrations, so
review the changes rather than treating all context as waste.

## 5. Cut output tokens with skills and concise instructions

Chase AI ranks scaffolding as the least effective of the five approaches today, but says it
can stack with caching, boundaries, routing, and hygiene.

The captioned “Ponytail” skill is said to reduce how much code Claude writes while preserving
effectiveness, making runs cheaper and faster. Its repository showed results for the older
Haiku 4.5. Chase AI says he reran the supplied benchmarks with “Fable,” found that the
numbers held up, and saw even better results with stronger models. He cautions that actual
results may differ with project complexity.

The captioned “Caveman” tool claims a 65% reduction in output tokens, according to Chase AI.
A one-line `CLAUDE.md` instruction such as “be brief” can also reduce output. Neither claim
comes with a dollar-cost benchmark in the video, and terse output can omit explanation or
useful code. Chase AI's larger point is that output reduction is only one part of the bill;
he says prompt caching dominates the available efficiency gains.

## A cost-aware operating playbook

For a fresh project, first run `/doctor`, trim stale instructions, and remove unused skills
and MCPs. Choose the model, effort level, plugins, and tools before beginning a focused work
batch. Keep related turns together so repeated context can remain a warm prefix.

Use a strong planner with a cheaper executor when the task permits. Treat each agent's cache
as separate. Test external or local executors on representative tasks rather than assuming
lower token price means lower total cost or equal quality.

Before an hour-long break or a configuration change, stop at an explicit boundary. Use
`/clear` when the project files tell the story, `/compact` when a chat summary is enough, or
a handoff file when the state must survive across conversations. Avoid carrying hundreds
of thousands of tokens merely for continuity.

Finally, add concise-output scaffolding only after fixing cache behavior and context size.
Measure the whole bill: warm reads, new writes, outputs, reset frequency, and any quality
rework. Chase AI supplies illustrative rates and benchmark claims, not a current pricing
contract or a universal guarantee.

## Bottom line

The defensible lesson is not that every Anthropic bill can fall by 20x. It is that a specific
cached-prefix comparison in Chase AI's example is 20x, and long cold histories can make that
difference consequential. The broader strategy is to preserve useful warm caches, batch
related work between deliberate reset boundaries, route routine work to cheaper adequate
models, trim default context, and reduce output only where brevity does not hurt results.
