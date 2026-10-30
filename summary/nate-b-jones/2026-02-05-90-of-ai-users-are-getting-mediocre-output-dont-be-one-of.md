---
title: 90% of AI Users Are Getting Mediocre Output
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=KX0GurmgAoo
date: 2026-02-05 15:00
tags: ai
---

# 90% of AI Users Are Getting Mediocre Output — Summary

[article](../../articles/nate-b-jones/2026-02-05-90-of-ai-users-are-getting-mediocre-output-dont-be-one-of.md)

Default AI output is the statistical median — optimized for the typical
user via RLHF (reinforcement learning from human feedback). Raters pick
outputs that satisfy most people, so the model learns the middle of the
preference distribution. Your output feels "just a little off" because
it is optimized for someone else.

Four levers beyond prompting to escape the median:

**1. Memory.** ChatGPT: saved memories, chat history references, project
isolation. Claude: RAG-style retrieval, project-scoped memory by default,
import/export. Gemini: personal intelligence connecting Google apps. Key
tactic: explicitly tell the AI to remember specific preferences.

**2. Instructions.** Persistent context about who you are and how you
want the AI to behave. ChatGPT: custom instructions, project workspaces,
custom GPTs. Claude: profile preferences, project instructions, custom
styles (upload writing samples), claude.md files for Claude Code. Key
tactic: be specific. "Be concise" does not steer; "For factual questions,
answer in one sentence" does.

**3. Apps and Tools.** MCP (Model Context Protocol, created by Anthropic)
is USB-C for AI — 10,000+ servers. ChatGPT connects to Gmail/Calendar.
Claude has wider MCP range but variable reliability. Gemini is weaker on
tools. Key tactic: tools steer inputs — turning them on/off changes
response character.

**4. Style and Tone.** ChatGPT: 8 personalities plus granular controls.
Claude: 3 presets plus custom styles from uploaded samples. Key tactic:
avoid conflicts between personality and instructions; pick style matching
actual usage, not aspirational usage.

Common failure: being too vague. "Be more helpful" vs. "When I'm stuck,
ask diagnostic questions rather than giving solutions" — the specific
version transforms output quality.

Compounding returns: capture corrections and encode them back into the
AI. Boris Cherny (Claude Code creator) ships ~100 PRs/week by updating
claude.md for every mistake. Non-engineers can keep a notes file and
review instructions monthly.

Limitations: steering does not fix hallucinations or creative work
ceiling (training data pulls toward center). If you use AI only
occasionally, the investment may not be worth it. If you use it multiple
times weekly for similar work, a few hours of setup buys permanently
better output.
