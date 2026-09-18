---
title: Cutting Anthropic API Costs with Caching, Batching, and Routing
author: Chase AI
channel: Chase AI
url: https://youtu.be/V0XbuApxlhg?is=zi5wLNsZpME--xI6
date: 2026-08-06 04:43
tags: ai, development
---

# Cutting Anthropic API Costs with Caching, Batching, and Routing
- Source: Chase AI, published August 6, 2026; video duration: 18:59.
- Its “20x more” title is sensational, not a universal savings guarantee.
- Supported thesis: Chase AI compares a $20/M-token write with a $1/M-token read.
- The video is about Claude Code, not Anthropic's asynchronous Message Batches API.
- Here, batching means grouping related work within a warm-cache session.
- Captions are automatic; model, command, repository, and tool names may be wrong.
- Chase AI simplifies one word to one token to explain input and output billing.
- The transcript calls 5+4+6=16; the listed values total 15, suggesting a source error.
- He says output tokens generally cost about five times as much as input tokens.
- Each follow-up carries prior context, so repeated input can grow to 100,000 tokens.
- A prompt cache acts like a cheap-to-read document containing the prior conversation.
- Chase AI says a subscription cache expires after one inactive hour.
- Every message refreshes that timer; a message at minute 59 starts another hour.
- He quotes “Fable” output at $50/M tokens and Opus output at $25/M tokens.
- He quotes base input at $10/M and a one-hour cache write at $20/M tokens.
- He quotes cache hits at $1/M; he notes a five-minute API option but gives no price.
- A warm 500,000-token history costs $0.50 to read in Chase AI's example.
- A new 1,000-token write is about $0.02; Chase AI cautions his math may be off.
- After the hour expires, he prices that 500,000-token history near $10.
- Model, effort, fast-mode, MCP, plugin, tool, compact, and upgrade changes reset cache.
- Stabilize those choices, batch related turns, and change configuration at boundaries.
- Do not infer an API batch discount, latency gain, or throughput result from the video.
- `/clear` drops chat history; project files may provide enough evidence to resume.
- Its trade-off is losing decisions or constraints that existed only in conversation.
- `/compact` starts over with a native summary stored in message history.
- Chase AI warns of context rot around 600,000 to 800,000 tokens; compact earlier.
- Compaction keeps continuity but resets cache and may omit details in summarization.
- A handoff skill writes a Markdown summary to disk for a fresh chat to read.
- Handoffs add file upkeep but are portable, inspectable, and reusable living documents.
- Routing assigns planning to “Fable” or Opus and execution to a cheaper model.
- The executor shares context with the advisor when blocked; each has its own cache.
- Chase AI reports better outcomes at lower cost for this advisor/executor pattern.
- A Codex plugin or custom skill can delegate Claude Code work to GPT models.
- Chase AI recommends captioned “Luna” and “Terra,” but supplies no exact prices.
- He says their prices fell sharply and Anthropic lacked an equivalent price point.
- Local models are another option when tasks fit; no setup or savings data are given.
- Run `/doctor` to trim `CLAUDE.md`, unused skills, and unused MCP integrations.
- Chase AI saw 40,000 starting tokens from skills, system prompt, memory, and more.
- He calls hygiene savings marginal but says pruning also reduces skill-selection confusion.
- Review deletions because useful instructions or integrations can otherwise disappear.
- “Ponytail” allegedly writes less code; Chase AI says supplied benchmarks held on “Fable.”
- The repository used old Haiku 4.5 data; project complexity may change real results.
- “Caveman” claims 65% fewer output tokens, according to Chase AI.
- “Be brief” can cut output, but terse answers can omit useful code or explanation.
- Measure reads, writes, outputs, resets, quality, and rework; rates are not guarantees.
- Priority: caching, deliberate boundaries, routing, hygiene, then output scaffolding.
