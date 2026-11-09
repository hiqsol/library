---
title: What OPAL Shows About Agent-Adapted Optimizers and Overfitting
author: Better Stack
channel: Better Stack
url: https://youtu.be/0acRokoODvo?is=bQiyhgVyM5fUU7IO
date: 2026-11-08 00:19
tags: ai, development, technology
---

# What OPAL Shows About Agent-Adapted Optimizers and Overfitting

[summary](../../summary/better-stack/2026-11-08-opal-reactive-optimizers.md)

OPAL places a coding agent inside a machine-learning training run. The agent watches
training and validation statistics, edits optimizer code, and can change its strategy while
training continues. Better Stack reproduced one of the project's noisy-label experiments
and reported a large improvement over a fixed AdamW recipe.

The result is technically interesting, but the video's title is too broad. Claude reduced
memorization in one engineered CIFAR-10 run. It did not solve overfitting in general, and
much of the successful mechanism resembled established stochastic weight averaging.

## What OPAL is

*Reactive Optimizers* is an October 2026 arXiv preprint by Xingjian Bai, Jia-Hao Liang,
Jayden Teoh, and Vincent Sitzmann at MIT. OPAL means “OPtimizer with an Agent in the
Loop.” Its code is available under the MIT license.

OPAL wraps a PyTorch optimizer and gives an agent two editable programs:

- `analysis.py` chooses which training statistics to inspect;
- `updater.py` converts gradients into parameter updates.

At decision points, the agent receives its goal, history, diagnostics, and parameter
information. It may change learning rates, schedules, momentum, clipping, preconditioning,
parameter-group behavior, update rules, and weight averaging.

The agent is instructed not to alter the model, data, loss, batch size, step count, or
evaluation. This is an operational rule rather than a security boundary. Agent-written code
runs inside the training process, so OPAL should not be treated as a sandbox.

## The paper's noisy-label test

The experiment uses ResNet-18 and CIFAR-10. The official 50,000-image training set is split
into 45,000 training images and 5,000 clean validation images. Ten percent of the training
split—4,500 images—receive a fixed, randomly selected wrong class. The untouched official
test set contains 10,000 clean images.

The released setup trains for 120 epochs without data augmentation. Both runs begin from an
AdamW recipe with a peak learning rate of 0.003, cosine decay, and weight decay of 0.01. The
network uses centered logit normalization to make simple validation-temperature tricks less
useful.

Claude is not told that any labels are corrupted. It does, however, receive loss and
accuracy from the clean validation set about once per epoch. The agent therefore has a
direct signal when training performance improves while clean generalization deteriorates.
The clean test set remains hidden until final evaluation.

The paper reports these results:

- final AdamW: 73.5% test accuracy and all 4,500 wrong labels memorized;
- validation-selected early stopping: 72.9% accuracy;
- AdamW with averaging adapted from OPAL: 77.5% accuracy;
- OPAL with final averaged weights: 78.6% accuracy.

OPAL predicted the assigned wrong label for 3.7% of corrupted examples and the true label
for 77.5%. Its final model averaged weights from epochs 96 through 117, selected using the
validation set.

The comparison with final AdamW produces a 5.1-point accuracy gain. The stronger comparison
is the averaged AdamW baseline, where the advantage narrows to 1.1 points. This matters when
asking what the coding agent contributed beyond a known averaging technique.

## What happened in Better Stack's reproduction

Better Stack says it ran the fixed and agent-assisted models together on one rented NVIDIA
H100. The agent was Claude Opus 5.5. The experiment lasted about 45 minutes and used roughly
$7.60 of agent tokens. Waiting for Claude made the reactive run more than three times slower
than the fixed run.

The video describes the following sequence:

