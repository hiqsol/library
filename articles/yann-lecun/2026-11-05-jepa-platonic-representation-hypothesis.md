---
title: Good-View JEPAs Align Modalities Efficiently but Do Not Prove AGI
author: Yann LeCun
channel: TheAIGRID
url: https://youtu.be/_fEqQa5hBmI?si=fE4mSq_IcDewcn8x
date: 2026-11-05 09:45
tags: ai, technology
---

# Good-View JEPAs Align Modalities Efficiently but Do Not Prove AGI

[summary](../../summary/yann-lecun/2026-11-05-jepa-platonic-representation-hypothesis.md)

A new paper by Randall Balestriero and Yann LeCun supplies a conditional theorem for when
separately trained representations from different modalities become equivalent up to rotation.
Its experiments also show that a 109-million-parameter text JEPA aligns more closely with
image-model representations than two 70–72-billion-parameter language models on specific
neighborhood metrics.

That is a substantive result. It does not show that the small model is a better language
model, that it understands the physical world, that next-token prediction cannot reach
human-level intelligence, or that LeCun has proved the AI industry wrong. TheAIGRID states
several benchmark numbers correctly but repeatedly turns representation alignment into world
understanding and then into an AGI forecast.

## The paper and the hypothesis

*Proving and Improving the Platonic Representation Hypothesis with JEPAs* was posted to arXiv
on October 29, 2026. Its authors are Randall Balestriero and Yann LeCun. Both list AMI Labs;
Balestriero also lists Brown University and LeCun lists New York University.

The work extends the 2024 *Platonic Representation Hypothesis* paper by Minyoung Huh, Brian
Cheung, Tongzhou Wang, and Phillip Isola. That earlier paper observed that representations
from different models and modalities can become more similar as capabilities improve. It
presented a hypothesis, limitations, and counterexamples rather than a universal law.

The new paper asks when this alignment should occur and how a learning objective can encourage
it. Its central idea is that representations are shaped by the graph formed by positive
training pairs. If two modalities connect the same underlying world states in the same way,
their optimal embeddings can share the same geometry even though their observations differ.

## What the theorem actually proves

The main Platonic Representation Theorem starts with a finite set of latent world states. Each
modality is assumed to be an injective rendering of those states, so every observation
preserves all information needed to identify its state. Each modality uses the same
distribution of positive pairs at the world-state level.

The result also assumes:

- population optima rather than ordinary finite-sample neural-network training;
- matched state distributions across modalities;
- a rotation-invariant objective and anti-collapse term;
- minimizers that are unique up to rotation;
- an identity predictor that directly compares embeddings.

Under those conditions, the optimal encoders learn the same world-state representation up to
one orthogonal transformation per modality.

For a concrete spectral formulation, the paper uses centered and whitened embeddings, squared
embedding distance, an embedding dimension below the number of states, and a spectral gap
after the selected dimensions. The optimum then corresponds to leading eigenfunctions of the
positive-pair kernel and is unique up to rotation.

This is a sufficient-condition theorem in an idealized model. It is not a proof that
independently trained real systems discover one objective reality. Real modalities are lossy
rather than injective, finite data and optimization matter, and no experiment in the paper
exactly satisfies the theorem.

The theory uses an identity predictor. The paper explicitly says it does not cover the
learned, possibly action-conditioned predictor used when a JEPA functions as a dynamic world
model. It therefore does not prove planning, control, or physical-world understanding.

The paper proves uniqueness for whitened second-order anti-collapse objectives when a spectral
gap exists. Uniqueness for LeJEPA's full-distribution SIGReg constraint remains assumed rather
than proved.

## Alignment under mismatched views

When modalities do not use exactly the same positive pairs, the paper bounds alignment error
using the difference between their positive-pair kernels and the relevant spectral gap.
Similar positive graphs and well-separated spectral directions protect alignment; crowded
directions may not align.

A synthetic test generated 300 finite worlds with 8–39 states and embeddings of one to five
dimensions. Every observed error remained below the theoretical bound and reached at most 18%
of it. This validates the bound in the synthetic setup, not its assumptions for natural images
and language.

## Good views and bad views

The paper calls separate observations of the same underlying state *good views*. Examples
include two photographs of one scene or two independently worded descriptions of it. Their
nuisance variables, such as wording, style, viewpoint, or lighting, can differ while the
underlying state remains shared.

*Bad views* are corruptions of one observation, such as two crops of one photograph or two
masked versions of one caption. They retain observation-specific nuisance information and can
spend embedding capacity preserving it.

