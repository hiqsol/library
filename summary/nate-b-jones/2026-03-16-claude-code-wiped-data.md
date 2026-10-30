---
title: Five Non-Coding Skills for the Agentic Era
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=8lwnJZy4cO0
date: 2026-03-16 00:00
tags: ai
---

# Summary: Five Non-Coding Skills for the Agentic Era

[article](../../articles/nate-b-jones/2026-03-16-claude-code-wiped-data.md)

Nate addresses vibe coders hitting a wall in 2026: the shift from
describing what you want to managing the agent that builds it. Agent
management is not a prompting problem — it's a supervision problem.
Think of yourself as a general contractor managing a construction crew.

**The shift:** In 2025, you got a single code block back. Now agents
execute 8+ steps autonomously — read databases, create tables, build
interfaces, add validation. If step 4 goes wrong, steps 5-8 make it
worse. Real incident: Meta security researcher SummerU had OpenClaw
delete her email inbox despite explicit stop commands — she had to
physically unplug the machine.

**Five skills (none require coding):**

1. **Save points (Git).** Version control = video game save points. A
   senior developer lost a production database to a "minor" agent change
   with no versioning. Learn Git's basics before your next feature.

2. **Know when to start fresh.** Agents have fixed context windows. Around
   message 30, they start ignoring prior instructions. Simple fix: restart.
   Advanced fix: build scaffold documents (workflow file, planning file,
   context file, task list) so you can resume at the 65% mark.

3. **Standing orders (rules files).** Claude Code uses `claude.md`, Cursor
   has its own format, `agents.md` works cross-tool. Start near-empty,
   add a line every time the agent gets something wrong. Keep under 200
   lines (ideally 100) — the file competes for context window space.

4. **Small bets.** Complex changes compound errors exponentially. A 12-step
   change where step 4 fails ruins steps 5-12. Break medium tasks into
   pieces, validate and save between each. Same principle applies to
   PowerPoint generation.

5. **Ask what agents won't.** Three demands: (a) handle failures with
   messages, never blank screens; (b) enforce row-level security, never
   paste secret keys into chat, never log customer emails/payment data;
   (c) set growth expectations early so the agent engineers accordingly.

**When to bring in a pro:** payments beyond basic checkout, medical or
children's data, legal compliance, performance issues under real load,
or a codebase the agent is struggling with. Getting customers first and
hardening later is what most startups never manage — it's a success, not
a failure.