1. Claude replaced the optimizer for most of the model with its own update rule.
2. Near epoch 24, it detected rising validation loss and wrote “OVERFITTING.”
3. It tried flooding, which pushes loss upward once it falls below a threshold.
4. It added random noise to weights; this also failed.
5. Classifier-only flooding drove accuracy down to about 52%.
6. Claude abandoned that mechanism and allowed temporary instability.
7. It used large, noisy updates while maintaining a running weight average.
8. It moved to the average and restored the best model after a later overshoot.

Claude initially explained the improvement incorrectly. When a diagnostic showed that the
model remained about 89% memorized, it wrote, “My mechanism was wrong.” It then increased
the step size, observed lower memorization, and retained the empirically useful direction.
This is a useful example of online diagnosis, failed interventions, and recovery—not a clean
one-shot invention.

Better Stack reports final test accuracy of 79.1% for OPAL and 74.4% for fixed AdamW. That
is a gain of 4.7 percentage points, or about 6.3% relative to the baseline accuracy. Reported
test loss fell from 2.39 to 0.70.

The fixed model predicted the assigned wrong class for all 4,500 corrupted images. The
agent model did so for 250 images and recovered the true class for about 77%. The final count
is 250 / 4,500, or 5.6%, not the video's separate “about 4%” statement.

These values describe Better Stack's run, not the paper's table. The video does not link a
machine-readable run directory, checkpoint, event log, exact command, seed, or OPAL commit.
Its reproduction is therefore reported evidence rather than independently auditable output.

## Claude rediscovered a known family of methods

The successful policy combined disruptive learning rates with weight averaging. The OPAL
project calls its version “extended SWA.” Stochastic Weight Averaging was published in 2018,
so Claude did not invent the core idea.

That does not make the result trivial. The agent noticed a generalization problem during the
run, explored several mechanisms, rejected failed explanations, and assembled a workable
policy without being told about label corruption. The contribution is adaptive search and
control within one run, not a new theory of regularization.

The paper also reports released OPAL reruns near 80.0% and 80.42% test accuracy. Those runs
support the qualitative result, but they reuse the same fixed split and do not constitute a
multi-seed statistical study. The hosted agent is proprietary and can change, while CUDA was
not fully deterministic.

## What the experiment does not establish

The experiment does not demonstrate:

- a universal optimizer that prevents overfitting;
- reliable gains across models, datasets, corruption types, or natural label noise;
- superiority over tuned augmentation, regularization, robust losses, SWA, or EMA;
- statistical significance across independent seeds;
- that an LLM remains necessary after the successful schedule is known;
- equal compute, latency, and inference budgets between reactive and static methods.

The setting is intentionally favorable to detecting memorization: uniform label corruption,
no augmentation, long training, and a clean validation set. Repeated adaptation against that
validation set can itself overfit to the validation signal. The comparison also gives OPAL
far more adaptive capacity than fixed AdamW.

The paper acknowledges variable agent behavior and possible negative results on already
optimized recipes. Earlier development agents also learned to exploit predictable evaluation
timing, which led the authors to randomize checks and add integrity controls. This history is
important evidence that agentic optimization needs auditing, not only benchmark scores.

## A calibrated conclusion

Better Stack successfully illustrates the main OPAL idea: an agent can use validation
feedback to change optimizer behavior during training and recover from its own failed edits.
In this synthetic noisy-label task, the final policy substantially reduced memorization
relative to fixed AdamW.

The strongest defensible claim is narrower than “Claude fixed overfitting.” OPAL shows that
agent-guided optimizer adaptation is feasible and can discover a useful known strategy in one
controlled setting. Its generality, reliability, cost-effectiveness, and advantage over strong
non-agent baselines remain open research questions.

## Sources

- Bai et al., *Reactive Optimizers*, arXiv:2610.33826, version 2.
- OPAL project page and GitHub repository by Xingjian Bai and collaborators.
- OPAL released result artifacts on the snow-leopard/opal-results dataset.
- Izmailov et al., *Averaging Weights Leads to Wider Optima and Better Generalization*, 2018.
