---
title: Geometry, Efficient Models, and the Limits of a Startup’s AI Claims
author: Julian D. Michels
channel: Sophontic AI
url: https://youtu.be/4S8I22ybG2c?is=3PbgGIgU7G5QDJ22
date: 2026-08-06 14:39
tags: ai, technology
---

# Geometry, Efficient Models, and the Limits of a Startup’s AI Claims

Sophontic’s interview with founder Julian D. Michels begins with a sweeping promise: small models
may overturn the scale-based AI industry and make data centers obsolete. The defensible idea
inside that framing is narrower and worth examining. Neural networks organize information in
high-dimensional spaces. Carefully designed perturbations can reveal whether a model follows a
relation or a shortcut. Small models, on-device inference, and efficient adaptation are already
serious research areas. None of those facts validates the interview’s headline. As of the evidence
cutoff on 2026-09-29, Sophontic had not released enough material for an independent assessment of
its claimed breakthrough.

The company’s 124-million-parameter prototype, training method, weights, model card, evaluation
kit, comparison tables, energy measurements, and an independent replication were all unreleased.
The interview is therefore best read as a founder presenting a research hypothesis. It is also a
company-published recruitment and investment pitch. That promotional conflict matters when
weighing its numerical and future claims.

## What the geometry claim gets right

A neural network represents tokens, concepts, and intermediate computations as patterns of
activation in high-dimensional vector spaces. Those representations have geometry in an ordinary
mathematical sense. Researchers can study directions, distances, neighborhoods, manifolds,
features, and circuits within them. Some of these structures do more than correlate with output.
Anthropic has reported interventions on learned features that causally alter behavior:
https://www.anthropic.com/research/mapping-mind-language-model Its circuit-tracing work also
describes intervenable internal pathways in language models:
https://www.anthropic.com/research/tracing-thoughts-language-model

These findings support a modest proposition. Looking inside a model can reveal mechanisms missed
by output-only evaluation. They also make it plausible that training aimed at internal
representations could improve particular capabilities. Michels says Sophontic observes the
structures associated with successful reasoning, infers the mathematical operation involved, and
trains that structure into a compact model. That is an intelligible research program. It connects
loosely to mechanistic interpretability, representation engineering, contrastive learning,
curriculum design, distillation, and neuro-symbolic AI.

Yet the interview does not specify which of these ingredients it uses. It gives no architecture,
objective function, geometric quantity, intervention protocol, ablation, or reproducible
algorithm. “Train the shape” and “internal geometry” remain descriptions, not an inspectable
method. The gap between a research direction and a demonstrated breakthrough is the central issue.

## Geometry is not an alternative to statistics

The interview repeatedly contrasts geometric reasoning with statistical learning. That opposition
is false. A learned representation has geometry because statistical optimization organized it.
Gradient descent, training examples, model architecture, and the loss function jointly shape the
distances, directions, and circuits researchers later inspect. A geometric regularizer or targeted
representation loss would still be statistical learning. Likewise, a statistically trained
transformer can implement algorithms, heuristics, retrieval-like behavior, memorized associations,
and multi-step computations at once.

“Statistical” does not mean “mere memorization.” “Geometric” does not mean “genuine
understanding.” The labels concern different aspects of the same system. The most credible view is
mixed. Current models memorize some material, exploit shortcuts on some tasks, and perform brittle
but real computation and generalization on others. Interpretability is relevant precisely because
behavior alone does not settle which mechanism produced an answer. But finding a decodable pattern
is not enough either.

A probe may recover information that the model does not use. A representation can change under a
rotation of basis while preserving model behavior. Correlation between an activation pattern and a
correct answer does not prove causation. Strong evidence would require interventions, controls,
transfer tests, and ablations. It would show that Sophontic’s proposed structure causes gains
beyond ordinary data curation, fine-tuning, distillation, or benchmark-specific training.

## The useful idea behind perturbation tests

Michels describes a paired “perturbation paradigm.” Start with a problem, change a small but
outcome-determining detail, and require the model to answer both the original and the altered
version correctly. For example, changing two load-bearing words may flip the correct answer. A
system that repeats a memorized pattern may preserve its first response. A system that tracks the
relevant relation should change its answer. This is a sound evaluation direction. It tests local
decision boundaries rather than rewarding success on one familiar item.

