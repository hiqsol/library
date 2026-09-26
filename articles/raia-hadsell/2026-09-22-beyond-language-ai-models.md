---
title: Beyond Language: Embeddings, Weather Models, and Interactive World Models
author: Raia Hadsell
channel: AI из первых уст
url: https://youtu.be/eK7mAQiprYo?is=L5izN0fLPX9Ri3ac
date: 2026-09-22 14:00
tags: ai
---

# Beyond Language: Embeddings, Weather Models, and Interactive World Models

## Source note

This article covers a Russian translated repost from **AI из первых уст**, uploaded on
September 22, 2026. The underlying English talk was uploaded on April 18, 2026 as
"How Google DeepMind is researching the next Frontier of AI for Gemini." The speaker is
Raia Hadsell, Google DeepMind's VP of Research and a UK AI Ambassador. The later date is
therefore the wrapper's date, not the date of Hadsell's original presentation.

The Russian automatic captions include translation errors and mangled technical names.
Figures and wording below are attributed to Hadsell unless another basis is stated. Even
where names can be corrected from the English source, exact limits and claims should be
read as a conference presentation, not as an independently reproduced evaluation.

## The frontier is broader than language

Hadsell frames frontier AI as a search for "root nodes": deep, unsolved problems whose
solution could enable many downstream uses. Her group asks which architectures should
come next for Gemini, which problems AI may be unusually able to solve, and how advances
may change artificial, human, and robotic intelligence. She says DeepMind seeks such
problems with partners, then carries the resulting capabilities toward useful applications.

That agenda is explicitly wider than large language models. Hadsell selects three kinds of
system that retrieve, forecast, and simulate rather than primarily produce language:
multimodal embeddings, neural weather models, and interactive world models. Together,
they support the talk's strongest thesis: important AI progress can come from learned
representations and dynamics outside next-token text generation.

The examples do not, by themselves, establish artificial general intelligence. They show
specialized systems with useful forms of recognition, prediction, control, and memory.
Hadsell's broader language about the "future of intelligence" is a research vision, not a
measurement showing that these systems possess general reasoning or human-like minds.

## One concept across many modalities

### The Jennifer Aniston neuron analogy

Hadsell begins with the neuroscience idea commonly called the "Jennifer Aniston cell."
Her careful version is not a claim that one neuron stores one celebrity. Rather, a small
set of neurons can respond selectively to a familiar person, object, or place. Hearing the
name, seeing a photograph or video, or recognizing the voice may activate a related set.
The attraction is a representation robust to the sensory form in which a concept appears.

An embedding model aims at an analogous computational property. It maps an input to a
vector whose location captures useful semantic relations. Similar concepts should be near
enough for rapid recognition, matching, and retrieval even when one item is text and the
other is an image, audio clip, video, or document. The analogy motivates invariance across
modalities; it does not show that a model represents concepts exactly as a brain does.

### Contrastive learning and a unified space

Hadsell points to contrastive loss functions and her earlier work on Siamese neural
networks. In broad terms, contrastive training pulls representations of related examples
together and pushes unrelated examples apart. A Siamese setup applies shared machinery
to paired inputs so their similarity can be learned. The useful product is a geometry for
comparison, not necessarily a generated answer.

That distinction makes embeddings a companion to generative models. A system sometimes
needs to generate; at other times it should find an existing item. Search, retrieval,
query matching, recommendation, and agentic logic can use embedding similarity to locate
relevant material before a generative component reasons over or presents it.

### Gemini Embedding 2

Hadsell presents **Gemini Embedding 2** as a fully multimodal model derived from Gemini.
It places text, images, video, audio, and PDFs in one semantic space. Her claimed advantage
is end-to-end encoding: separate modality pipelines need not be joined after the fact, a
process that can lose information or introduce alignment errors.

In the talk, she says one vector can represent up to:

- 8,000 text tokens;
- 128 seconds of video;
- 80 seconds of audio; or
- an entire PDF.

Those are spoken limits, not benchmark results. Published launch material reportedly uses
8,192 text tokens, 120 seconds of video, and PDFs of up to six pages, while not confirming
the spoken 80-second audio limit. The mismatch is important when implementing the model
and is also a reason not to treat translated automatic captions as API documentation.

