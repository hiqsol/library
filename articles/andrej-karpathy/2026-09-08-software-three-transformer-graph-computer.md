---
title: Software 3.0 and the Transformer as a Graph Computer
author: Andrej Karpathy
channel: Perfology Clips
url: https://youtu.be/Rlk0GLRWwTI?is=aN9QGYGnzZ-WG0oV
date: 2026-09-08 04:30
tags: ai, development
---

# Software 3.0 and the Transformer as a Graph Computer

[summary](../../summary/andrej-karpathy/2026-09-08-software-three-transformer-graph-computer.md)

## Source caveat

The Perfology Clips upload is dated September 8, 2026, but it appears edited and spliced.
Abrupt transitions near 22 and 24 minutes join material from at least two older Karpathy talks.
The publication date therefore does not date every underlying segment, and the video should not
be treated as one continuous new interview. Its English automatic captions also contain errors.
Names and terms can often be restored from context, but uncertain numbers and phrases remain
uncertain below.

## Three layers of software

Karpathy divides programming into three paradigms that accumulate rather than replace one another.

**Software 1.0** is explicit code: a person designs an algorithm and writes instructions, perhaps
in C++. Karpathy invokes Donald Knuth and *The Art of Computer Programming* for a paradigm that
has dominated for roughly 70 years. It produced systems as intricate as Linux, yet some desired
behaviors resist complete rule books: recognizing cats, playing strong chess, driving a car, or,
probably, constructing AGI one hand-written behavior at a time.

**Software 2.0** treats a neural network as a program whose source is a dataset. Training is the
compiler, and learned weights are the resulting binary. The programmer builds a data engine rather
than directly writing the weight-space program. Karpathy describes his roughly five years at Tesla
as a loop: train, deploy, inspect telemetry, collect failures, label them, add examples to tests or
training data, and repeat. ConvNets for vision, reinforcement learning for chess, and Whisper for
speech illustrate learned programs. The chess reward caption is inconsistent; the likely scheme is
+1 for a win, 0 for a draw, and -1 for a loss. Software 1.0 still supplies the training and
deployment infrastructure beneath Software 2.0.

**Software 3.0** moves the programmable artifact again, from dataset to prompt. A sufficiently
capable language model can be conditioned at runtime to perform a task described in natural
language. Karpathy summarizes the progression as designing the algorithm, designing the dataset,
and designing the prompt. Hence his claim that “the hottest new programming language is English.”
This is another layer, not the disappearance of ordinary code or trained weights.

## Prompting a simulator

An LLM is trained to predict the next token, then generates by feeding each prediction back as the
next input. Karpathy says that something striking emerges around a trillion parameters trained on
essentially the whole internet: the model does not merely continue prose but infers tasks from the
document it is asked to complete.

Few-shot prompting makes that shift visible. Put a passage, several question-and-answer examples,
and a new question in one context, and GPT can continue the pattern without a weight update. Prompt
wording also changes how much computation is expressed. In Karpathy's arithmetic example, a juggler
has 16 balls; half are golf balls, and half of those are blue. A hasty model says 8.
The answer is 4. Intermediate steps distribute work across more output tokens instead of forcing
the answer into one token's computation.

Karpathy reports that “Let's think step by step” raised one benchmark from 17% to 78.7%. He says
“Let's work this out in a step-by-step way to be sure we have the right answer” reached 82%. His
interpretation is that prompts select among behaviors represented in internet text: asking for steps
finds worked solutions, while asking for the right answer may bias toward worked solutions that end
correctly. Likewise, an “IQ 200” persona is his analogy for selecting a more capable style, not a
validated intelligence measurement.

This selection view leads to the idea of GPT as a simulator. In the blog demonstration “Building a
Virtual Machine inside ChatGPT,” prose tells the model to behave like a Linux terminal. It maintains
an imaginary directory, creates `jokes.txt`, and later prints its contents. It can even appear to
run Python. A simulated `ping bbc.com` returned plausible packets and about 24.9 ms while inventing
the IP address. The model completed a convincing terminal transcript; it did not contact the BBC.

