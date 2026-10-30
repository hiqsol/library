---
title: Why Wider Language Models Hit a Scaling Plateau
author: Dan Grib
channel: Dan Grib
url: https://youtu.be/6xQ8LQfkBg4
date: 2026-09-19 14:15
tags: ai, development
---

# Why Wider Language Models Hit a Scaling Plateau

[summary](../../summary/dan-grib/2026-09-19-llm-width-scaling-plateau.md)

*The supplied source does not report that result. Dan Grib's video instead explains a claim
about model width, superposition, interference, and diminishing returns from training-time
scaling. The distinction matters.*

## What the source actually covers

Grib presents a recent paper as **“Superposition Yields Robust Neural Scaling”** and lists it
as an MIT paper published at NeurIPS 2025. The supplied description therefore does identify
MIT, although neither the description nor the transcript names any individual paper authors.
Findings below are attributed to the paper or its researchers only as Grib presents them;
interpretive framing is attributed to Grib.

The video's title says that MIT found a “hard limit in LLM scaling” that money cannot fix.
That is Grib's headline, not a result established in the supplied text about every form of LLM
scaling. In particular, the source never mentions **test-time compute**, inference-time
scaling, repeated sampling, search, verifier-guided reasoning, or longer chains of thought.
It supplies no experiment in which extra test-time compute makes a language model worse.

## The setup Grib describes

Grib starts with the growth from GPT-1 to GPT-2 one year later and GPT-3 another year later.
He says larger models brought better performance and helped establish “bigger equals better.”
GPT-3, he notes, later powered the first version of ChatGPT. He describes the industry as
following this scaling strategy for the last 6 years.

His account focuses on self-supervised learning. An LLM ingests sources such as all of
Wikipedia, hundreds of thousands of books, and a filtered copy of most of the public internet.
With substantial computing power, it learns a mathematical map of relations among words
without being taught explicit grammar rules.

Grib estimates that a working model handles over 50,000 distinct words and concepts, calling
that conservative. Yet its internal space—what he says researchers call its dimensions or
width—is generally only a few thousand units wide. For a model the size of GPT-3, he gives a
width of a bit over 12,000.

The source does not give an experimental protocol, dataset, sample size, training run,
ablation, task suite, or benchmark score. GPT-1, GPT-2, and GPT-3 are historical examples,
not identified test subjects in a reported experiment. No benchmark is named. The extra
resources list GPT-2's 2019 paper, GPT-3's 2020 paper, Chinchilla's 2022 training-compute
paper, and Epoch AI's 2024 paper on frontier-model training costs, but the video does not
report new evaluations on those models or papers.

## Scaling method: width, not test-time compute

In an idealized representation, each of the more than 50,000 concepts would have an
independent direction. Because width is smaller than the concept count, Grib says models do
not merely discard low-value concepts. Instead, they pack concepts into overlapping
internal directions. He calls this **superposition**, crediting Anthropic's 2022 paper
“Toy Models of Superposition” for laying out the concept.

His examples of potentially nearby concepts are banana, elephant, bunk, balloon, and the
semicolon. The packing works because every concept is not needed at the same instant in a
sentence. But activating one concept can weakly activate a neighbor. Grib calls that bleed
**interference** and says it can push a model toward a slightly wrong or completely wrong
word.

As Grib reports the paper's formula, doubling model width halves interference. Because he
frames interference as a source of errors, he says the same doubling also halves those
errors. This is the **one-over-width** relation: more dimensions let the same crowded set of
concepts spread farther apart.

This is a parameter- or architecture-scaling argument tied to training a wider model. It is
not a method that spends more computation on a prompt after training. The supplied material
therefore cannot support the requested failure pattern—performance worsening as test-time
compute rises—or any quantitative test-time curve.

## The failure pattern that is actually claimed

The described pattern is diminishing economic return followed by saturation, not worsening.
A wider model has less overlap and interference until each genuinely independent feature can
occupy its own direction. At that ceiling, superposition disappears, so there is no remaining
interference for additional width to reduce. Grib says making the model wider after that
point buys “absolutely nothing.” He does not say accuracy reverses or that error increases.

Grib also says total error does not extrapolate to zero. Language has irreducible ambiguity:
a sentence beginning “I really like” could reasonably continue with cats, dogs, or pizza.
Unlike the equation 2 + 2 = 4, such data may have no single correct next word. Perfect
prediction was therefore never available merely by increasing width.

## Quantitative claims and the role of money

Grib gives the following exchange rates and cost illustration:

- Doubling width cuts interference in half and, in his account, halves related errors.
- Every width doubling raises training cost by 6 times, described as conservative.
- A present-day frontier model is said to cost about $300 million to train.
- Successive doublings are estimated at about $1.8 billion, $11 billion, $65 billion, and
  $390 billion for one model.

He argues that even free energy, nuclear fusion, or an unlimited-money “glitch” would not
change the error exponent. As Grib presents the researchers' explanation, **Zipf's law**
locks the one-over-width exponent through the frequency distribution of language: a few words,
such as “that” and “is,” occur extremely often, while many words, such as “photosynthesis”
and “kaleidoscope,” occur very rarely.

Money could, in this account, buy wider models along the same costly curve. It could not make
that curve steeper, remove language's irreducible ambiguity, or create further gains after
superposition had been eliminated. But the supplied source does not establish that money
cannot improve systems through better data, algorithms, architectures, multimodality,
training objectives, hardware, retrieval, tools, or test-time methods.

## Practical implications

If Grib's presentation is accurate, simply widening dense language models faces three limits:
6-times cost for each doubling, a one-over-width improvement rate constrained by Zipf's law,
and a saturation point once width matches the number of genuinely independent linguistic
features. Practitioners should distinguish eliminating representational interference from
solving every source of model error.

Grib interprets these limits as one reason some researchers are moving toward systems with a
“proper understanding” of the physical world that learn from video and senses rather than
human text alone. That is his commentary about a possible direction, not a benchmarked
finding reported in the supplied material.

## What this does—and does not—establish

On the supplied evidence, the paper as presented by Grib proposes a mathematical account of
robust neural scaling through superposition. It links width to interference and predicts
halving a component of error when width doubles, followed eventually by no width-derived gain.

It does **not** establish that:

- more test-time compute makes models worse;
- all LLM performance follows a single one-over-width curve;
- total model error is identical to interference error;
- every scaling axis has reached, or soon will reach, a hard ceiling;
- GPT-1, GPT-2, GPT-3, ChatGPT, or Chinchilla was tested in the reported study;
- any named benchmark deteriorated under added compute; or
- money cannot fund progress by routes other than brute-force width scaling.

The absence of tasks, benchmark results, confidence intervals, model configurations, and an
experimental procedure in the supplied transcript prevents a stronger empirical conclusion.
It also prevents assessment of where the proposed ceiling lies in real systems.

## Source limitations

This account uses only the supplied description and timestamped English automatic captions.
Automatic captions may mishear names, equations, technical wording, and numbers. One caption,
for example, renders a sentence as “there's no one in offering,” which likely does not reflect
the intended wording. The transcript also contains the fragment “models like GPT-3 and,”
suggesting an omitted or mistranscribed model name.

The description supports the MIT affiliation by labeling “Superposition Yields Robust Neural
Scaling” as “MIT, NeurIPS 2025.” It does not provide author names. Without the paper text, the
video's mathematical claims, costs, attributions, and interpretation cannot be independently
checked. The defensible conclusion is narrow: Grib describes limits to gains from increasing
model width; the source does not document a test-time-compute experiment or a result in which
more test-time computation makes a language model worse.
