---
title: Perplexity Can Be an Early-Warning Metric, Not a Universal Intelligence Scale
author: Jakub Pachocki
channel: OpenAI
url: https://openai.com/index/perplexity-and-intelligence/
date: 2026-11-22 00:00
tags: ai, technology
---

# Perplexity Can Be an Early-Warning Metric, Not a Universal Intelligence Scale

[summary](../../summary/jakub-pachocki/2026-11-22-perplexity-and-intelligence.md)

OpenAI chief scientist Jakub Pachocki proposes using pretraining loss as a shared
measure of AI progress and as a trigger for industry-wide safety limits. OpenAI's
internal series links lower loss on held-out code to conversational, coding,
cybersecurity, and mathematical milestones.[1]

The disclosure is useful, but it does not yet establish a universal intelligence
scale. The corpus, tokenizer, context protocol, contamination controls, uncertainty,
and capability measurements needed to reproduce the thresholds are not public.

Pretraining loss can serve as an upstream warning signal inside a controlled model
family. Cross-lab pacing would require a common measurement protocol and direct
capability and risk evaluations alongside it.

## What OpenAI disclosed

The article publishes base-model loss values for OpenAI systems from GPT-3.5 through
an unnamed November 2026 internal checkpoint. OpenAI says the values come from a
fixed snapshot of held-out data sourced from its internal codebase.[1]

Selected points include:

- GPT-3.5 at 0.986;
- GPT-4 at 0.913;
- GPT-5.3-Codex / GPT-5.4 at 0.871;
- GPT-5.6 Sol at 0.828;
- GPT-6 Astra at 0.783;
- GPT-6.2 Astra at 0.761;
- an unnamed internal model at 0.732.

The chart associates those points with milestones such as fluent conversation,
benefiting from thinking before answering, useful coding, cybersecurity expertise,
and a claimed Millennium Prize solution. A shaded 0.68–0.70 region is marked with a
question mark.[1]

These values are first-party disclosures. OpenAI has not released the evaluation
corpus, tokenizer, precise scoring implementation, model checkpoints, confidence
intervals, or an independently auditable package.

## What cross-entropy measures

For each token in a held-out sequence, a language model assigns probabilities to
possible next tokens. Cross-entropy loss is the average negative logarithm of the
probability assigned to the token that actually occurred.

Lower loss means the model assigned more probability to the observed continuation.
With natural logarithms, the result is measured in nats per token. Perplexity is the
exponential of that loss.

The same quantity has a coding interpretation: a better probability model can encode
the evaluated token stream with fewer expected bits or nats.

This makes held-out loss a clean measure of predictive fit under a specified test.
It does not directly measure truthfulness, planning, tool use, robustness, agency,
scientific judgment, or safety.

## Why loss is valuable

Empirical scaling-law research found that language-model loss changes smoothly and
predictably with model size, data, and training compute over controlled model
families.[2]

Later work has also estimated downstream performance by first forecasting pretraining
loss and then fitting an empirical mapping from loss to task results. Those mappings
can be useful when the family, domains, data mixtures, and evaluation procedure are
controlled.[4]

Loss has practical advantages over a static benchmark:

- it is continuous rather than pass/fail;
- it can be measured throughout training;
- it is less likely to saturate suddenly than a fixed task score;
- it can provide warning before developers know which capability will emerge;
- it covers unreleased checkpoints as well as products;
- it has a long history as an optimization target.

OpenAI's internal series therefore matters. It suggests that one stable code-loss
measure has remained informative across several generations of its own systems.

## Why the number is not portable yet

A raw loss is comparable only when the evaluated text, tokenization, preprocessing,
context construction, scoring rules, and model state are comparable.

### Tokenizers change the denominator

Different tokenizers divide the same text into different units. A tokenizer with
longer tokens changes both the prediction task and the number of terms being averaged.
A value of 0.8 nats per token under one vocabulary need not represent the same coding
rate as 0.8 under another.

Bits per byte can reduce tokenizer dependence, but it still requires identical bytes,
normalization, preprocessing, and context rules.

### Domains have different entropy

Code, conversation, news, mathematics, multilingual prose, and noisy web text have
different regularities. A model can achieve excellent code loss without being
uniformly better in medicine, persuasion, multilingual reasoning, or embodied work.

OpenAI's disclosed series uses proprietary code data. That may be especially relevant
to coding, cyber, and formal reasoning while being less representative of other risks.

### Aggregate loss hides mixtures

A single number averages over the evaluation distribution. Changing the proportion of
boilerplate, code, mathematics, prose, or rare languages changes the result even when
the model does not change.

Two models can have the same aggregate loss while differing substantially by domain.
Research that predicts downstream performance across data mixtures therefore uses
multiple domain-specific losses rather than assuming one scalar transfers unchanged.[4]

### Context changes the task

A longer context window can expose relevant earlier text and lower loss. Concatenating
documents differs from resetting at boundaries. Retrieval, repository paths,
neighboring files, and metadata can make code easier to predict.

