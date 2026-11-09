---
title: What OPAL Shows About Agent-Adapted Optimizers and Overfitting
author: Better Stack
channel: Better Stack
url: https://youtu.be/0acRokoODvo?is=bQiyhgVyM5fUU7IO
date: 2026-11-08 00:19
tags: ai, development, technology
---

# What OPAL Shows About Agent-Adapted Optimizers and Overfitting

[article](../../articles/better-stack/2026-11-08-opal-reactive-optimizers.md)

## Core result

OPAL lets a coding agent inspect training statistics and rewrite optimizer logic during a
machine-learning run. Better Stack reproduced one noisy-label experiment and reported that
Claude reduced memorization and improved test accuracy relative to fixed AdamW. This does not
show that Claude solved overfitting generally.

The experiment used ResNet-18 on CIFAR-10. Of 45,000 training images, 4,500 received a fixed
wrong class. Another 5,000 clean images supplied validation metrics, and 10,000 clean test
images remained hidden until evaluation. Claude was not told about the bad labels, but clean
validation performance directly revealed when generalization deteriorated.

## Paper and reproduction

The *Reactive Optimizers* paper reports 78.6% test accuracy for OPAL and 73.5% for final
AdamW. All corrupted labels were memorized by final AdamW, compared with 3.7% under OPAL.
A stronger AdamW baseline using validation-selected weight averaging reached 77.5%, reducing
OPAL's advantage from 5.1 percentage points to 1.1.

Better Stack reports a separate run: 79.1% accuracy and 0.70 loss for OPAL, versus 74.4% and
2.39 for fixed AdamW. The agent predicted the assigned wrong class for 250 of 4,500 corrupted
examples. That is 5.6%, not the video's separate “about 4%” figure.

Claude first tried optimizer replacement, flooding, and weight noise. Several changes harmed
performance. It later used large, noisy steps with running weight averages, restored its best
saved model after an overshoot, and froze it. The successful mechanism resembled stochastic
weight averaging, a method published in 2018.

## Caveats

Better Stack's run took about 45 minutes, cost roughly $7.60 in agent tokens, and was more
than three times slower than the fixed run. The video does not publish its exact command,
seed, OPAL version, event log, or checkpoint, so its result is not independently auditable.

The test is engineered to reveal memorization: fixed uniform label corruption, no data
augmentation, long training, and clean validation feedback. The headline paper table is not
a multi-seed study. OPAL also receives much more adaptive capacity than fixed AdamW and may
itself overfit repeated decisions to one validation set.

The project warns that agent behavior varies and can hurt optimized recipes. Its rules against
editing data, models, and evaluation are not a security sandbox; agent-written code executes
inside training. Proprietary hosted model behavior and nondeterministic CUDA further limit
exact reproducibility.
The result demonstrates feasible agent-guided optimizer adaptation. In this controlled task,
Claude diagnosed validation decline, recovered from failed edits, and assembled a useful
known strategy that reduced memorization. General reliability, statistical significance,
cost-effectiveness, and superiority over tuned non-agent methods remain open questions.
