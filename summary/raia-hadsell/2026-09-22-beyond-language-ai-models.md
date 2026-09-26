---
title: Beyond Language: Embeddings, Weather Models, and Interactive World Models
author: Raia Hadsell
channel: AI из первых уст
url: https://youtu.be/eK7mAQiprYo?is=L5izN0fLPX9Ri3ac
date: 2026-09-22 14:00
tags: ai
---

# Beyond Language: Embeddings, Weather Models, and Interactive World Models

## Source and framing

This is based on a Russian translated repost uploaded by **AI из первых уст** on
September 22, 2026, not a new Hadsell presentation. The English source was uploaded on
April 18, 2026. Russian automatic captions may distort names, figures, and nuance.
Claims below are therefore attributed to Raia Hadsell or Google DeepMind.

Hadsell frames frontier AI as finding deep "root" problems with many downstream uses.
Her examples retrieve, forecast, and simulate rather than primarily generate text.
The strongest thesis is that major AI progress extends beyond language models.
The talk does not demonstrate unified general intelligence or AGI.

## Multimodal embedding and recognition

The Jennifer Aniston neuron is an analogy for a small neural set that responds to one
person across a name, photograph, video, or voice, enabling rapid recognition.
Embedding models seek similar invariance by mapping different media into a semantic space.
Contrastive losses and Siamese networks train related items closer than unrelated ones.
**Gemini Embedding 2** encodes text, images, video, audio, and PDFs in one vector space.
Hadsell cites 8,000 tokens, 128 seconds of video, 80 seconds of audio, or a whole PDF.
**Matryoshka Representation Learning** can search at 256 dimensions, then use more.
Uses include cross-modal retrieval, query matching, recommendation, and agentic logic.
It shows useful recognition, not biological equivalence, consciousness, or AGI.
## Neural weather forecasting

**GraphCast** learns from roughly 40 years of global data with a spherical graph network.
It autoregressively predicts about 100 variables from the surface to lower stratosphere.
Hadsell says it forecast **Hurricane Lee** landfall nine days ahead versus six for the
best physics-based models, potentially adding three valuable days of preparation.
The talk's late-2024 reference conflicts with Lee's documented September 2023 landfall.
**GenCast** is probabilistic: it samples futures and exposes tails in chaotic weather.
Hadsell reports wins on 97% of about 1,300 comparisons and a 15-day member in eight
minutes on one chip; those figures do not mean 97% of forecasts were simply correct.
**FGN**, or **Functional Generative Network**, directly predicts cyclone properties.
Hadsell says the US National Hurricane Center uses it, without defining operational status.
These results support specialized forecasting, not universal superiority or AGI.
## Interactive world models

**Genie 1** made brief, controllable 2D platformers; **Genie 2** added slow 3D worlds.
**Genie 3** demos show walking, skiing, embodied views, and responsive water movement.
A short artist-made clip becomes a flyable world whose structures remain on return.
An origami-lizard test preserves a starting area after about a minute away.
Users can also alter a running world with new prompts, not only set its initial scene.
Hadsell proposes games and immersive education, but these are predictive applications.
The demos show bounded memory, control, and visual coherence, not faithful physics,
long-term persistence, causal understanding, autonomous planning, or general intelligence.