Other examples turn prose into an operational specification. A GPT-3 smart-home prompt defines JSON
fields such as `action`, `location`, and `target`, plus a time, appliance inventory, and a home in
St. Albans, United Kingdom. It asks the system to switch off a son's light after 20 minutes.
The model infers the device and computes the later timestamp. “GPT Is All You Need for the Backend,”
the winning project at a Scale hackathon Karpathy judged, gave one LLM JSON state and a requested
route. “Delete the last two todos” produced updated JSON without conventional Python route logic.

Karpathy also discusses the alleged prompt for Microsoft's Bing persona Sydney, while explicitly
leaving its authenticity uncertain. The prompt purportedly specifies identity, introduction,
formatting, limits, and safety policy in prose. For him, that shows the power and fragility of
programming a personality with text. He cites Riley Goodside, then a staff prompt engineer at
Scale, as an early specialist who had personally helped him use such systems.

## Memory, tools, agents, and specialists

Native context is finite and conversation memory is short-lived. Karpathy favors keeping context
fixed while teaching a model to use an external scratchpad. Demonstrations could establish markers
such as `start scratchpad` and `end scratchpad`; decoding logic would store that text outside the
window and later expose it for retrieval or attention. His notebook analogy is direct: people do not
keep everything in biological memory either.

He argues that strongly meta-learned transformers may learn to use new tools dynamically, but this
is a proposal, not a demonstrated solution in the clip. He forecasts more general agents that use
external memory and tools, as well as specialized systems such as a doctor GPT. A mixture of experts
could route needs to different AI specialists, much as people consult different professionals.

## One interface for many modalities

A transformer's input need not be words. Each modality can be chopped into tokens, tagged with
learned type or modality embeddings, supplied with positional information, and placed in one set.
Self-attention then learns which pieces communicate. Karpathy contrasts this uniform interface with
the awkward choices involved in inserting radar, maps, vehicle type, or audio into a ConvNet.

A Vision Transformer divides an image into square patches; in his illustrative answer, an image
might occupy roughly the first 1,000 tokens. A mel spectrogram can be sliced for speech, as in the
“copy-paste transformer” characterization of Whisper. A Decision Transformer tokenizes states,
actions, and rewards. AlphaFold has a transformer at its computational core. Radar needs its own
representation, although Karpathy candidly says he does not know that native representation well
enough to prescribe the chunking.

Attention therefore relaxes the requirement that computation live on a fixed two- or
three-dimensional Euclidean grid. The inputs are fundamentally a set. Order and geometry can be
added through fixed sine-and-cosine positions, learned position vectors, modality embeddings, or
attention masks. Karpathy stresses a scale-dependent caveat: with little data, stronger priors such
as convolutional locality can help; with effectively infinite data, encoding less prior structure
may let the model learn better structure. Local and global attention layers can also be alternated
when full attention is too expensive.

## From fragmented pipelines to architectural convergence

Karpathy recalls entering AI in force around 2012, when “AI” sounded less serious than “machine
learning.” Circa 2011, vision systems combined pages of hand-engineered descriptors with an SVM.
NLP had a separate vocabulary around part-of-speech tagging, morphology, parsing, and coreference.
Researchers in one field could struggle to read work in another.

Alex Krizhevsky and colleagues changed the emphasis with AlexNet in 2012: large neural networks,
large datasets, and large compute delivered strong results. A shared toolkit of parameters,
optimizers, and scaled training spread through vision, language, speech, translation, and RL.
Sequence-to-sequence work became legible across specialties. The 2017 paper *Attention Is All You
Need* drove a second convergence: many fields increasingly reused the same architecture, changing
mainly the tokenization and data.

Karpathy speculates that this convergence could point toward a generic learning mechanism, loosely
analogous to a relatively homogeneous cortical sheet whose regions differ less than their functions
suggest. He presents that as an intriguing analogy, not established neuroscience.