The terminology is relative to the task. Viewpoint may be a nuisance for image–text alignment
while remaining essential for an acting agent. The paper also classifies DINOv2 and most of
its own image encoders as bad-view JEPAs under this definition because their positives are
crops of the same image.

For stylized spectral models, the authors prove that good views can remove nuisance
information under separation assumptions. Bad views retain nuisance dimensions when those are
more strongly preserved than relevant world-state directions. Practical networks do not
exactly satisfy this model.

The choice of data matters too. Good views define the intended relationship directly. Weak bad
views may need dense data to connect observations of the same state, while overly strong
corruptions may join different states through shared nuisances.

## Next-token prediction is not directly covered by the main theorem

The paper algebraically rewrites a linear-softmax next-token loss as an attraction term
between a context representation and a target-token embedding plus a log-partition term that
acts somewhat like an anti-collapse or uniformity term. In this generalized sense, next-token
prediction has a two-encoder JEPA form.

Important differences remain. Context and token encoders occupy different spaces, and the
optimum is identified only up to a general invertible linear transformation rather than a
rotation. The main spectral theorem assumes one encoder and one kernel on one space.

The claim that next-token prediction behaves like a bad-view JEPA and wastes dimensions on
wording or style is therefore a heuristic supported by experiments, not a direct corollary of
the theorem. The paper provides evidence that it is inefficient for the tested cross-modal
alignment objective, not that language modeling is inefficient for every purpose.

## The controlled Flickr30k experiment

The paper first compares objectives with matched small encoders and data. It uses 29,000
Flickr30k training images, five captions per image, a ViT-S/16 image encoder, and a
33-million-parameter BERT-S text encoder.

For text, good views are different captions of one image, then trimmed and masked. Bad views
are multiple trimmed or masked spans of one caption. A next-token baseline uses the same BERT
architecture causally.

On 1,000 test pairs, mutual 10-nearest-neighbor overlap was:

- 0.062 for good-view JEPA;
- 0.047 for bad-view JEPA;
- 0.042 for next-token prediction;
- 0.043 when next-token training saw paired captions.

After fitting a rotation, image-to-text retrieval at rank one was 0.044 for good views, 0.027
for bad views, 0.021 for next-token prediction, and 0.023 for next-token training on caption
pairs. Chance was reported as 0.001.

Showing next-token training both captions barely helped. The gain came from using captions as
positive views, not merely exposing the model to both.

Trimming captions to shared content was the most important reported ablation. Whole-caption
views scored 0.185 R@1 in that setup and trimmed views scored 0.246. Training was not
automatically stable: without gradient clipping, 3 of 36 default-SIGReg runs collapsed, and
all tested alternative SIGReg weights without clipping collapsed.

## Good views on both sides

An MSR-VTT video experiment used 7,000 training clips, 20 captions per clip, and 1,000 test
clips. Mutual 10-nearest-neighbor overlap was:

- 0.067 with good image and good text views;
- 0.059 with bad image and good text views;
- 0.043 with good image and bad text views;
- 0.039 with bad views on both sides;
- 0.01 at chance.

The authors caution that their 7,000-clip image JEPA was much weaker than DINOv2. Scaling
genuinely good image views remains future work.

## The 109M-versus-72B headline

The large comparison trains a BERT-base-sized 109-million-parameter text encoder on 900
million samples associated with 940 million web images, totaling 116 billion text tokens. Each
image can have alt-text plus two machine-generated recaptions.

On WIT-1024, the paper compares neighborhood structure between text features and frozen DINOv2
ViT-B image features. The reported mutual 10-nearest-neighbor overlap was:

- 0.184 for the 109M good-view text JEPA;
- 0.154 for Qwen2.5-72B;
- 0.151 for Llama-3-70B;
- 0.111 for a matched next-token control;
- 0.088 for a matched bad-view JEPA.

The result also held in the reported direction under linear CKA, with a CLIP image model, on
COCO, and with several other image encoders. A fourth 109M JEPA seed using twice the effective
SIGReg weight scored only 0.121. Averaging all four seeds gives 0.168 rather than the
selected-weight three-seed mean of 0.184, still above the compared LLM values.

The metric asks whether local neighborhoods in the text and image spaces overlap. A score of
0.184 is not 18.4% world understanding. The comparison says nothing directly about language
generation, reasoning, mathematics, coding, factual knowledge, or general task ability.

