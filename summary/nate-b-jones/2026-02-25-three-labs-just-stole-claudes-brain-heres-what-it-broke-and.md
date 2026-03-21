---
title: Three Labs Just Stole Claude's Brain
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=0v9ixCWNhPo
date: 2026-02-25 15:00
tags: ai
---

# Three Labs Just Stole Claude's Brain — Summary

DeepSeek, Moonshot, and MiniMax ran 16 million automated conversations
with Claude across 24,000 fake accounts. Not a Cold War — a Napster
problem. A pressure gradient where capabilities worth trillions can be
extracted for thousands.

**The operations:** DeepSeek: 150,000 exchanges extracting reasoning
traces + censorship-safe training data. MiniMax: 13M exchanges targeting
agentic coding/tool orchestration; pivoted within 24 hours of a new model
release; 20,000+ simultaneous accounts. Moonshot: 3.4M exchanges targeting
agentic reasoning, tool use, computer vision; produced Kimi.

**Distillation produces compression, not copies.** Frontier models occupy
a wide manifold (broad capability space). Distilled models occupy a narrow
manifold — optimized for targeted behaviors, brittle outside distribution.
Like NFL highlights vs. the full game.

**The performance shadow:** On short, well-defined tasks, distilled models
perform at ~90% of frontier quality. On extended agentic work (hours/days,
novel tool combinations, error recovery), the gap is a chasm. Kimi K2
excels at PowerPoint but drops on sustained agentic work. No benchmark
captures this gap because evals for sustained autonomous generality don't
exist yet.

**Economics:** MiniMax spent ~$2M in API costs to extract capabilities
costing ~$2B to develop. A 1,000:1 return on theft. The incentive is
universal — every non-hyperscaler lab faces the same pressure gradient.
Even Meta pursued capabilities through talent acquisition ($14B Scale AI
deal, nine-figure researcher packages).

**Time edge matters.** Capabilities double ~every 90 days. Countermeasures
(behavioral fingerprinting, detection classifiers) won't stop distillation
but slow it — exactly like DRM in music. The friction window is where the
money lives.

**Task scope framework:** Match model provenance to task scope.
- Narrow tasks (classify, summarize): distilled models at 90%+ quality,
  fraction of cost — take the trade
- Wide tasks (multi-day autonomous, novel tool combos): frontier only.
  The distilled model breaks by hour 4-8

**Off-manifold probe:** Run a complex domain task on different models.
When both succeed, change one constraint. Does the model adapt or force-fit?
Reveals more than leaderboard scores.

**Three takeaways:** (1) Assume frontier capabilities will leak — speed
bumps matter because curves are exponential. (2) Distilled models are
systematically worse in ways benchmarks miss, especially for agentic work.
(3) Model routing (which AI for which problem given provenance) is now a
competitive advantage.
