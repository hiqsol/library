---
title: "90% of AI Users Are Getting Mediocre Output: Stop Prompting, Do This"
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=KX0GurmgAoo
date: 2026-02-05 15:00
tags: ai
---

# 90% of AI Users Are Getting Mediocre Output: Stop Prompting, Do This

## How AI Averages You Out

Nobody gets 10x results from default vanilla ChatGPT, Claude, or Gemini.
Most people have slept on the big levers that model makers have released
for customization.

Default AI output is the statistical middle — the median. It is the Pizza
Hut approach: not trying to give you the best response for your situation,
but the best response for everybody who might ask a similar question.

### Why This Happens: RLHF

Modern AI assistants go through reinforcement learning from human feedback
(RLHF). The model generates multiple responses. Human raters compare them
and pick which seems better. The model learns to produce outputs raters
would choose.

The raters are not experts in your field. They do not know your
constraints or preferences. Their optimization target is "produce
something a typical human would rate highly." When thousands of raters
evaluate millions of outputs, the model learns to hit the middle of the
preference distribution — the answers that satisfy most people.

The training that makes models helpful in general is exactly what makes
them mediocre for you specifically. Every time you use default settings,
you get an answer optimized for a hypothetical typical person. You are not
typical.

## The Four Levers Beyond Prompting

### Lever 1: Memory

Memory is AI retaining information about you across conversations.

**ChatGPT:**
- Saved memories: facts you explicitly ask it to remember
- Chat history sense: references past conversations with clickable
  citations
- Project-only memory: discussions stay isolated per project
- Temporary chats now retain memory, style, and personalization

**Key tactic:** Tell ChatGPT to remember specific preferences. "Remember
I prefer one-sentence answers to factual questions." Intentional memory
is more reliable than automatic capture.

**Claude:**
- RAG-style retrieval: can search past conversations
- Memory summary: synthesizes key facts across history, updates
  periodically
- Project-scoped by default: each project has a separate memory space
- Supports memory import/export between accounts

**Key tactic:** Use projects deliberately. Each project gets its own
memory and instructions. Create a project for each distinct context.

**Gemini:**
- Personal intelligence connecting to Google apps (Gmail, Photos,
  YouTube)
- Can find your car model from a Gmail receipt to recommend tires
- Settings > Personalization lets you connect/disconnect specific apps

**Key tactic:** Decide how much data you are willing to give Google.
Full connection gives immediate personalization; the trade-off is privacy
surface area.

### Lever 2: Instructions

Persistent context about who you are and how you want AI to behave.
Severely underused by most people.

**ChatGPT:**
- Custom instructions (multiple text fields)
- Project-specific workspaces with their own instructions
- Custom GPTs

**Key tactic:** Be specific. "Be concise" does not steer the model.
Instead: "For factual questions, answer in one sentence. For analysis
requests, walk through reasoning step by step."

**Claude:**
- Profile preferences, project instructions, styles
- Custom style feature: upload samples of your best work and Claude
  generates a style profile matching your tone and sentence structure
- Claude markdown files (for Claude Code): project architecture, coding
  standards, common commands. Checked into Git. Whole team contributes.

**Key tactic:** Boris Cherny (Claude Code creator) describes his team's
practice: whenever Claude does something wrong, add a rule to the
claude.md file. Within a month, it is comprehensive.

### Lever 3: Apps and Tools

Capabilities the AI can use: searching the web, running code, creating
files, reading documents.

**Model Context Protocol (MCP):** The universal interface standard for
connecting AI to external tools. Created by Anthropic, adopted widely.
Over 10,000 MCP servers exist. Think of it as USB-C for AI.

**ChatGPT:** Apps connect to Gmail, Calendar, etc. Automatically
references them where relevant (though "where relevant" is ambiguous).

**Claude:** Wider range of MCP servers, but connectivity varies. Easy to
connect Figma; tricky for Stripe. Changes as implementations mature.

**Gemini:** Shorter on tool use than it should be — a big weakness of
the ecosystem.

**Key tactic:** Tools steer inputs, not just add features. Turning tools
on and off changes the character of responses. Be intentional about what
you want.

### Lever 4: Style and Tone Control

**ChatGPT:** Eight personalities (friendly to cynical) plus granular
controls for warmth, enthusiasm, headers, emojis.

**Key tactic:** Ensure no conflict between personality and instructions.
If instructions say "be verbose" and personality says "concise," you just
burn tokens.

**Claude:** Three built-in presets (formal, concise, explanatory) plus
custom styles from uploaded writing samples.

**Key tactic:** Pick a style that reflects your actual usage, not your
aspirational usage. If you are a casual user, do not select formal.

## The Common Failure Mode: Being Too Vague

"Be concise" does not move you. "Be direct" does not move you. Compare:

| Vague                        | Specific                              |
|------------------------------|---------------------------------------|
| "Be more helpful"            | "When I'm stuck, ask diagnostic       |
|                              | questions rather than giving solutions.|
|                              | I learn better by being guided."       |
| "I'm a professional"         | "I've done product for 15 years.      |
|                              | Skip fundamentals, go to nuance."     |

The specific versions tell the AI where you are and help it help you.

## Compounding Returns

Every interaction generates information about what you need. Most people
correct in their head, get frustrated, and move on. People getting 10x
results do something different: they capture corrections and encode them
back into the AI.

- Notice a pattern of corrections? Add it to instructions.
- Tell memory to retain it.
- Update style settings.

Boris Cherny runs 5 Claude Code instances in parallel and another 5-10
on claude.ai, shipping roughly 100 PRs per week. His workflow is not
magic — it is the discipline of updating a rule in claude.md for every
mistake Claude makes.

You do not need to be an engineer. Keep a notes file. Find yourself
making the same correction twice? Write it down. Review instructions
monthly. The gap widens over time as you invest in the levers.

## What Steering Does Not Fix

- **Hallucinations** are not an averaging problem. No amount of personal
  context fixes them.
- **Creative work** has a ceiling. Training data pulls toward the center
  of the distribution. You can steer against it but are fighting gravity.
- **Effort cost.** If you use AI only occasionally, steering may not be
  worth the investment. If you use it multiple times a week for similar
  work, a few hours of setup buys permanently better output.

## Getting Started Simply

Pick one task where you use AI regularly and the output does not feel
right. Over the next few sessions, notice what adjustments you make and
write them down. Then find the custom instruction setting for your
preferred AI and add those notes. Notice the difference. Iterate.

> The median is not mandatory. Default output is optimized for typical
> users with typical needs. You are not typical. Your levers are memory,
> instructions, tools, and style. Most people use none or one. Using
> more than one compounds toward a personalized AI that actually fits
> you.