The comparison is not fully controlled. The large LLMs have different architectures,
objectives, training data, and purposes. Hyperparameters were tuned for the good-view model
rather than equally for every baseline.

Most training recaptions were generated by LLaVA built on Llama-3-8B with a CLIP vision
encoder. The text encoder did not see pixels, but paired vision–language information entered
through image-based caption generation and grouping of texts by source image. At least 43 of
the 1,024 WIT captions were found in the DataComp alt-texts; removing them changed checked
scores by no more than 0.002.

The strongest justified statement is narrow: on tested representation-alignment metrics, this
109-million-parameter good-view text encoder outscored the two 70–72-billion-parameter LLMs.

## What 42 times fewer samples means

With the same 109M encoder family and text source, a good-view JEPA reached 0.109 WIT
alignment after 21.6 million training samples. The next-token baseline reached 0.111 after 900
million samples.

The ratios are:

- about 42 times fewer training samples;
- about 14 times fewer text tokens, because one good-view sample reads three texts;
- about 435 times fewer unique source images.

This is not a universal efficiency constant. The runs used different batch sizes and learning
rates, and the paper did not score an earlier checkpoint from the 900-million-sample
next-token run. Samples, tokens, compute, and the cost of producing and grouping
image-conditioned captions are different quantities.

The supported conclusion is that good views were much more sample-efficient for this alignment
target than the matched next-token baseline.

## Captioning required more than one rotation

The theorem motivates fitting an orthogonal map between aligned embedding spaces. The video
says a single rotation was enough to create an image captioner, which omits substantial
machinery.

The empirical system used frozen DINOv2 or DINOv3 image encoders, a good-view text encoder, a
causal caption decoder trained or fine-tuned on text, and an orthonormal linear map fitted
using 30,000 Flickr image–caption pairs. Its strongest setup used a Qwen2.5-1.5B decoder and
consensus over 32 sampled captions.

The strongest reported CIDEr score was 0.838 on COCO. No neural network was trained jointly on
image–caption pairs, but the map itself was fitted on paired data. When source and target
dimensions differ, the map has orthonormal rows rather than being a simple square rotation.

The paper also reports pair-free geometry matching and a weaker zero-pair captioner. That is a
separate experiment and should not be confused with the strongest 0.838 system.

## The result is not a world model

The paper evaluates alignment, retrieval, captioning, and zero-shot classification. These are
useful behavioral consequences of aligned representations. They do not establish human-like
causal, physical, or semantic understanding.

The paper's theorem excludes action-conditioned prediction. Calling the text encoder a small
world model or saying it replaces accumulated knowledge with understanding goes beyond the
evaluated result. The work may inform world-model research without itself solving world
modeling.

It also does not prove that language models cannot reach human-level intelligence. LeCun's
criticism of LLM-only approaches is a broader research position supported by arguments and
other work, not a conclusion of this theorem.

## LeCun's text-versus-vision calculation is rhetoric

LeCun compares 20–30 trillion text tokens at roughly three bytes each with four years of
visual input at about two megabytes per second over 16,000 waking hours. Both estimates fall
near 10^14 bytes.

The arithmetic is plausible: 20–30 trillion tokens correspond to roughly 60–90 terabytes,
while the visual estimate is about 115 terabytes. The inference is not established. Raw byte
throughput is not mutual information or usable learning signal; the encodings are not
comparable; vision is highly redundant; children receive action, touch, sound, proprioception,
and social feedback; and model training repeatedly transforms its data.

The calculation illustrates LeCun's view that embodiment carries rich information. It does not
prove that text cannot support human-level intelligence.

## Related JEPA results are separate papers

The video combines several publications into one fast-moving AMI narrative. The chronology is
broadly real, but not every paper lists AMI Labs.

LeJEPA, posted in November 2025, proposes SIGReg for self-supervised representation learning.
The auto-transcript incorrectly calls it LLaMA. It is not itself an action-conditioned world
model.

*When Does LeJEPA Learn a World Model?*, posted in May 2026, proves latent recovery under
restrictive Gaussian linear-dynamics assumptions. Its affiliations are Cold Spring Harbor
Laboratory, NYU, and Brown, not AMI Labs.

LeWorldModel, posted in March 2026, has about 15 million parameters and reports planning up to
48 times faster than DINO-WM in its setup. The number refers to latency, roughly one second
versus 47, not a 48-fold success improvement. It was competitive rather than uniformly
superior and does not list AMI Labs among its affiliations.

