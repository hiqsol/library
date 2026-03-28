---
title: "Anthropic Just Gave You 3 Tools That Work While You're Gone."
author: Nate Jones
channel: Nate B Jones
url: https://www.youtube.com/watch?v=3e7gmNPr5Vo
date: 2026-03-28 00:00
tags: ai
---

# Summary

Anthropic shipped three primitives for Claude that together replicate
what OpenClaw does — but managed, sandboxed, and without self-hosting.
The thesis: agents should get work off your desk, not create more
reading material.

## Three Building Blocks

**1. Scheduled Tasks** — cloud-hosted cron for Claude. Repo +
schedule + prompt; runs on Anthropic's servers whether your laptop
is on or not. Connects to any existing MCP server. Anthropic uses
it internally to keep a Go/Python library in sync. Best for hourly+
recurring tasks (no sub-minute). Use cases: AI news briefings,
airline price alerts, bill reminders.

**2. Dispatch** — mobile orchestration layer, not just persistent
chat. Phone pairs with Claude Desktop via QR; you spawn/manage
multiple parallel co-work sessions from your pocket. Pavle Hurin
ran it 48 hours — 25 min of commands, hours of parallel execution.
Constraints: desktop must be on, no bulk folder approval, ~50%
success on complex multi-app tasks (research preview).

**3. Computer Use** — keyboard/mouse control of any desktop app
remotely via Dispatch. Covers the vast majority of tools that will
never have MCP servers (old Jira, bespoke ERPs, SAP). The "last
mile" connector.

## OpenClaw vs Anthropic

Not a safety distinction — it's self-hosted vs managed. Same
historical pattern: self-hosted email → Gmail, rack servers → AWS,
Jenkins → GitHub Actions. OpenClaw = more freedom, more ops work.
Anthropic = managed, sandboxed, mass-adoption ready.

## Framework for Agent Work

- **Close commitment loops**: delegate open promises (scopes,
  minutes, memos) — quality issues are prompting skill issues
- **Better decisions**: use Dispatch to pull 70% of data before
  meetings instead of the usual 30%
- **Compound signal detection**: OpenBrain + MCP surfaces patterns
  across weeks (competitor hiring, patents, strategy shifts)
- **Overnight engineering**: real work — dependency migrations, test
  coverage, refactors — not linter runs

## Key Insight

The hardest shift isn't technical — it's learning to trust that work
happens when you're not watching. The meta skill of 2026 is
untethering: walk away, manage from your phone, and let agents carry
the load.