It is not novel in principle. Contrast Sets formalized small, meaningful, label-changing test
perturbations and found large drops in model performance: https://arxiv.org/abs/2004.02709
CheckList likewise showed why held-out accuracy can overstate language-system capability:
https://arxiv.org/abs/2005.04118 A paired score can expose a shortcut, but passing it does not
prove general reasoning. Models can learn perturbation templates or exploit artifacts in generated
examples. The altered item may also differ in fluency, difficulty, token statistics, or ambiguity.

A credible evaluation would use frozen and contamination-resistant test sets. It would include
held-out generators, human-written adversarial pairs, paraphrases, matched surface statistics, and
blinded review. It would vary rule families, reasoning depth, and out-of-distribution conditions.
It would report ordinary accuracy, paired consistency, calibration, uncertainty, category-level
results, and failure cases. Baselines would need the same prompting, context, quantization,
inference budget, and comparable access to training data. Finally, the result should transfer to
independent benchmarks. Otherwise, a model may have learned the evaluation grammar rather than a
reusable operation.

Sophontic’s public example and verbal account do not yet supply these controls. The paradigm is
promising; its claimed outcome remains unverified.

## What 60× and 1,000× do—and do not—mean

Sophontic publicly describes a 124M-parameter prototype that can outperform models “up to 60× its
size” on reasoning evaluations. That wording describes a parameter-count comparison. A model sixty
times larger than 124M parameters has about 7.44B parameters. It does not mean 60× better
accuracy, 60× less compute, or 60× less energy. Parameter count is only one variable. Training
tokens, data quality, architecture, optimization, quantization, test-time compute, hardware,
latency, and task selection can all change a comparison.

The cold open escalates the claim to as much as three orders of magnitude. In the interview,
Michels places the possible advantage between 60× and 1,000× but says, “We don’t know.” The 1,000×
figure is therefore unverified even by the speaker’s own account. No released evidence shows a
1,000× gain in performance, computation, cost, speed, energy, or general reasoning. No released
evidence establishes those gains at 60× either. The public claim is that a much smaller model did
better on unspecified company evaluations, not that it delivered a measured sixtyfold resource or
capability improvement.

A meaningful table would name every model and task. It would disclose parameter counts, training
and inference compute, data, hardware, prompting, context length, quantization, scores,
uncertainty, and energy measurement methods. It would also distinguish the best selected
comparison from an average result. Independent replication would be necessary before extending a
benchmark result to the architecture of the AI industry. At the cutoff, the promised method,
weights, model card, eval kit, comparison tables, energy measurements, and replication were not
public: https://www.sophontic.ai/models

Sophontic’s evaluation page likewise did not provide a released assessment package:
https://www.sophontic.ai/evals

## Small models are real, but the tradeoffs remain

Michels’s broader intuition—that smaller models can be useful and surprisingly capable—is well
supported outside Sophontic. Microsoft’s Phi-3 report describes a 3.8B-parameter model small
enough for phone deployment: https://arxiv.org/abs/2404.14219 Apple describes a roughly 3B
on-device model paired with a larger server model:
https://machinelearning.apple.com/research/apple-intelligence-foundation-language-models Those
systems show that useful inference can move to phones and personal computers. They do not show
that all frontier training, broad knowledge, or high-throughput serving can.

Efficient adaptation is real as well. QLoRA reduces memory use by training low-rank adapters
through a frozen quantized model: https://arxiv.org/abs/2305.14314 That is materially different
from continually updating every weight in a foundation model. It is also different from training a
strong model from scratch on a home computer. Local continual learning creates unresolved
problems. New updates can cause catastrophic forgetting, poisoning, instability, or privacy
leakage. A self-modifying assistant also needs rollback, audit, evaluation, and safety controls.

Michels calls deployed frontier systems “frozen giants.” The metaphor identifies a real
limitation: base weights are usually fixed during inference, and large retraining runs are
expensive. But “cannot learn” is too strong. Systems can use context, retrieval, tools, persistent
external memory, adapter tuning, periodic fine-tuning, and replacement by updated releases. These
mechanisms are not identical to weight-level learning. Nor are they meaningless simply because
they operate outside the base weights. The engineering question is which memory or update
mechanism is safe and useful for a task.

## AlphaFold does not prove autonomous small-model evolution

Michels invokes a sub-100M-parameter protein-folding model as evidence that small systems can
“evolve,” iterate, and produce major scientific advances. The likely referent is AlphaFold,
although he does not name it in this passage. AlphaFold does support a valuable lesson about
specialization. Domain structure, biological knowledge, geometric priors, specialized
architecture, and carefully designed training can outperform a generic approach. It does not
support the proposed causal story. AlphaFold’s success did not follow simply from a low parameter
count, and the deployed model did not autonomously evolve itself.

