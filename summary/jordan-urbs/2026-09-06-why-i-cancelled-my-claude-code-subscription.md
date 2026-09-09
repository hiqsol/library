---
title: Why I Cancelled My Claude Code Subscription (And You Should Too)
author: Jordan Urbs
channel: Jordan Urbs
url: https://www.youtube.com/watch?v=yFvl2x8_9gI
date: 2026-09-06 19:38
tags: ai, development
---

# Summary

Jordan Urbs cancelled a Claude Max subscription he loved because too much of his work had
become dependent on one subsidized product. His alternative is an experiment built around
portable workspaces, OpenCode, open-weight models, and explicit model routing.

## The Economics and Lock-In

- Claude Max cost $200 per month, while Urbs sometimes used more than 700 million tokens in
  a day; two peak days exceeded 1.4 billion tokens combined.
- He estimates those two days at more than $50,000 using uncached public API prices, or about
  $1,800 after accounting for prompt caching.
- Flat-rate access made him stop considering per-request cost or whether each task needed the
  strongest model.
- Claude Code supported landing pages, ads, media assets, content workflows, and a book,
  channel, educational game, and Patreon-style site built with his son.
- He calls the resulting dependency “ignorance debt”: convenience discourages understanding
  until switching tools requires rebuilding the workflow.

## The Replacement Is a Portfolio

- A single Claude substitute is the wrong goal; planning, implementation, repetitive work,
  creative writing, and audits can use different models.
- OpenCode supplies a model-agnostic, open-source harness compatible with his existing agentic
  workflows.
- His proposed routing uses Kimi K3 for planning, GLM 5.2 for cheaper implementation and
  writing, DeepSeek V4 Flash for simple tasks, and a frontier model for demanding reviews.
- Venice provides the open-weight models and says it has zero-data-retention agreements with
  inference providers, addressing his concern about profiling the creative process.

## Workspaces Are the Durable Asset

- `AGENTS.md`, reusable skills, and subagent profiles can encode how work is performed and
  which model should receive each task.
- A well-structured workspace reduces context discovery and token use even when two harnesses
  call the same underlying model.
- Smart routing sends expensive models only the work that needs them and lets cheaper models
  implement plans or perform routine transformations.
- Owning portable instructions, knowledge, and routing rules matters more to Urbs than owning
  GPUs; providers and models can then be replaced without rebuilding everything.

## The Experiment

- Venice Max also costs $200 monthly, provides $225 in credits, and offers more than 300
  models.
- Metered credits sacrifice Claude's convenience but force deliberate choices about model
  strength, prompt caching, context size, and reusable instructions.
- Urbs does not yet claim success. He will test the setup for several weeks and acknowledges
  that he may discover gaps or resubscribe to Claude.
- His principle is to rent frontier reasoning when useful while owning the workspace and
  understanding the cost of every prompt.
