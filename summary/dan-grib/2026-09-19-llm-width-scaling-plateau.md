---
title: Why Wider Language Models Hit a Scaling Plateau
author: Dan Grib
channel: Dan Grib
url: https://youtu.be/6xQ8LQfkBg4
date: 2026-09-19 14:15
tags: ai, development
---

# Why Wider Language Models Hit a Scaling Plateau

## Bottom line

The supplied source does not show more test-time compute making an LLM worse.
Dan Grib instead explains width scaling, superposition, and interference.
The reported outcome is diminishing returns and eventual saturation, not reversal.

## Paper and attribution
Grib names “Superposition Yields Robust Neural Scaling,” labeled MIT, NeurIPS 2025.
Thus the description identifies MIT, but it gives no individual author names.
Paper findings here mean findings only as Grib presents them.
His broader claims about the field and future systems are commentary.

## Setup and mechanism

Grib traces GPT-1, GPT-2 one year later, and GPT-3 another year later.
He says the industry has pursued bigger models for the last 6 years.
Self-supervised learning uses Wikipedia, hundreds of thousands of books, and the web.
A working model handles over 50,000 words and concepts, by his estimate.
Its width is usually a few thousand dimensions; GPT-3 is a bit over 12,000.
Superposition packs concepts into overlapping directions when dimensions run out.
Anthropic's 2022 “Toy Models of Superposition” is credited for the concept.
Overlap produces interference, which can yield slightly or completely wrong words.

## Scaling result and numbers

The paper's relation, as Grib reports it, is one over width.
Doubling width halves interference and, in his account, related errors.
Each width doubling costs 6 times more, which he calls conservative.
From about $300 million, he projects $1.8 billion, $11 billion, $65 billion,
and then $390 billion to train one model.
Zipf's law allegedly locks the exponent through rare and frequent word usage.
Total error still cannot reach zero because language has ambiguous continuations.
At enough width, no superposition remains, so extra width buys no further gain.
It does not make performance worse; the claimed width benefit falls to zero.

## Implications and limits

Unlimited money or free energy would not steepen this width curve, Grib argues.
That does not rule out gains from data, algorithms, hardware, tools, or retrieval.
It also says nothing direct about inference-time search or longer reasoning.
No test-time scaling method, task, benchmark, sample size, or score is supplied.
GPT-1, GPT-2, and GPT-3 are examples, not identified experimental subjects.
The source does not establish a hard limit for every kind of LLM scaling.
Grib points to learning from video and senses as a different research direction.
These are English automatic captions and may contain transcription errors.
Names, equations, technical terms, and numbers could therefore be imperfect.
