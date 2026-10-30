---
title: "Anthropic Just Gave You 3 Tools That Work While You're Gone."
author: Nate Jones
channel: Nate B Jones
url: https://www.youtube.com/watch?v=3e7gmNPr5Vo
date: 2026-03-28 00:00
tags: ai
---

# Anthropic Just Gave You 3 Tools That Work While You're Gone

[summary](../../summary/nate-b-jones/2026-03-28-anthropic-3-tools-work-while-gone.md)

Anthropic finished shipping three capabilities for Claude that together
close the gap with OpenClaw — but without the security risks. You can
text Claude from your phone, it takes over your desktop, clicks through
screens, navigates tools with no API, and delivers finished work while
you are away. Not a summary to review, not a draft to edit — the thing
itself just gets sorted.

The distinction between work that lands on your desk and work that gets
off of it is the whole game now. Too many AI agent demos are optimized
to look good rather than optimized to actually get work off your desk.

## Building Block 1: Scheduled Tasks

Claude scheduled tasks give you a computer in the cloud you can message
and tell to do stuff on a schedule. You get a repository, a schedule,
and a prompt — Anthropic's infrastructure runs it whether your laptop
is on or not.

Limitations: no sub-minute frequency. Best for hourly, every-two-hours,
every-three-hours recurring tasks. Anthropic dog-foods this internally
— they use scheduled tasks to maintain a Go/Python library sync,
keeping a codebase in one language automatically in sync with another.

It connects to any MCP server you've already wired into Claude —
Linear, GitHub, Slack, OpenBrain, Google Drive. Connectors carry over;
no double configuration.

### Non-Developer Use Cases

- **AI news briefing**: wake up with research already compiled into
  your OpenBrain via a scheduled job
- **Airline price monitoring**: run a schedule every hour, get alerted
  when the price drops below your threshold
- **Bill reminders**: for services without auto-pay, schedule a
  reminder so you never miss a payment

## Building Block 2: Dispatch (Persistence)

OpenClaw had persistence — context carried across sessions. Dispatch
closes that gap for Anthropic, but it's more than persistent chat on
your phone.

When you pair your phone with Claude Desktop via QR code, you get an
orchestration layer. From one conversation on your phone, you can spawn
and manage multiple Claude co-work sessions running simultaneously on
your desktop. Each session runs independently — its own context, file
access, and connectors. Your phone is the command surface; your desktop
is the execution surface. Sessions run in parallel.

### Real-World Example

Pavle Hurin, a product manager, ran Dispatch for 48 consecutive hours.
He went to a kid's bounce house and directed multiple rounds of
iteration from the sidelines — competitor analysis, stakeholder
messaging drafts — all running in parallel across multiple co-work
instances. Over two days he spent roughly 25 minutes entering commands;
Claude executed hours of parallel work.

### Current Limitations

- Desktop must be on (cloud-only execution likely coming soon)
- Each subtask requests folder access individually — no bulk approval
- Can't attach or receive files from phone directly (workaround: sync
  co-work to Google Drive or Dropbox)
- Complex multi-app tasks succeed roughly 50% of the time (labeled
  "research preview")

## Building Block 3: Computer Use

The most consequential piece for builders. MCP connectors are great
but will never reach even 50% coverage of all tools. Computer use
takes the blinders off — Claude can remotely operate any desktop
application through keyboard and mouse, including the web browser.

Use cases: old Jira instances without good MCPs, bespoke ERP screens,
old SAP instances, any tool where you can't get engineering to build
a connector but have a process that has to run.

## OpenClaw vs Anthropic: Not Safety, but Hosting Model

The real difference is self-hosted vs managed:

- **OpenClaw**: infrastructure you roll yourself — configure the
  network, manage credentials, vet skills, troubleshoot websockets.
  More raw freedom. Powerful for developers who want control.
- **Anthropic**: managed infrastructure — scheduled tasks on their
  servers, sandboxed Dispatch, permission-gated computer use. Like the
  shift from self-hosted email to Gmail, rack servers to AWS, Jenkins
  to GitHub Actions.

The self-hosted version comes first and proves the category. The
managed version comes second and gets mass adoption. OpenAI (Peter
Steinberger's team) is watching closely and will launch soon.

## Framework: Getting Work Off Your Desk

### 1. Close Commitment Loops

Every promise you make — in email, Slack, WhatsApp — is an open loop
sitting in your head. Delegate these to agents: revised scopes,
meeting minutes, memoranda of understanding. If quality isn't good
enough, that's a prompting skill issue, not a fundamental limitation.

### 2. Make Better Decisions

Instead of stuffing docs into ChatGPT five minutes before a meeting,
use Dispatch in the morning to develop understanding of the subject.
Push for 70% of available information instead of the usual 30%. Use
computer use to pull dashboards and spreadsheets you normally wouldn't
have time to check.

### 3. Compound Signal Detection

With OpenBrain connected via MCP, your agent detects patterns across
weeks — competitor hiring patterns, patent filings, emerging
strategies — and surfaces them proactively wherever you are.

### 4. Overnight Engineering

Not "run the linter" — real work: migrate a dependency, improve test
coverage to 80%, refactor the authentication layer. Work that's
important but never urgent, exactly what falls through the cracks.

## The Real Shift

The hardest part isn't the technology — it's learning to trust that
the computer is doing work when you aren't looking at it. We need to
learn to untether, to walk away, to touch grass, and to come back with
good decisions about what to give our agents next. That is the meta
skill of 2026.