## How attention emerged

An early neural language model, likely Bengio and colleagues' 2003 work, used three words in an MLP
to predict a fourth. The influential 2014 sequence-to-sequence architecture used an encoder LSTM to
compress an English sentence into one vector and a decoder LSTM to generate a translation. That
fixed vector became an obvious information bottleneck.

Bahdanau and colleagues replaced the bottleneck with a soft search over encoder states. At each
decoding step, compatibility scores identify relevant source positions; a softmax converts scores
into weights, and a weighted sum forms the context vector. Karpathy identifies this as the first use
of “attention” for this mechanism that he knows.

Karpathy says Dzmitry Bahdanau told him the intuition grew from middle-school translation exercises:
a student's gaze moves between source and target text. Cursor-based attempts failed, but a learned
soft cursor implemented with softmax and a weighted average reportedly worked on the first try.
Its working name was “RNNsearch.”
Karpathy says Yoshua Bengio proposed “attention” in the final edit.
This is Karpathy's relayed origin story, not independent evidence supplied by the upload.

The 2017 Transformer removed recurrence and combined attention with positional encodings, residual
connections, MLP blocks, layer normalization, parallel heads, and a durable 4x MLP expansion.
Karpathy calls this an unusually good local minimum: later changes often failed to stick. Important
survivors include pre-norm placement and rotary or relative positional encodings, while the basic
architecture remains close to the original.

## Attention as directed-graph message passing

Karpathy's graph interpretation separates every transformer block into two alternating operations:

1. **Communication:** multi-head attention moves information among token nodes.
2. **Computation:** an MLP transforms each node independently.

Each node contains a vector. Learned linear maps produce its query, key, and value:

- The **query** describes what the destination node seeks.
- The **key** advertises what a possible source contains.
- The **value** is the content that source will send if selected.

For one destination, the graph first determines which source nodes have permitted directed edges
into it. The destination query is dotted with their keys. Softmax turns those compatibility scores
into nonnegative weights summing to 1. Their values are averaged with those weights, and the result
updates the destination. Topology determines who may speak; Q/K compatibility determines how loudly
each permitted source speaks for the current data.

One head is one instance of this operation. Heads are independent copies in parallel, with different
Q/K/V projections, so a node can seek several kinds of information at once. Layers are copies in
series, each with new parameters. Karpathy's memorable distinction is: heads in parallel, layers in
series.

Connectivity creates the familiar transformer families. In an encoder, every token can attend to
every other token. In a decoder, a triangular causal mask permits attention only to the current and
previous positions; future positions would leak the training answer. In cross-attention, decoder
nodes provide queries while keys and values come from final encoder states. Thus self-attention and
cross-attention use the same mathematics and differ in where keys and values originate.

These patterns yield GPT as decoder-only, BERT as encoder-only, and T5 as encoder-decoder. BERT uses
bidirectional communication with masking and other denoising objectives, supporting tasks such as
sentiment classification. T5 adds cross-attention for mappings such as translation. A decoder-only
GPT has causal self-attention and no encoder.

## In-context learning inside the graph

Karpathy reads the GPT-3 paper, *Language Models are Few-Shot Learners*, as evidence for in-context
learning or meta-learning. Adding demonstrations can improve task performance even though no model
weights change. The outer loop uses stochastic gradient descent to learn weights; the inner loop
changes behavior through activations while the model processes a context.

He speculates that those activation dynamics might implement something resembling a learned or even
gradient-like algorithm. He cites theoretical work constructing ridge regression from a transformer
operator, but the operator's name is garbled in the captions and should not be stated as certain.
His analogy between repeated additive gradient updates and residual-network updates is explicitly
“much more hand-wavy.” In-context learning is empirical; this proposed mechanism is not settled.

## Why the Transformer scales on GPUs

Karpathy groups the architecture's advantage into expressivity, optimizability, and efficiency. It
can represent sophisticated functions; residual paths, normalization, and related choices make deep
networks trainable; and its shallow, wide computation graph maps well to GPU parallelism. He invokes
Neural GPU as another attempt to design a model backward from hardware capabilities.

