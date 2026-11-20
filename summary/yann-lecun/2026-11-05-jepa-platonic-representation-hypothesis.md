---
title: Good-View JEPAs Align Modalities Efficiently but Do Not Prove AGI
author: Yann LeCun
channel: TheAIGRID
url: https://youtu.be/_fEqQa5hBmI?si=fE4mSq_IcDewcn8x
date: 2026-11-05 09:45
tags: ai, technology
---

# Good-View JEPAs Align Modalities Efficiently but Do Not Prove AGI

[article](../../articles/yann-lecun/2026-11-05-jepa-platonic-representation-hypothesis.md)

Balestriero and LeCun prove a conditional Platonic Representation Theorem. If modalities injectively
render the same finite world, use identical world-level positive pairs, reach population optima, and
have unique rotation-invariant solutions, their representations are equivalent up to rotation.

The assumptions are restrictive. Real modalities are lossy, finite training matters, and the theory
uses an identity predictor, not an action-conditioned world-model predictor. It does not prove
that real models discover objective reality, learn dynamics, plan, or understand the world.

Good views are independent observations of one state, such as two captions of one scene. Bad views
are corruptions of one observation. Good views suppress nuisance features in a stylized spectral
model. Next-token loss has a generalized two-encoder JEPA form, but calling it a bad-view JEPA is an
experimentally motivated heuristic rather than a theorem.

On WIT-1024, a 109M good-view text JEPA scored 0.184 mutual 10-nearest-neighbor overlap with DINOv2
image features. Qwen2.5-72B scored 0.154 and Llama-3-70B scored 0.151. This measures representation
alignment, not language ability, reasoning, coding, factual knowledge, or 18.4% understanding.

A fourth JEPA seed scored 0.121; all four average 0.168. Texts were grouped by source image, and two
captions per image came from a vision-language recaptioner. Hyperparameters were tuned for the
good-view model rather than equally for all baselines.

The 42× claim compares 21.6M good-view samples reaching 0.109 alignment with 900M next-token samples
reaching 0.111. It also means about 14× fewer text tokens and 435× fewer unique images. Different
optimization recipes were used, so this is not a universal compute- or data-efficiency law.

Image captioning required frozen vision and text encoders, a text-trained causal decoder, and an
orthonormal map fitted on 30,000 Flickr pairs. The strongest system used a Qwen2.5-1.5B decoder and
32-sample consensus. It was not created by a rotation alone.

LeWorldModel separately reported up to 48× lower planning latency, not 48× higher success. H-JEPA
raised Visual AntMaze success from about 18% to 73.3%, but gains varied. These results and
AMI Labs' verified $1.03B funding do not establish this paper's AGI implications.

LeCun's comparison of text bytes with four years of visual throughput is plausible arithmetic but
scientifically incommensurate. Raw bytes are not usable information, and children also learn through
action, touch, sound, proprioception, and social feedback.

The strongest conclusion is narrow: under idealized assumptions, matching positive structures yield
representations equivalent up to rotation. Good-view training was much more sample-efficient than a
matched next-token baseline for cross-modal alignment. It did not prove the AI industry wrong,
replace accumulated knowledge with demonstrated understanding, or establish a path to AGI.
