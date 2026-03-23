---
title: "Terence Tao: How the World's Top Mathematician Uses AI"
author: Terence Tao
channel: Dwarkesh Patel
url: https://www.youtube.com/watch?v=Q8Fkpi18QXU
date: 2026-03-20 00:00
tags: ai, development
---

# Terence Tao: How the World's Top Mathematician Uses AI

*Interview by Dwarkesh Patel. Terence Tao is a Fields Medal winner and professor at UCLA,
widely considered the world's greatest living mathematician.*

## Kepler as a Model for AI-Driven Science

Tao opens with the story of Kepler's discovery of planetary motion. Kepler inherited Tycho
Brahe's massive observational dataset — the most accurate naked-eye astronomical data ever
collected — and spent years cycling through hypotheses. His first beautiful theory (planetary
orbits inscribed in Platonic solids) failed. He eventually worked out elliptical orbits and the
laws of planetary motion.

The analogy to AI: LLMs could do what Kepler did — cycle through large spaces of hypotheses
against a verifiable data bank. As long as there's a ground truth to check against (like Brahe's
data), AI can try random relationships and discard failures. This kind of broad empirical
exploration can drive real scientific progress.

## The Copernican Revolution in Intelligence

We're going through a cognitive Copernican revolution: we used to think human intelligence was
the center of the universe. Now we're discovering there are very different types of intelligence
with different strengths and weaknesses. Our assessment of which tasks require intelligence must
be completely reordered.

Newton's theory initially had gaps; Darwin's theory was missing heredity. Progress often requires
deleting assumptions you didn't know you were making — like Aristotle's idea that objects
"naturally want to rest," which made the moving Earth seem absurd. The hardest conceptual leaps
are about abandoning comfortable priors.

## Breadth vs. Depth: AI and Human Complementarity

AI excels at breadth; human experts excel at depth. Our current scientific culture is optimized
for depth because that's all humans could do. With AI, we now have a tool for breadth — and
science needs to be redesigned to exploit it.

Tao's proposed new paradigm:
- More effort on broad classes of problems rather than one or two deep important problems
- Use AI to "map out" entire new fields — make easy observations, identify islands of difficulty
- Human experts then focus on those islands
- Eventually: AI achieves both breadth and depth simultaneously

*"Science will be unrecognizable after that."*

## Erdős Problems: 50 Down, ~600 to Go

A website tracks ~1,100 open Erdős problems. With AI assistance, about 50 have been solved — a
remarkable burst. But the pace has since plateaued. Three separate attempts to point frontier
models at the entire problem set produced only minor observations, no new pure-AI solutions.

The mountain range analogy: imagine climbing in the dark. You don't know which cliffs are 3 feet
high and which are 300. AI is a jumping machine that can leap 2 meters — higher than any human.
Set loose in the range, it quickly found all the low walls. But it can't create partial progress
or identify intermediate stages the way humans can. It either solves the problem or it doesn't.

**The bullish/bearish split:**
- *Bearish*: AI only reaches a certain height ceiling
- *Bullish*: when AI reaches Terence Tao's level, it can apply that level of intelligence to a
  million problems simultaneously — something impossible with humans. Even at human-average level,
  AI breadth is qualitatively more powerful than human breadth.

## Lean and Formal Proof Verification

Lean (a formal proof assistant) has become a key tool. A Lean proof verifies every logical step
mechanically, making it possible to:
- Identify which lemmas in a proof are novel versus boilerplate
- Ablate parts of a proof to find the minimal core
- Delegate post-processing and summarization to other AIs
- Have multiple independent AI tools — one to generate a proof strategy, one to critique it, one
  to do the literature survey

The Erdős problem website has seen proofs where AI generates 3,000 lines of Lean code, then other
AIs summarize and humans write their own cleaner versions. Having one proof unlocks a whole
post-processing pipeline.

On incomprehensible AI proofs (e.g., a 10-million-line Lean proof of the Riemann Hypothesis):
Tao is not worried. Once you have the artifact, you can analyze it — ablate steps, have other AIs
find elegant sub-proofs, gradually build understanding.

## The Missing Piece: Semiformal Languages for Strategies

What Lean does for *proofs*, we don't yet have for *strategies*. Proof strategies — the
meta-reasoning about which approach to try, why a conjecture seems plausible, why a method is
likely to work — remain informal and human-dependent.

The bottleneck: we can't benchmark AI on strategy generation because we have no formal way to
assess whether a strategy is good, except by waiting years to see if it pans out.

Tao's wish: a semiformal language for mathematical reasoning that could be validated
semi-automatically, similar to how Lean validates proofs. Without it, AI can't be trained via
reinforcement learning on strategy quality.

## How Tao Learns New Fields

Tao identifies as a "fox" (knows a little about everything) who collaborates with "hedgehogs"
(deep experts in one area). His learning process: obsessively pursue things he feels he *should*
understand but doesn't. Once he can explain a result to himself in terms he knows, he stops.

AI has made this significantly faster. He uses AI for:
- Literature searches and surveys
- Proof checking and verification
- Code for numerical experiments
- Generating and critiquing proof strategies

## Gauss, the Prime Number Theorem, and Data-Driven Conjectures

Gauss computed the first ~100,000 primes looking for patterns. He found a statistical one: the
density of primes up to x is approximately 1 / ln(x). This was the first major data-driven
conjecture in mathematics — no proof, just empirical observation — and it launched analytic
number theory.

The twin prime conjecture (infinitely many pairs of primes 2 apart, like 11 and 13) remains
unproved. But mathematicians are *certain* it's true, because the probabilistic/random model of
the primes predicts it unambiguously. Failure of the Riemann Hypothesis would shatter this model
and immediately cast doubt on all prime-based cryptography.

## Exposition as a Human Moat

Darwin wrote in plain English with no equations, weaving narrative and data. Newton wrote in
Latin and withheld key results from rivals. Darwin's work spread in years; Newton's took decades
to become accessible.

The art of building a case — combining data with narrative, making gaps seem like future
discoveries rather than fatal weaknesses — is a soft skill that's hard to automate. Tao doubts
RL can optimize for persuasiveness in any rigorous way. This may remain a permanently human
dimension of science.

## Vibe Coding vs. Vibe Researching

In software, the *output* (working code) is the point. If an AI produces working code that
also teaches you a new abstraction, that's a bonus. In research, the understanding gained *in
the process* is much of the value. Solving the Millennium Prize Problems matters primarily because
the techniques developed along the way reshape mathematics — not just because the statement is
confirmed. A pure AI solution of the Riemann Hypothesis, even in Lean, might produce a result
without producing insight.

Tao is optimistic that Lean proofs can be mined for insight post hoc, but acknowledges this is
an open and nascent area.