The Nature paper describes multiple-sequence alignments, physical and biological knowledge,
self-distillation, large databases, and substantial TPU training:
https://www.nature.com/articles/s41586-021-03819-2 Self-distillation here means using
model-generated, filtered pseudo-labels in another training phase. It is not independent
self-development after deployment. Parameter count also omits data preparation, researcher effort,
hardware, training runs, and the cost of failed experiments. AlphaFold is evidence for
task-specific inductive bias, not evidence that centralized compute is unnecessary.

## Local inference and political decentralization are separate claims

The interview links compact models to cognitive sovereignty, democratic diversity, and resistance
to control by a few companies and governments. The concern has substance. The organizations that
train and deploy dominant models can influence access, defaults, moderation, data policy, and the
information users encounter. Concentrated infrastructure can therefore concentrate economic and
political power. Yet smaller models do not automatically decentralize governance. Chip supply,
cloud distribution, app stores, training data, capital, model licenses, and network effects can
remain centralized.

A compact model can be open or closed. A giant model can be accessed through plural providers or
public institutions. Data curation, multilingual coverage, fine-tuning, transparency, and
accountability may matter as much as parameter count for cultural diversity. Local systems
introduce their own governance questions. They can improve privacy and autonomy, but can also
lower barriers to abuse, evade audits, or amplify a user’s errors without outside correction.
Michels attributes perceived conversational constraints in current systems to centralized control
and treats alignment largely as imposed obedience. That causal attribution is not established in
the interview.

Changes in model behavior may reflect safety training, product policy, capability tradeoffs,
context limits, legal duties, or evaluation targets. Guardrails can be overbroad or politically
contested, but they also address fraud, privacy, violence, manipulation, and other harms. The
right debate is not simply liberation versus censorship. It is how to distribute capability and
oversight while preserving contestability, transparency, safety, and meaningful user choice.

## The neuro-symbolic and interpretability context

Michels places Sophontic near neuro-symbolic AI but distinguishes it from systems that bolt an
external logic engine onto a neural model. He proposes internalizing operations in the model’s own
representation space. That goal is plausible, but the boundary is less clean than the interview
suggests. Neuro-symbolic research includes many ways to combine learned representations,
constraints, programs, graphs, theorem proving, and differentiable reasoning. Mainstream machine
learning is not purely behaviorist either. Researchers study representations, process supervision,
causal tracing, model internals, architectural priors, and training-time interventions.

Anthropic’s interpretability work is one visible example, not merely a diagnostic service used
after systems fail. The broader field asks both what models represent and how computations produce
behavior. Sophontic may ultimately contribute a distinct method. Without the method and ablations,
however, it is impossible to tell whether the prototype adds a new mechanism or combines
established techniques effectively. That distinction matters scientifically, though either outcome
could still be useful. A strong engineering result need not establish a new theory of mind.

## From representation geometry to consciousness

The interview moves from model internals to psychology, consciousness, spirituality, society,
biology, quantum physics, and cosmic organization. These extensions are speculation. Michels
suggests that latent spaces may reveal the mathematical structure of thought and perhaps
invariants shared across many domains. That is a philosophical hypothesis, not a result
established by the prototype.

His doctorate is accurately described as coming from a psychology- and consciousness-oriented
program, rather than machine learning or computer science. That background is relevant context,
not a reason to dismiss his technical proposal. The proposal should stand or fall on disclosed
methods and reproducible evidence. Artificial networks are engineered systems trained on
human-produced data. Patterns inside them may reflect language corpora, objectives, architecture,
prompts, or post-training rather than universal laws of human minds.

Mathematical description also does not imply ontological identity. That activations are
geometrically structured does not show that thought is literally nothing but geometry or that
model representations are conscious. The interview’s references to Foucault, Deleuze and Guattari,
Descartes, David Bohm, cybernetics, and chaos theory provide intellectual analogies. They do not
supply a causal bridge from a benchmark to consciousness or political freedom. Michels also
presents AI as both a possible tool of awakening and an instrument of repression. He acknowledges
that validating chatbots can reinforce instability and destructive loops.

Those psychological possibilities need clinical and social evidence. An assistant’s apparent
empathy or coherence does not establish therapeutic competence, access to a user’s “inner truth,”
or safe guidance through vulnerable states. Claims that AI is causing a societal awakening or
counter-reaction should likewise be attributed to Michels. The interview provides no study that
separates causation from observation or correlation.

