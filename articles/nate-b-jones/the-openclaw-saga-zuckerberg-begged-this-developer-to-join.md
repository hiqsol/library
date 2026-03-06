# The OpenClaw Saga: Zuckerberg Begged This Developer to Join Meta

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=5IzPLjqkFaE)
- **Author:** Nate B Jones
- **Published:** 2026-02-17 15:00

---

## Peter Steinberger Joins OpenAI

Peter Steinberger built the fastest-growing open-source project in
GitHub history from his living room, bleeding $20,000 a month. On
Valentine's Day, he posted three paragraphs announcing he was joining
OpenAI. Sam Altman followed up calling him a "genius" who would drive
the next generation of personal agents.

The announcement landed less than 48 hours after OpenClaw shipped its
most significant security update ever, patching more than 40
vulnerabilities. This is not a coincidence.

## The Origin Story

On a Friday night in November 2025, Peter Steinberger — an Austrian
developer who had already sold his PDF framework company for over
$100 million — sat down and built a prototype in about an hour. The
concept: wire up an LLM to WhatsApp so it could read messages, browse
the web, and execute shell commands.

Steinberger had spent three years deliberately away from tech after
his exit — traveling, therapy, ayahuasca. Before OpenClaw, he had
churned through **43 different projects**. Number 44 was the one.

The initial version connected a messaging interface to Claude. He
open-sourced it as "Claudebot." By mid-January it had ~2,000 GitHub
stars — respectable but not a phenomenon.

Then everything detonated at once:

- **January 27:** Anthropic's legal team sent a trademark notice.
  Steinberger renamed to Maltbot.
- During the renaming, in the literal seconds between releasing his
  old GitHub handle and claiming the new one, **crypto scammers sniped
  the account** and promoted a fake $CLAW token on Solana. They served
  malware from his GitHub and hijacked his npm packages.
- Three days later: renamed to **OpenClaw** with purchased domains,
  trademark searches, and a coordinated account exchange executed with
  "Manhattan Project level secrecy." Spent $10,000 to buy a dormant
  Twitter account.

Each rename triggered new threads on Reddit and Hacker News. The
trademark drama drew media coverage. Maltbook (a social network for
AI agents) went viral.

Result: **200,000 GitHub stars**, 10,000+ commits from 600
contributors in under three months — the fastest-growing repository
in GitHub history.

## Why OpenAI Over Meta

Both Zuckerberg and Altman made concrete offers.

**Zuckerberg:**
- Reached out via WhatsApp
- When Steinberger suggested calling right then, Zuck asked for a few
  minutes — apparently needed to finish coding
- Tried OpenClaw personally, called it "amazing"
- Gave blunt product feedback alternating between praise and pointed
  criticism
- Peter valued the directness and hands-on engagement

**Altman / OpenAI:**
- Promised computational power tied to the Stargate deal
- OpenAI was already contributing tokens to the project
- Steinberger had built OpenClaw using Codex models
- More personal connections and deeper history building on their tech
- Less hands-on product engagement than Zuck

**Deciding factor:** Mission alignment. Steinberger's stated goal —
building an agent his mother could use — requires frontier models and
research pipeline only a hyperscaler lab can provide. OpenAI also
agreed to support OpenClaw as an independent open-source project
through a foundation — a non-negotiable condition.

Steinberger's posture: complete optionality, zero desperation. "The
beauty is if it doesn't work out, I can just do my own thing again."

## What OpenAI Actually Got

OpenAI did **not** acquire OpenClaw. Steinberger joined as an
employee. OpenClaw moves to an independent foundation, remains open
source. Altman confirmed continued sponsorship.

The Chrome/Chromium model: OpenClaw as the open-source engine (like
Chromium), OpenAI's consumer products as the polished commercial layer
(like Chrome).

Three hard-to-replicate assets came with Steinberger:

1. **Developer trust** — built OpenClaw in public, bled cash, routed
   sponsorship money to dependencies. Told Lex Fridman: "I don't do
   this for the money. I don't give a f---."
2. **Architectural knowledge** — gateway architecture, skills
   marketplace (ClawHub), browser control, cron scheduling, multi-model
   support, integrations spanning a dozen messaging platforms, plus
   hard-won security experience
3. **Community** — 600 contributors, chaotic inventive Discord,
   developers building AI-controlled mini breweries, smart home
   automations, DevOps pipelines

## The Competitive Context

- Anthropic's Claude Code hit **$1B ARR** in 6 months
- OpenAI's Codex launched as a macOS app — supposed counter-punch but
  playing catch-up
- Steinberger was publicly calling himself "the biggest unpaid promoter
  for Codex"
- Recorded a 3-hour Lex Fridman episode comparing Codex 5.3 and Opus
  4.6 side by side
- His assessment: Codex reads a large volume of code before starting,
  less interactive but reliable; Claude has stronger role-playing,
  more interactive but sometimes impulsive

He ran 4-10 agents simultaneously, accumulated **6,600 commits in
January alone**, and built most of OpenClaw's codebase by talking to
AI rather than typing.

## The Security Crisis

In late January, security researcher Mav Leven disclosed a high-severity
vulnerability: **one-click remote code execution** through a crafted
malicious link exploiting cross-site WebSocket hijacking.

Broader picture:
- **21,000+** exposed OpenClaw instances publicly accessible (up from
  ~1,000 days earlier)
- Misconfigured instances leaking API keys, OAuth tokens, plaintext
  credentials
- Maltbook's database: **35,000 email addresses** and **1.5 million
  agent API tokens** exposed
- **70%** of ~4,000 skills in ClawHub mishandled secrets through LLM
  context windows (Snyk)
- A bundled hook identified as "soul evil" had inadvertently remained
  in the codebase

Steinberger shipped three rapid security releases culminating in
**40+ security patches** on February 12, two days before announcing
his move to OpenAI. He did not leave the project in a vulnerable state.

## Where OpenAI Goes Next

Altman: Steinberger's work would "quickly become core to OpenAI's
product offerings."

OpenAI appears to be building toward a consumer agent product beyond
ChatGPT — a persistent, always-on personal agent managing email
triage, calendar conflicts, Slack follow-ups, file organization,
proactive task management.

Steinberger told Lex Fridman that OpenClaw-style agents would "kill
80% of apps." His logic: every app is just a slow API to what the
user wants. An agent that knows your location, sleep patterns, stress
levels, and calendar does not need separate apps for fitness tracking,
food ordering, or scheduling.

The deeper shift is not about replacing apps but changing the
interface paradigm from graphical/touch to **delegation**: you tell
the agent what you want done, it figures out which APIs to call.

The hard problem in agentic AI is not model capability — the LLMs
were already good enough. The challenge is integration, persistence,
and the willingness to give an AI system real access to real things.

Steinberger's contribution was not a new algorithm. It was glue code,
architectural decisions, a messaging interface, and the audacity to
let an agent modify its own source code.