Even the irreducible entropy floor depends on what information is allowed in the
context.

### Contamination can produce false confidence

A held-out file can still have near-duplicates, quoted solutions, or public mirrors in
training data. Repeatedly selecting architectures and data mixtures against the same
private set can also create adaptive overfitting without directly training on it.

A shared safety metric would need deduplication, contamination audits, versioning, and
rotating secret evaluation sets.

## Lower loss is not intelligence by definition

Within a fixed development regime, lower held-out loss often predicts broader
pretraining progress. That is weaker than calling it a direct measure of general
intelligence.

Loss weights tokens by their frequency in the corpus. Improvements on abundant,
predictable material can dominate rare but consequential abilities. It does not
represent deployment scaffolds, tools, permissions, memory, inference compute,
multi-agent coordination, or post-training.

Holistic evaluation frameworks use multiple scenarios and metrics because one scalar
cannot represent accuracy, calibration, robustness, fairness, efficiency, and risk at
once.[6]

Pachocki acknowledges this limitation indirectly: prompting, fine-tuning,
reinforcement learning, and chain-of-thought elicitation can change useful behavior
without changing the reported base-model loss.[1]

The careful claim is that loss is a broad internal proxy for pretraining progress, not
an intrinsic unit of intelligence.

## The thresholds are correlations

OpenAI associates GPT-3.5's 0.986 with fluent conversation and GPT-4's 0.913 with
productive chain-of-thought use. It says losses below 0.8 coincided with
transformative cyber and mathematical capabilities.[1]

The chart itself complicates a clean threshold story. GPT-5.6 Sol is labeled a
“cybersecurity expert” at 0.828, above 0.8. Some later products also have worse listed
loss than earlier products, such as GPT-4.1 / o3 after GPT-4.5.

Calendar time, compute, architecture, training data, post-training, elicitation, and
evaluation all changed alongside loss. Without neighboring checkpoints, ablations,
uncertainty, and independent replication, the chart cannot show that a precise loss
value caused a capability.

Research on emergent abilities reinforces this caution. Some apparently sudden jumps
disappear when discontinuous exact-match metrics are replaced with smoother measures
or higher-resolution statistics.[3]

This does not prove that qualitative transitions never occur. It shows that a sharp
benchmark transition is not enough to establish a new internal capability at a
universal threshold.

## The 0.68–0.70 window is a forecast

The lowest disclosed point is an unnamed internal model at 0.732. No model in the
chart reaches the proposed 0.68–0.70 band.[1]

Pachocki predicts further transformative capabilities in that range but says he does
not know what they will be. OpenAI provides no forecasting model, confidence interval,
capability definition, or independent validation for the band.

It should be treated as an informed internal forecast, not an established scaling law
or a deadline.

## Proximity to entropy does not prove accelerating intelligence

As loss approaches a fixed entropy floor, a small absolute improvement can remove a
large fraction of the remaining reducible loss.

That mathematical statement does not imply a larger gain in intelligence. There is no
general theorem mapping a reduction in prediction error to a fixed increase in
reasoning, planning, or scientific capability.

The downstream mapping may be smooth, thresholded by a scoring rule, saturated,
domain-specific, or even non-monotonic. It must be measured empirically for each task
and development regime.[4]

The entropy floor is also unknown and changes with corpus, tokenizer, and permitted
context.

## Chain-of-thought capability has multiple causes

OpenAI says GPT-4 at approximately 0.91 could use chain-of-thought reasoning
productively and that this motivated later reasoning models.[1]

It is plausible that pretraining created latent capabilities that prompting elicited.
But public GPT-4 documentation does not isolate how much observed performance came from
pretraining, post-training, prompts, data exposure, or evaluation choices.

The chart therefore records OpenAI's internal historical interpretation, not a public
ablation connecting chain-of-thought ability to 0.91.

## Cyber and mathematics claims need separate verification

OpenAI associates Astra-class losses with capabilities it characterizes as critical in
cybersecurity and groundbreaking in mathematics. Those claims rest on separate
internal evaluations and released artifacts, not on loss alone.

A mathematical proof artifact can be checked independently, but formal validity,
human-readable understanding, authorship, and institutional recognition remain
separate questions.

Similarly, cyber capability depends on the tasks, permissions, scaffolding, success
criteria, and operational conditions used in evaluation.

The loss value can be a warning that deeper evaluation is needed. It cannot substitute
for that evaluation.

## AI-assisted AI research is increasing

Pachocki argues that a step change could occur before full recursive self-improvement:
AI may accelerate the algorithmic research that improves pretraining.[1]

OpenAI reports meaningful AI contributions to recent design work while attributing
most of the steep 2026 loss improvement to long-term human research and compute
investment. The evidence is based on internal usage data and interviews rather than a
controlled causal experiment.

