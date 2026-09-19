---
title: Software 3.0 and the Transformer as a Graph Computer
author: Andrej Karpathy
channel: Perfology Clips
url: https://youtu.be/Rlk0GLRWwTI?is=aN9QGYGnzZ-WG0oV
date: 2026-09-08 04:30
tags: ai, development
---

# Software 3.0 and the Transformer as a Graph Computer
## Source caveat
This 2026 Perfology Clips upload appears edited and spliced from older Karpathy talks.
Abrupt cuts near 22 and 24 minutes mean the upload date does not date every segment.
Its English automatic captions contain errors, so uncertain terms and numbers stay caveated.
## From code to prompts
Karpathy calls explicit algorithms Software 1.0, the dominant model for about 70 years.
Software 2.0 makes the dataset source, training the compiler, and weights the program.
His Tesla data engine cycled through training, deployment, telemetry, failures, and labels.
Software 3.0 makes the prompt a runtime program, while the earlier two layers remain.
Few-shot examples let GPT infer a task without changing weights: in-context learning.
Karpathy reports “Let's think step by step” moving one benchmark from 17% to 78.7%.
A longer correctness-focused prompt reached 82%; his explanation is distribution selection.
The 16-ball puzzle yields 4 blue golf balls, showing how extra tokens can aid computation.
## Simulators, memory, and modalities
GPT can simulate a terminal, JSON smart home, app backend, or Bing's alleged Sydney persona.
A fake `ping bbc.com` returned about 24.9 ms and a false IP: simulation is not execution.
Karpathy proposes fixed context plus an external scratchpad and forecasts tool-using agents.
He also anticipates specialists such as doctor GPTs, possibly routed as mixtures of experts.

Images become patches, speech becomes spectrogram slices, and trajectories become tokens.
ViT, Whisper, Decision Transformer, and AlphaFold illustrate architectural convergence.
Type and position embeddings preserve modality and order; masks encode allowed connections.
Karpathy says stronger priors help with little data, while abundant data may need fewer.

## Attention as a graph computer

Bahdanau attention softened the LSTM encoder bottleneck with weighted source-state search.
The 2017 Transformer kept attention and added positions, residuals, MLPs, norms, and heads.
Karpathy frames attention as data-dependent message passing on a directed graph.
Queries state what destinations seek; keys advertise sources; values carry their content.
Softmax normalizes Q-K scores to weights summing to 1, then values are weighted and summed.
Heads repeat this in parallel; layers repeat it in series; MLPs compute at each node.

Encoders connect all tokens; decoders use triangular masks to block future-answer leakage.
Cross-attention uses decoder queries with final encoder keys and values.
Thus GPT is decoder-only, BERT encoder-only, and T5 encoder-decoder.
Karpathy treats gradient-like inner learning in activations as speculation, not settled fact.

## Scale, code, and the central claim

Unlike a serial, long-thin RNN graph, a Transformer is shallow, wide, and GPU-parallel.
Residual paths and normalization aid optimization; hardware efficiency enables larger scale.
nanoGPT is about 300 lines and reportedly reproduced GPT-2 in 38 hours on one GPU node.
Its 4 x 8 toy batch gives roughly B x T examples; causal masking sets future weights to zero.
Karpathy's conclusion: GPT is a general-purpose text computer reconfigured by its prompt.