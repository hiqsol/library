---
title: How Vercel Solved Agent Building
author: Andrew Qu
channel: AI Engineer
url: https://youtu.be/9dYcwOkpCE8?is=Qe3sSd4u8WeXL-3P
date: 2026-09-14 17:00
tags: ai, development
---

# How Vercel Solved Agent Building

[article](../../articles/andrew-qu/2026-09-14-how-vercel-solved-agent-building.md)

## The problem

- Andrew Qu describes Vercel's attempt to put useful agents across business teams.
- A lean data team kept dropping planned work to answer ad hoc company questions.
- The goal became an agent that could query, analyze, and report without that interruption.

## Six stages

1. A mega-prompt generated SQL from a schema, but Qu still copied and ran it manually.
2. A multi-agent pipeline split planning, execution, SQL, and reporting but lost context.
3. One stateful agent could revisit errors and run for at most 100 steps.
4. A sandboxed filesystem agent used Bash and file tools for open-ended exploration.
5. A recurring job distilled repeated solutions into reusable skills.
6. Eve packaged the lessons as a convention-based framework for building agents.

## Reported scale and results

- Vercel's AI SDK reduced a provider switch from 300-400 changed lines to one line.
- Qu says 30% of evals passed, yet trusted users called the agent awful on novel questions.
- Qu says the filesystem redesign roughly doubled the data agent's eval score.
- He says its launch article drove 70% of vercel.com traffic during one week.
- He reports thousands of daily queries and a library of roughly 100 skills.
- He reports roughly 20 Vercel agents with decent product-market fit.

## Runtime and project model

- Eve uses conventional folders for system instructions, skills, tools, and channels.
- Its runtime covers durability, isolated execution, model calls, and connections.
- Open-source adapters include PostgreSQL, the OpenAI Responses API, and Docker.
- Vercel options include Workflows, Sandbox, and Connect with short-lived OIDC tokens.
- Deployments expose runs, tool calls, steps, estimated costs, and optimizations.
- Builders can start from a template, deploy on Vercel, or self-host from eve.dev.

## Customer and thesis

- Qu says Aura rebuilt a service-testing agent that visits, installs, and tries websites.
- He reports fewer steps, better success, and better insights than its prior approach.
- The key advantage is not warehouse access alone but company-specific knowledge.
- That includes terminology, data relationships, procedures, and source-selection judgment.
- Skills preserve this knowledge so each run does not restart from an empty context.
- Generic infrastructure lowers friction; proprietary operating context creates usefulness.

## Caveat

- This summary uses auto-captions and cautiously normalizes obvious product names.
- Eve is supported by repeated transcript references to the framework and eve.dev.
- Performance, adoption, and customer outcomes are Qu's claims, not verified facts.