The model uses **Matryoshka Representation Learning**, or **MRL**. It learns nested vector
representations at several dimensionalities within one network. Hadsell's example begins
retrieval with 256 dimensions, then uses more dimensions for a richer comparison. This can
support a cheap first-stage search followed by a more precise reranking stage. It does not
mean discarded coordinates can later be recovered unless the fuller vectors were retained.

Hadsell calls the quality state of the art, but the talk supplies no numerical embedding
benchmark. The demonstrations and architecture support a narrower conclusion: one model
can encode mixed modalities into a shared, size-flexible representation useful for search.
They do not establish consciousness, grounded human understanding, or AGI. Nor does the
Jennifer Aniston analogy prove biological equivalence; it is an intuition about invariant
recognition.

## Forecasting a physical system from data

### From the UK Met Office question to GraphCast

The weather program began, in Hadsell's account, when a computer scientist at the **UK Met
Office** asked whether AI could forecast rainfall better than physics-based models. The
DeepMind team had roughly 40 years of global weather observations on which to train. The
resulting work treats atmospheric evolution as a learnable prediction problem while the
underlying atmosphere remains a complex physical and chaotic system.

**GraphCast** uses a spherical graph neural network. Hadsell describes graph nodes spanning
the globe from Earth's surface into the lower stratosphere. Given an atmospheric state,
the network autoregressively predicts later states: each predicted step helps form the
input to the next. She says it forecasts about 100 atmospheric variables, including wind
speed, temperature, and humidity, at locations around Earth.

The talk describes a forecast horizon of up to 15 days. The original public GraphCast
release documented a 10-day horizon, so the spoken figure may refer to the broader weather
program or may be imprecise. Either way, this is a global changing field, not a language
model answering a weather question in prose.

### Hurricane Lee and three extra days

The central example is **Hurricane Lee**. The animation follows the storm across the
Atlantic as it pauses, turns north, accelerates, and makes landfall in Nova Scotia.
Hadsell says GraphCast predicted the landfall location accurately nine days in advance,
whereas the best physics-based reference models reached that accuracy six days ahead.
For emergency planning around a major hurricane, she argues, three extra days matter.

The translated talk introduces this as something seen in late 2024. Hurricane Lee's
documented landfall was in September 2023, so the date in the talk or captions is not
reliable. The case is still evidence of useful long-range track guidance, but one striking
storm does not measure average performance, calibration, intensity accuracy, or behavior
across all weather regimes. It also does not show that physical modeling is obsolete.

### GenCast: probabilities for chaotic weather

Hadsell next presents **GenCast**, a mesh-based probabilistic successor. A deterministic
forecast gives one trajectory. A probabilistic model samples plausible futures, making it
possible to estimate a distribution and inspect its tails. This matters because weather is
chaotic and low-probability outcomes can carry the greatest human cost.

She says GenCast was more accurate in 97% of comparisons against about 1,300 benchmark
forecasts. The published evaluation is more specific: it reports better performance than
ECMWF ENS on 97.2% of 1,320 variable-and-lead-time targets, using 2019 test data after
training through 2018. That is not the claim that 97% of individual forecasts were simply
"correct."

Hadsell also says a 15-day forecast took eight minutes on one chip, compared with hours on
a large supercomputer. The documented comparison refers to one ensemble member on one
Cloud TPU v5, not necessarily the cost of the complete probabilistic ensemble. The result
still matters: cheaper members can make a larger set of possible futures more practical.

### FGN and direct cyclone prediction

The latest weather model named in the talk is **FGN**, expanded there as **Functional
Generative Network**. Hadsell contrasts two pipelines. One first forecasts weather, then
runs a cyclone detector as post-processing. FGN instead trains the network directly on
cyclone recognition and categorization, track, wind speed, and eye formation. Making the
operational target part of training can improve the variables users care about.

Hadsell says the **US National Hurricane Center** is already using the technology and is
enthusiastic about its advantage. She does not say whether that use is experimental,
advisory, or routine operations. Her hope that it will be used worldwide in coming years
is a forecast and promotional aspiration, not a demonstrated deployment fact.

