---
title: "McKinsey Says $1 Trillion In Sales Will Go Through AI Agents. Most Businesses Are Invisible."
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=BE4RclIGDmY
date: 2026-03-22 00:00
tags: ai, startups, development
---

# McKinsey Says $1 Trillion In Sales Will Go Through AI Agents. Most Businesses Are Invisible.

[article](../../articles/nate-b-jones/2026-03-22-mckinsey-trillion-sales-ai-agents-invisible.md)

McKinsey projects up to $1 trillion in orchestrated B2C retail revenue from AI agents by 2030 in
the US alone. Shopify's Toby Lütke calls agentic shopping "the transformation of a lifetime."
Over 1 million Shopify merchants are already enabling agent-mediated transactions.

*The core argument:* Claude (250,000 GitHub stars in weeks) validated that people want a unified
agent interacting with the entire digital world on their behalf. But Claude only works as a
paradigm if company systems — not personal systems — are agent-readable and agent-writable at root.
Almost no one is discussing the structural precondition underneath the hype.

*Why this is hard:* The entire 2010s software stack was designed to keep bots out — CAPTCHAs,
gated APIs, JavaScript-heavy interfaces. 15+ years of anti-bot architecture must now be flipped.
Big players (Google, Apple) are still fighting this: Google has moved to shut down Claude bots
using its services; Apple restricted vibe-coding apps including Replit. But the author argues this
is a losing battle — the Napster analogy applies. The people want agent-readable systems.

*The data problem:* You cannot just wrap an existing API in an MCP server and call it done. Making
a company truly agent-readable imposes deep changes on the internal data stack. Humans are
forgiving generalists who skip details; agents are not. ~80% of a product's meaning lives in
marketing copy and tribal knowledge — not in data structures. That 80% is exactly what customers
will ask agents about. It must be extracted and converted into structured, agent-readable data.

*Stripe case study:* Stripe shipped an MCP server for customer lookups, refunds, subscriptions —
a good start. But their Sigma analytics layer (unlimited CSV exports) cannot simply be wrapped in
MCP without overloading context windows. Real agent-readability requires an intermediary database,
careful data partitioning, and serious security design. Even leading companies have not solved this.

*SAP case study:* SAP announced an MCP server for Commerce Cloud. The gap between that thin slice
and all SAP installations being agent-readable by default is "the Grand Canyon." Making most SAP
installs truly agent-readable is a multi-quarter initiative. Vendor pressure from customers will
be one of the biggest stories of 2026.

*Four misconceptions executives hold:*
• "We'll optimize agent discovery like search" — wrong. Agents evaluate structured data against
  explicit constraints; there is no above-the-fold, no ad-spend advantage. Clean schemas win.
• "Schemas only work for simple products" — wrong. Complexity benefits most from agent-readability;
  it removes the friction that forces customers to settle for good enough.
• "Customers won't trust agents to transact" — wrong framing. Trust is a spectrum starting with
  long-horizon intent delegation (e.g., help me evaluate sound systems) and widening over time.
• "We'll wait and see" — lethal. Data cleanup takes months to quarters. Waiting means missing the
  window. By the time a company is ready, agent traffic will have already passed it by.

*The practical exercise:* Have a real conversation with Claude or ChatGPT trying to transact with
your top three competitors, then with your own company. Benchmark how hard it is to get data out.
Identify whether you lead, lag, or could leapfrog. Companies that structure their data around agent
attention first will also find it easier to build great personalized human experiences — clean data
is a force multiplier for both audiences.

*Andrej Karpathy's prediction:* 99% of future attention will be AI/agent attention. Companies
invisible to agents are invisible to that attention. The window to act is now.
