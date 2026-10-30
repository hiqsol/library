---
title: "Agentic Engineering: My Ideal AI Development Workflow"
author: Kyrylo (Beer::Code)
channel: Beer::Code
url: https://youtu.be/4uLqamwjl-w
date: 2026-03-26 00:00
tags: ai, development
---

# Agentic Engineering: My Ideal AI Development Workflow

[article](../../articles/beer-code/2026-03-26-agentic-engineering-ideal-ai-development-workflow.md)

Ukrainian developer Kyrylo demonstrates a full feature development
cycle using AI — from analysis to deploy — building a salary change
module in a real product.

## Core argument

The "one-shot" approach (dump everything into one prompt) fails on
real projects. 66% of developers say AI writes "almost right" code.
Trust dropped from 70% to 60% in one year. The fix isn't better
tools — it's building a systematic process.

## The workflow (7 phases, zero code until phase 5)

1. *Analysis* — market research, competitor analysis, ranked
   proposals, PRD generation. Validate at each step.
2. *Business analysis* — break epic into independent stories
   with separate contexts.
3. *Design mockups* — Figma via MCP, mobile + desktop, before
   any code.
4. *Persist context* — store requirements in Obsidian; Claude Code
   uses same MD files for task tracking.
5. *Implementation* — worktrees for isolation, agent teams for
   parallel work, voice-dictated prompts, CLAUDE.md for conventions.
6. *Code review* — 4 parallel agents: bugs, requirements, tests,
   spec compliance. Auto-generated fix plans.
7. *Frontend from Figma* — MCP reads design system, Claude
   generates matching code.

## Key references

- Boris Cherny (Claude Code creator, from Odessa): hasn't written
  code by hand since Nov 2025. Designs architecture + requirements,
  AI implements.
- Andrej Karpathy coined "Agentic Engineering" — orchestrating
  agents vs. vibe coding (blind generate-and-push).

## Three takeaways

1. Design the process, not tools. One connected flow > five
   separate tools.
2. AI output is a draft. Every response needs validation and
   business context.
3. Cover the entire SDLC — analysis, architecture, tests, deploy —
   not just coding.

## Meta-insight

Each era of software made code cheaper but raised the thinking bar:
single file → patterns → frameworks → microservices → AI. Now
competition is at the level of ideas and architecture. The most
valuable engineering decision is saying "no" — AI never will.
