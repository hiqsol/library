---
title: One Simple System Gave All My AI Tools a Memory
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=japT66frdhM
date: 2026-03-13 00:00
tags: ai
---

# Summary: One Simple System Gave All My AI Tools a Memory

[article](../../articles/nate-b-jones/2026-03-13-one-simple-system-ai-tools-memory.md)

Nate extends his Open Brain system (personal Supabase database + MCP
server) with a visual "human door" — a web interface that lets both
humans and agents read/write the same data through different doorways.

**The problem:** Chatting through AI is a "keyhole" — text-only, infinite
scroll, no visual overview. You need agent reasoning across data, but you
also need to see data with human eyes. Not many interfaces serve both.

**Architecture:** A structured table in Supabase is the single source of
truth. The agent reads/writes via MCP (already built with Open Brain).
The human reads/writes via a simple web app hosted free on Vercel. No
sync layer, no middleware, no export — consistency is architectural.
When the agent writes a row, it's visible on your phone instantly. When
you edit on your phone, the agent sees it next query.

**How to build the visual:** Describe what you want to Claude/ChatGPT →
it generates a small web app → deploy to Vercel (free) → bookmark on
phone. Behaves like an app without the app store.

**Use cases demonstrated:**

1. **Household knowledge base** — paint colors, plumber contacts, kids'
   shoe sizes, Wi-Fi passwords. Feed facts into Open Brain during
   normal conversation. Visual layer: search bar + auto-categorized
   topics (living room, car, school).

2. **Professional relationships** — log interactions, surface neglected
   contacts. "You haven't reached out to James in months. Last time,
   he was worried about his team's reorg." Visual: flame indicators for
   connections needing attention.

3. **Job search dashboard** — parallel work streams (companies, roles,
   contacts, applications, interviews). Cross-category reasoning: "You
   met someone from their data team at the October conference." Visual:
   pipeline view, pattern insights across interviews, resume version
   performance.

**Design principles:**
1. Agent bridges time — agentic memory doesn't decay like human memory
2. Agent sees across categories — connections between tables humans
   won't cross-reference
3. Agent surfaces → human decides → agent executes

**The flywheel:** Every model upgrade automatically makes your entire
system smarter. OpenClaw (1.5M+ agents spawned in weeks) can monitor
autonomously, but you don't need it — Claude or ChatGPT querying via
MCP already delivers massive value. Start at whatever AI comfort level
you have.

**Key principle:** "Your data is agent-readable. Your AI reaches it
directly. It doesn't scrape a UI. There's no export. It doesn't ask
permission from a platform." Any future AI client plugs into the same
MCP server.