An RNN may implement arbitrary programs in principle, but Karpathy calls that point impractical.
An unfolded RNN is a long, thin, serial graph. A Transformer is shallow and wide: token
positions can be processed in parallel, gradient paths are shorter, residual streams aid flow, and
layer normalization controls scales. He qualifies the gradient-path explanation with “I don't
exactly know why”; it is intuition rather than a full theory. Hardware fit matters because more
throughput permits larger training runs, and scale itself drives deep-learning performance.

In hindsight, Karpathy says he might rename the 2017 paper “A General-Purpose, Efficient,
Optimizable Computer.” The achievement is not attention alone but the conjunction of representation,
trainability, and hardware efficiency.

## nanoGPT: the graph in code

Karpathy presents nanoGPT as a readable, complete implementation of roughly 300 lines. He says it
can reproduce GPT-2 on OpenWebText with enough compute and reports about 38 hours on one GPU node;
the automatic captions do not establish the accelerator type or count. His toy corpus is tiny
Shakespeare, roughly 1 MB, used to generate effectively unlimited Shakespeare-like text.

Text first becomes integers. A character-level tokenizer maps each character to an ID; practical
models often use subword methods such as BPE, SentencePiece, or WordPiece. Separate documents can be
joined with an end-of-text token. The captioned claim about that boundary is incomplete, so no
stronger conclusion is warranted.

Training samples blocks from one long token sequence. With block size 8 and batch size 4, the input
has shape 4 x 8, but it supplies roughly B x T next-token examples: `[47]` predicts `58`,
`[47, 58]` predicts `1`, and `[47, 58, 1]` predicts `51`. Rows are independent graphs, so no
information crosses the batch dimension. Making the batch large enough helps saturate the GPU.

The forward pass adds token embeddings to positional embeddings, applies optional dropout, passes
the vectors through transformer blocks, applies final layer normalization, and uses `lm_head` to
produce next-token logits. Targets are shifted by one position, and cross-entropy is the standard
negative log-likelihood classification loss.

Inside a pre-norm block, normalized vectors enter causal multi-head attention, return through a
residual connection, then enter a two-layer per-token MLP with GELU and another residual path. For a
block of eight tokens, node 1 reads itself, node 2 reads nodes 1 and 2, and so on through node 8.

The difficult-looking attention code mostly manages batch, head, time, and channel dimensions.
Linear projections make Q, K, and V. Matrix multiplication computes all Q-K dot products. A masked
fill assigns forbidden future scores negative infinity, so softmax makes their weights zero. The
remaining weights multiply V to form weighted value sums; reshaping and projection return the result
to the residual stream. Removing the mask produces encoder attention. Adding a sublayer whose query
comes from the decoder and whose keys and values come from the encoder produces cross-attention.

Generation begins from a token, perhaps a newline in the character model. The model samples a next
token, appends it, and reruns the growing sequence. With toy block size 8, it must crop old tokens
after the window fills. The captions appear to drop digits from two typical context-length numbers,
so the likely 1,024 and 2,048 values should not be treated as established by this upload.

## A runtime-programmable graph computer

The graph view unifies the technical and programming claims. Tokenization defines nodes; masks and
cross-attention define directed edges; Q/K/V make communication conditional on current data; MLPs
compute locally; and repeated layers compose a general computation. Training with SGD writes one
kind of program into weights. A prompt then configures another program in activations at runtime.

Earlier networks often resembled special-purpose computers. Karpathy argues that a large Transformer
trained on a sufficiently broad and difficult corpus becomes a general-purpose computer over text.
The prompt is the program, and GPT “runs” it by completing the document. Terminal, smart-home,
backend, Q&A, and persona examples show the flexibility of this interface; the fake BBC ping shows
its central limit. Runtime programmability produces simulations and useful structured outputs, not
a guarantee of factual execution, persistent state, tool access, or truth.