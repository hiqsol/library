---
title: Geometry, Efficient Models, and the Limits of a Startup’s AI Claims
author: Julian D. Michels
channel: Sophontic AI
url: https://youtu.be/4S8I22ybG2c?is=3PbgGIgU7G5QDJ22
date: 2026-08-06 14:39
tags: ai, technology
---

# Geometry, Efficient Models, and the Limits of a Startup’s AI Claims

[article](../../articles/julian-d-michels/2026-08-06-geometric-reasoning-ai-infrastructure.md)

Sophontic’s interview with founder Julian D. Michels presents a promising research direction as a
sweeping challenge to scale-based AI. The grounded core is that neural representations have
analyzable high-dimensional geometry. Causal interpretability work shows that some internal
features and circuits shape behavior. Geometry and statistics are not opposites: statistical
optimization creates that geometry.

Michels says Sophontic identifies structures associated with reasoning and trains them into small
models, but the interview does not disclose an inspectable method.

Its paired perturbation test is sensible: change a load-bearing detail and require correct answers
to both the original and altered problem. Contrast Sets and CheckList show that such tests can
expose shortcuts, but passing them does not by itself prove general reasoning. Controls must rule
out templates, artifacts, contamination, and benchmark overfitting.

Sophontic describes a 124M prototype outperforming models up to 60× its size. That is a
parameter-count comparison, not proven 60× performance, compute, or energy. The 1,000× figure is
unverified; Michels himself says, “We don’t know.”

At the 2026-09-29 cutoff, the prototype, method, weights, model card, evaluation kit, comparison
tables, energy measurements, and independent replication were unreleased. The company-published
interview ends with an investor and engineer solicitation, so its technical and future claims
require particular scrutiny.

Small and on-device models are real, as are efficient methods such as QLoRA. Local inference or
adapter tuning is not equivalent to full continual foundation-model training, which still faces
compute, forgetting, poisoning, privacy, and stability problems. The AlphaFold analogy is
misleading: specialization and biological priors mattered, but its success also required major
databases, researcher effort, and centralized TPU training.

Smaller models may improve privacy and access, yet model size alone does not decentralize chips,
data, distribution, ownership, or governance. The interview’s claims about liberation,
consciousness, and shared cosmic geometry remain philosophical speculation rather than
consequences of the reported benchmark. Michels’s doctorate is from a
psychology/consciousness-oriented program, not ML or CS; that is relevant context, while the
technical proposal still turns on reproducible evidence.

The cited Anthropic “spiritual bliss attractor” also needs experimental context. Recurring
model-to-model themes can reflect prompts, post-training, sampling, and feedback; they do not
establish desire, consciousness, or a formal topological attractor. The claim that data centers
will become obsolete should be rejected. The IEA projects their electricity use rising from 415
TWh in 2024 to about 945 TWh in 2030: https://www.iea.org/reports/energy-and-ai/executive-summary

A hybrid architecture is more likely: capable edge models for suitable private or low-latency
tasks, alongside cloud systems for training, storage, reliability, and large-scale serving.
Sophontic may have a useful method, but only a public release and independent replication can
separate that possibility from the interview’s promotional extrapolation.