This supports increasing AI assistance, not autonomous research. Humans still define
objectives, choose experiments, allocate compute, review evidence, and decide what to
train and deploy.

## Monitorability may degrade for several reasons

OpenAI reports that lower base-model loss correlates strongly with greater no-CoT
capability and more weakly with the ability to control visible reasoning. It also finds
that reinforcement learning and model-generated training data can increase CoT
controllability.[5]

The researchers explicitly call these imperfect proxies for monitorability. Their
results implicate architecture, reinforcement learning, and training data as well as
pretraining loss.[5]

The evidence supports concern that visible reasoning may become a less complete window
into model behavior. It does not establish that chain-of-thought monitoring has already
failed or that perplexity alone determines monitor evasion.

Action monitoring, activation-based methods, full-trajectory review, and independent
safeguard testing remain necessary complements.

## A shared limit could still be useful

Pachocki proposes that developers commit not to cross agreed loss limits until concrete
monitoring milestones are achieved.[1]

Existing responsible-scaling frameworks already use threat models, capability
thresholds, safeguards, and risk assessments. OpenAI's Preparedness Framework tracks
biological and chemical, cyber, and AI self-improvement capabilities, with stronger
requirements at High and Critical levels.

A loss trigger could add earlier warning. It is available before a new dangerous
capability is fully understood and can activate stronger testing, security, external
review, or a safety-case update.

It should not replace capability thresholds. A system above the loss limit might gain
dangerous abilities through reinforcement learning, tools, inference scaling, or an
architecture change. A system below it could be dangerous in a narrow domain.

## How a defensible standard could work

A cross-lab standard would need at least:

- versioned, independently curated evaluation corpora;
- multiple domains, including code, language, science, and multilingual text;
- tokenizer-resistant reporting such as bits per byte;
- identical preprocessing and context-construction rules;
- contamination and adaptive-overfitting audits;
- secret rotating sets as well as stable trend sets;
- uncertainty intervals and sensitivity analysis;
- disclosure of checkpoint selection and product mapping;
- secure access for independent evaluators;
- a warning band before a hard trigger;
- predefined actions when either loss or direct capability thresholds are crossed.

The rule should be disjunctive: crossing a loss trigger **or** a direct risk threshold
activates stronger requirements. Remaining above a loss threshold must never override
evidence of dangerous capability.

## Gaming risks

Once a metric controls development, organizations gain incentives to optimize the
measurement rather than the underlying safety objective.

Possible strategies include choosing a favorable tokenizer, changing the corpus or
mixture, training indirectly on the test distribution, selecting convenient
checkpoints, or shifting capability gains into post-training and tools.

A proprietary benchmark cannot support public accountability without trusted external
access. A single common number could also create metric monoculture and crowd out
evidence about misuse, autonomy, deception, and safeguard efficacy.

Independent administration, rotating tests, multiple domains, and direct risk measures
would reduce but not eliminate these problems.

## What should accompany loss

A safety regime should also measure:

- cyber, biological, autonomy, and AI-R&D capabilities;
- autonomous task success and required human intervention;
- post-training and inference-compute scaling;
- tool access, persistence, permissions, and deployment scale;
- no-CoT capability and long-horizon performance;
- monitorability, controllability, and adversarial monitor evasion;
- evaluation, objective, and training awareness;
- sandbagging and oversight gaming;
- safeguard stress tests and residual-risk estimates;
- model-weight security, containment, incidents, and near misses.

Perplexity can tell developers when to look harder. These measurements help determine
what the system can actually do and whether safeguards are adequate.

## Bottom line

OpenAI has provided an important view into its internal pretraining trend. Held-out
code loss appears to have been a durable leading indicator across its model family.

The evidence does not yet support treating 0.8, 0.76, or 0.68 as universal intelligence
thresholds. The values come from an undisclosed code corpus and protocol, and capability
milestones are correlational, internally interpreted, and confounded by other changes.

A standardized compression metric could be a useful precautionary trigger if it is
independently measured, cross-tokenizer, multi-domain, contamination-resistant, and
paired with direct capability and risk evaluations.

The strongest version of Pachocki's proposal is not “perplexity equals intelligence.”
It is that labs need a continuous upstream signal that can trigger safety work before
unknown capabilities become visible. Loss may be one such signal, but it cannot carry
that responsibility alone.

## Sources

[1] https://openai.com/index/perplexity-and-intelligence — Perplexity and Intelligence
[2] https://arxiv.org/abs/2001.08361 — Scaling Laws for Neural Language Models
[3] https://arxiv.org/abs/2304.15004 — Are Emergent Abilities of Large Language Models a Mirage?
[4] https://arxiv.org/abs/2410.08527 — Scaling Laws for Predicting Downstream Performance in LLMs
[5] [CoT monitorability](https://alignment.openai.com/cot-monitorability-model-lifecycle)
[6] https://arxiv.org/abs/2211.09110 — Holistic Evaluation of Language Models