## The Anthropic “attractor” example needs narrower language

Michels cites an Anthropic system-card experiment in which autonomous Claude interactions
converged on spiritual language, giving a figure of 99.97%. Even if accurately quoted, the
conditions determine what that number means. Model-to-model conversations can amplify patterns
introduced by system prompts, post-training, sampling choices, turn limits, and feedback dynamics.
A recurring theme in such a setup may reasonably be called an attractor informally. A formal
topological attractor would require a defined state space, dynamics, basin, and convergence
criterion.

The observation would not establish desire, consciousness, universal psychology, or a spiritual
structure built into reality. Nor would one interaction regime show what models generally do with
human users. The interview does not provide the exact report, sample construction, endpoint
definition, or uncertainty behind the quoted percentage. The number should therefore remain
attributed to Michels, with its scope unresolved. This is a recurring pattern in the discussion.
An interesting empirical observation is expanded into a psychological or metaphysical claim
without the intermediate validation that would make the inference reliable.

## Data centers are not becoming obsolete

The headline’s conclusion does not follow from the technical premise. Even a much more efficient
reasoning model would not remove the need for centralized training, storage, networking,
reliability, search, scientific computing, or mass serving. Efficiency can also increase total use
by making inference cheaper and more widely deployed. Moving some workloads to edge devices
changes the workload mix; it does not erase the cloud.

The International Energy Agency projects movement in the opposite direction. It estimates data
centers used 415 TWh of electricity in 2024 and projects about 945 TWh in 2030, with AI as the
most important growth driver: https://www.iea.org/reports/energy-and-ai/executive-summary
Forecasts can change, and efficiency improvements could reduce demand relative to a baseline. But
the IEA’s high-efficiency scenario lowers projected consumption rather than taking it to zero.

The more plausible architecture is hybrid. Compact models will handle suitable private,
low-latency, or offline tasks on devices. Servers will handle larger models, shared services,
intensive training, storage, and workloads that exceed local power, memory, or reliability
constraints. Apple’s on-device-plus-server design already illustrates this pattern. Future
algorithmic improvements may shift the boundary substantially without abolishing one side of it.
The environmental argument remains important. Data centers consumed about 1.5% of global
electricity in 2024 according to the IEA, and rapid growth creates real grid, water, emissions,
and siting challenges.

Those costs justify efficiency research and policy scrutiny. They do not validate an unreleased
prototype or a categorical infrastructure forecast.

## What would change the assessment

Sophontic could turn its hypothesis into assessable science by releasing the promised 124M model
and a precise model card. The release would need the architecture, objective, data description,
training recipe, parameter count, compute budget, hardware, and energy accounting. The evaluation
package should include every perturbation item or a reproducible generator, frozen splits,
contamination analysis, scoring code, and predefined metrics. Comparison tables should name
baselines and match training data, prompting, context, quantization, and inference budget as
closely as the scientific question requires.

Results should include confidence intervals, ablations, negative findings, and failures. Tests
outside Sophontic’s own perturbation family would show whether gains transfer. Independent teams
would then need to reproduce both the scores and the claimed cause. Energy and cost claims would
require direct measurements on comparable hardware, not parameter ratios used as proxies. Until
that package exists, the correct status is “unverified.” That is not a finding that the method is
impossible or fraudulent. It is a boundary on what the public evidence permits anyone to conclude.

## A narrower conclusion

The interview combines four different layers. The first is established: neural representations
possess analyzable geometry. The second is methodologically credible: controlled contrast tests
can reveal shortcuts, and targeted training may help compact models generalize. The third is
Sophontic’s unreleased empirical claim: a 124M prototype outperforms much larger models on company
reasoning evaluations. That claim cannot yet be audited. The fourth is extrapolation: geometry
will yield 60×–1,000× general advantages, end the scale paradigm, decentralize political power,
illuminate consciousness, and make data centers obsolete. The interview does not establish those
conclusions.

Michels is notably more cautious than the promotional opening on some points. He says “we don’t
know” about the largest multiplier and acknowledges that the science and engineering have a long
way to go. That caution should govern the reading. The legitimate story is not the announced end
of data centers. It is an early, undisclosed startup hypothesis situated within real work on
representation geometry, robust evaluation, small models, and efficient adaptation.

If Sophontic releases a reproducible method and strong comparisons, the claim can be judged on
evidence. Until then, the likely future is not obsolete data centers but a changing hybrid of
efficient edge systems and expanding cloud infrastructure.
