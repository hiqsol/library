---
title: "Field Guide to Fable: A Research System for UI Generation"
author: Thariq Shihipar
channel: AI Engineer
url: https://youtu.be/9fubhllmsBU?is=xiEOaLziyYvJUVrx
date: 2026-07-06 16:00
tags: ai, development
---

# Field Guide to Fable: A Research System for UI Generation

[article](../../articles/thariq-shihipar/2026-07-06-field-guide-fable-ui-generation.md)
## Thesis and scope
Shihipar presents Fable as a model whose useful behavior must be discovered empirically.
This summary treats his method as a research system for generating and refining UIs.
The talk is not a formal UI study and gives no model architecture or training-data detail.
Caption caveat: automatic captions may mishear names, versions, and technical terms.
## Research goal and design
The goal is to expose capability overhang while finding gaps between a spec and reality.
Shihipar calls the spec a map and the codebase, constraints, and real world the territory.
His evaluation loop inspects context, generates options, interviews users, and logs choices.
It then reviews the implementation and quizzes the operator to preserve understanding.
No sample size, controlled baseline, user study, or UI benchmark is reported in the talk.
## Data and system design
The workflow creates working context, not training data: blind spots, prototypes, answers,
references, implementation notes, and quizzes become evidence for the next decision.
Shihipar says models are “grown, not designed” through data, feedback, and compute.
He argues that the harness determines which uneven, or “spiky,” abilities users can reach.
Anthropic removed 80% of Claude Code's system prompt, according to Shihipar.
He attributes that change to newer models needing context more than constraining examples.
## UI generation workflow
First, ask Fable to inspect the product and identify unknown unknowns and major constraints.
Second, generate one HTML page with four genuinely different design directions.
Third, use reactions to surface tacit taste and convert it into explicit requirements.
Fourth, have Fable ask questions that could change architecture, state, or data flow.
Fifth, supply code and an HTML mock-up as references for implementation in the real stack.
Finally, log deviations, inspect edge states, and quiz the human before handoff or merge.
## Findings and examples
Shihipar says chat fails on Pokémon names ending in “aw,” despite knowing the names.
He says Claude Code fetches a list and filters it to find Croconaw and Drednaw.
He uses this comparison to argue that tools can reveal otherwise inaccessible capability.
He contrasts pasted context with a coding agent that searches and builds its own context.
He also describes output evolving from Markdown to plans and interactive HTML reports.
According to Shihipar, the question tool progressed from fragile calls to HTML interviews.
He reports making the talk's deck with Fable in about four hours.
He also says tasks that once took weeks in an old codebase could take hours for him.
These productivity examples are personal anecdotes, not controlled general estimates.
## Metrics, limits, and lessons
Reported quantities include 80% less system prompt, 40 questions, four designs, and 4 hours.
The talk gives no accessibility, render, defect, preference, latency, cost, or value metric.
It compares workflows and model generations, not Fable against named UI products.
Teams should separately measure unresolved unknowns, deviations, quality, speed, and value.
A generated mock-up can hide loading, error, empty, permission, and responsive states.
Shihipar warns that easier building does not make valuable product choices easy.
His “good, fast, cheap” challenge is an ambition, not proof that trade-offs disappeared.
The implementation lesson is to inspect reality, diversify prototypes, and record decisions.
Keep the human able to explain the architecture and revisit the harness as models change.
