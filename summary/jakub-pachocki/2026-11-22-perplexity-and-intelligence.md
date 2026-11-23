---
title: Perplexity Can Be an Early-Warning Metric, Not a Universal Intelligence Scale
author: Jakub Pachocki
channel: OpenAI
url: https://openai.com/index/perplexity-and-intelligence/
date: 2026-11-22 00:00
tags: ai, technology
---

# Perplexity Can Be an Early-Warning Metric, Not a Universal Intelligence Scale

[article](../../articles/jakub-pachocki/2026-11-22-perplexity-and-intelligence.md)

OpenAI chief scientist Jakub Pachocki proposes pretraining loss as a shared measure of AI progress
and a trigger for industry safety limits. OpenAI's internal series links lower loss on held-out code
to conversational, coding, cyber, and mathematical milestones.

Cross-entropy measures average next-token prediction error under a specified corpus, tokenizer, and
context protocol. Perplexity is its exponential. This is a stable measure of predictive fit and
coding efficiency, but it does not directly measure reasoning, agency, truthfulness, or safety.

Loss often scales smoothly with model size, data, and compute inside controlled model families. It
can also help forecast downstream performance when researchers fit task- and domain-specific
mappings. Those findings do not make one loss number a universal intelligence unit.

OpenAI's figures come from a private code dataset. The corpus, tokenizer, context rules,
contamination controls, checkpoints, uncertainty, and capability measurements are not public, so the
reported 0.99-to-0.73 scale cannot yet be reproduced or compared across laboratories.

Per-token loss changes with tokenization. It also depends on domain mixture, document boundaries,
context length, metadata, retrieval, and contamination. A value of 0.8 from one lab need not mean
the same thing as 0.8 from another.

OpenAI links losses near 0.78 and 0.76 with major cyber and mathematical capabilities. These are
first-party correlations, not demonstrated causal thresholds. The chart itself labels a cyber expert
at 0.828, while the predicted 0.68–0.70 transition has no measured model or confidence interval.

Some apparently sudden emergent abilities become smooth when exact-match scores are replaced by
higher-resolution metrics. Genuine transitions may still occur, but a benchmark jump does not prove
that a precise loss value created a new capability.

Being closer to an entropy floor means a small loss reduction may remove more of the remaining
prediction error. Information theory does not imply that it must produce a larger intelligence gain;
the mapping from loss to capability remains empirical and task-specific.

OpenAI also reports declining chain-of-thought monitorability as models improve. Lower base loss,
architecture, reinforcement learning, and model-generated training data all contribute, so
perplexity alone does not explain monitor evasion.

A shared loss trigger could start safety testing before developers know which dangerous capability
will emerge. It should supplement direct cyber, biological, autonomy, AI-R&D, monitorability,
security, and safeguard evaluations—not replace them.

A credible cross-lab standard would need common byte-normalized tests, secret rotating corpora,
multiple domains, contamination audits, uncertainty reporting, independent access, and predefined
actions when either loss or direct risk thresholds are crossed.

The strongest conclusion is not “perplexity equals intelligence.” Held-out loss is a useful upstream
indicator of pretraining progress. It may help tell developers when to look harder, but it cannot
show by itself what a deployed system can do or whether its safeguards are adequate.