Taken together, the weather examples strongly support the value of learned forecasting as
a fast, specialized complement and sometimes a benchmark winner over numerical baselines.
They do not prove causal understanding of atmospheric physics, universal superiority,
zero need for observational systems or experts, or AGI. Operational decisions also require
calibration, robustness under rare shifts, ensembles, and institutional validation.

## Interactive world models

### From agent training to environment generation

DeepMind's world-model line grows from work on **Atari**, **Go**, **StarCraft**, and
**MuJoCo**-style robotics environments. Those projects studied agents acting in a world.
Hadsell says the research question expanded: rather than only train an agent in a fixed
setting, could a model generate an effectively unbounded supply of interactive settings?

That shifts the output from a static image or video to an environment that reacts to user
actions. A credible world model needs more than visual variety. It needs responsiveness,
spatial consistency, some persistence, controllability, and enough temporal coherence for
a participant to act and observe consequences.

### Genie 1, Genie 2, and the move to 3D

**Genie 1** generated varied two-dimensional platform worlds from a request. A player could
move left or right and jump, but a world lasted only seconds. Hadsell treats this as a proof
of direction: scale the data, improve the method, and train again.

**Genie 2** moved to interactive 3D game environments. It was not yet real time, forcing
the user to move slowly, and it lacked the realism and higher definition of later demos.
The progression separates distinct capabilities: diversity, control, dimensionality,
speed, visual quality, and persistence do not arrive automatically as one package.

The English talk briefly says "then along came **Veo 3**" before the later demonstrations,
which are labeled **Genie 3**. It gives no technical account of how Veo 3 and Genie 3 are
related. The Russian captions blur several model names, so no integration claim should be
inferred from that transition alone.

### What the Genie 3 demonstrations show

In one prompt, the user walks down a muddy lane in Kent. Looking down reveals a body;
walking disturbs water. Hadsell interprets this as modeling not just the lane's appearance
but aspects of engaging with it. Another scene supports skiing, with a first-person body
and movement through a mountain environment.

A second route starts from a short video fragment made by an artist. **Genie 3** extends
that handcrafted opening into a world through which the user can fly. The user can bounce
off a strange structure, leave it, return, and find it in the expected place. This shows
bounded spatial memory and interactive continuation rather than mere playback.

The "origami lizard in an origami world" prompt provides a clearer consistency test. A
user runs away for about a minute, returns to the starting point, and finds the scene as it
was. Public framing describes consistency over a few minutes. That is meaningful memory
for generation, but it is not indefinite storage or proof of a complete internal map.

The final demonstration begins near the DeepMind office along London's Camden Canal.
Hadsell issues new prompts while already inside the generated experience, and the world
changes immediately more than once. Initial prompting therefore does not fix the whole
session: a user can alter the environment while it is running.

### Applications and limits

Hadsell imagines a new form of gaming in which one person can even prompt changes into
another person's experience. She also proposes education: learners might enter a generated
world to explore a subject rather than only read about it. These are plausible applications
suggested by the demos, not evidence of learning gains, commercial readiness, or safe
multi-user operation.

The demos support interactive visual synthesis, short-horizon consistency, prompt control,
and multiple kinds of movement. They do not establish faithful physics, reliable causal
reasoning, long-term memory, autonomous planning, factual simulation, or transfer to the
open physical world. A scene that looks coherent can still behave incorrectly. Calling it
a "world model" describes the system's function and ambition; it does not prove a complete
or human-like model of reality.

## What the three areas establish

The best-supported common claim is practical and architectural. Embeddings make concepts
retrievable across media; neural forecasters learn useful dynamics from decades of global
data; world models turn prompts and clips into environments that respond over time. Each
moves AI beyond text while solving a different computational problem.

A stronger claim remains unproven. Cross-modal similarity is not general understanding;
weather accuracy on named targets is not broad intelligence; and an explorable generated
scene is not evidence of grounded cognition. These systems may become components of more
general agents, but the talk does not test an integrated agent across the three domains.

Hadsell's language about root problems, a new frontier, worldwide adoption, new forms of
entertainment, and immersive education is forward-looking. The concrete demonstrations
make that vision credible enough to investigate. They do not turn forecasts about AGI or
social impact into established results. The durable lesson is narrower: frontier AI is
already plural, and progress should be judged against the task, baseline, and limitations
of each system rather than against the visibility of language models alone.