H-JEPA, posted in October 2026, uses hierarchical latent spaces at longer temporal strides. On
simulated Visual AntMaze, a flat planner achieved about 18% success and a three-level planner
achieved 73.3 ± 3.5%. The improvement was not universal: three-level H-JEPA performed poorly
on Push-T, and real-robot DROID evaluation measured offline planning fidelity rather than
autonomous deployment. H-JEPA does list AMI affiliations.

These papers support an active research program. They do not validate the PRH theorem's AGI
implications or turn every result into one AMI product roadmap.

## Other world-model evidence does not validate this theorem

The video's 3D World Simulator reference concerns a separate hybrid particle–voxel dynamics
system, not a JEPA result. It reports action-conditioned multimodal simulation at more than 50
frames per second on an RTX 5090 and sim-to-real policies described as comparable to policies
trained on real data. That does not prove universal transfer or the PRH theorem.

World Labs' Atlas can generate camera-controlled views, reconstruct 3D geometry, and support
real-to-sim workflows according to its official demonstrations. Those are company-reported
product results, not independent evidence of general physical understanding.

Brittleness is a real concern, but the video appears to combine multiple sources. JEPA-Bisim
reports that DINO-WM planning degrades under background changes and distractors. Older work
shows some JEPA objectives can focus on slow static features. A May revision of another study
compares several planning designs. No single identified paper exactly matches the video's
claim that one May study found all designs failed under changes of object color or background.

## AMI Labs claims and forecasts

Reputable reporting supports AMI Labs raising $1.03 billion in March 2026 at an approximately
$3.5-billion pre-money valuation. Reported investors include Bezos Expeditions, Nvidia,
Samsung, and Toyota Ventures. AMI's official site lists operations in Paris, New York,
Montreal, and Singapore.

The official site does not substantiate the video's estimate of 50–60 researchers. The broader
claim that this small team can leapfrog firms with far more capital is a forecast.

World models running on phones, glasses, or robots; radical reductions in training cost; wider
access for universities and smaller countries; and a route to AGI are conditional scenarios.
The paper does not evaluate deployment memory, total compute, energy, product cost, robotics,
persistent memory, reasoning, or planning.

The claimed data wall is also external to the paper. Images, video, and sensor streams are
abundant, but abundance does not make them diverse, labeled, permissioned, useful, or cheap to
train on.

## What would strengthen the evidence

The next tests should include:

1. independent replication of the alignment results;
2. equally tuned objective baselines under matched compute;
3. models trained without vision-conditioned recaptions;
4. larger good-view JEPAs and genuinely good image views;
5. evaluations of causal prediction, control, memory, and planning;
6. robustness to viewpoint, background, object, and domain changes;
7. end-to-end accounting of data creation, compute, memory, and latency;
8. deployment in robots and products with held-out real-world outcomes.

TheAIGRID itself names several sensible signals to watch: replication, scaling, real product
use, and adoption by major labs. Those would provide more evidence than social-media
enthusiasm or model-size comparisons on one alignment benchmark.

## Bottom line

Balestriero and LeCun proved that, under restrictive JEPA assumptions, modalities trained with
the same world-level positive structure learn equivalent representations up to rotation. They
also showed that good-view text training produces stronger image–text neighborhood alignment
than matched next-token training and, on that narrow target, can outperform far larger
language models with many fewer samples.

The result supports better view design as an important research direction. It does not
establish that a small JEPA understands the world, replace memorization with understanding,
invalidate LLM scaling, or provide a demonstrated path to AGI. The paper is stronger and more
interesting when its theorem, metric, assumptions, and limitations remain visible.

## Sources

- Balestriero and LeCun, *Proving and Improving the Platonic Representation Hypothesis with JEPAs*.
arXiv:2610.39302.
- Huh et al., *The Platonic Representation Hypothesis*. arXiv:2405.07987.
- Balestriero and LeCun, *LeJEPA*. arXiv:2511.08544.
- Klindt, LeCun, and Balestriero, *When Does LeJEPA Learn a World Model?* arXiv:2605.26379.
- Maes et al., *LeWorldModel*. arXiv:2603.19312.
- Zhang et al., *H-JEPA*. arXiv:2610.06805.
- Wang et al., *Hybrid Particle-Voxel Dynamics for Multimodal 3D World Simulation*.
arXiv:2611.04492.
- *JEPA-Bisim*. arXiv:2602.18639.
- World Labs, *Atlas* announcement.
- ACM A.M. Turing Award profile for Yann LeCun.
- AMI Labs official site and TechCrunch funding report.
