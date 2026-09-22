---
title: Jev as a Fast Classifier for Claude Code
author: Jay E
channel: Jay E | RoboNuggets
url: https://youtu.be/tTnUcSj-QPA?is=HSHJmP1x22LcU9bP
date: 2026-09-21 10:40
tags: ai, development
---

# Jev as a Fast Classifier for Claude Code

## What the video presents

Jay E presents Jev as a fast, low-cost classifier beside Claude Code, not a replacement.
It returns binary, menu, or scale decisions while Claude handles generation and reasoning.

Jay calls this a "system one" layer and calls general models "system two" systems.
The title's "10x" is promotional; the video supplies no tenfold productivity benchmark.

## Setup and Claude Code workflow

Access is said to be available directly from TypeSafe with an API key or via OpenRouter.
Jay used OpenRouter, then gave Claude a setup prompt and confirmed that Jev was callable.
No package, repository, model ID, environment variable, or complete prompt is provided.

The integration uses a local router script and a custom Claude Code skill or instruction.
The session switch is captioned as `/jv on`; its spelling and implementation are unverified.
Exact commands should be checked against provider documentation or Jay's linked PDF guide.

## Context and storage

Jev receives a task plus candidate models, skills, or labels and returns one selection.
Claude then delegates, loads the chosen skill, or continues the surrounding workflow.
The custom switch appears to preserve enablement within a Claude session.
No database, durable memory, context rehydration, retention policy, or index is shown.
Semantic media search is demonstrated, but its ingestion and storage architecture are not.

## Jay's three usage levels

1. Route agent work: choose a model or one of about 145 skills before Claude acts.
Jay reports 70% savings across 12 prompts and skill lookup in 5 rather than 30 seconds.
2. Classify business inputs: label leads, support, spam, fraud, refunds, or churn.
A 100-email demo is said to finish in under one second, without accuracy measurements.
3. Build classification-led apps: search Rubric media by meaning rather than filename.
Jay also cites Kits's Unclutter extension for removing ads, banners, and other "slop."

## Benefits, limits, and safeguards

Jay cites 20–200x speed and 40–400x cost claims, plus $0.04 per million input tokens.
The demos look fast, but provide no raw benchmark data, controls, or independent validation.
Keep API keys out of prompts, repositories, logs, and generated Claude Code skill files.
Treat routed content and selections as untrusted; constrain tool and file permissions.
Benchmark route accuracy, final quality, retries, latency, and total cost on real workloads.
Automatic captions vary names such as Jev, "Fable," "Astra," "TypeSafe," and "Opus 5."
## Bottom line

Jev may be a useful decision layer, but persistence belongs to the surrounding system.
