---
title: They Ignored My Tool Stack and Built Something Better
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=_gPODg6br5w
date: 2026-01-19 15:01
tags: ai
---

# They Ignored My Tool Stack and Built Something Better

## Background

Nate posted a video about building a "second brain" system without any
code, describing a specific stack: Notion for storage, Zapier for
automation, and Claude or ChatGPT for intelligence. The community took
the architecture and implemented it in completely different tools — and
in doing so, revealed four building principles that define how complex
AI systems get constructed in 2026.

## Principle 1: Architecture Is Portable, Tools Are Not

The original stack was Notion + Zapier + Claude/ChatGPT, but community
members built the same system using wildly different tools:

- **Discord + Obsidian + Mac Whisper:** Used Discord as the capture
  point instead of Slack. Mac Whisper transcribes audio locally. Connected
  Mac Whisper to automatically process Zoom recordings, send transcripts
  to Obsidian, then a slash command processes and files everything by
  project.
- **Notion mobile export only:** Capture on phone, export to Notion,
  Claude processes inbox on schedule. No Zapier, no automation chain.
- **Local YAML files + Slack + Claude Code:** Session-based rather than
  always-on. Spin up a Claude Code session that processes inbox, runs
  classification, writes to YAML files.

The architecture — capture point, sorting mechanism, intelligence layer,
retrieval — stayed stable across all implementations. Tools are
interchangeable; patterns are sticky.

**Implication:** Don't memorize tools. Learn patterns. The tools will
shift, but the architectural principles are durable.

## Principle 2: Principles-Based Guidance Scales Better Than Rules

One community member built their system using Claude's computer use
capability with Obsidian and a custom TypeScript agent on a VPS. The
key insight: they wrote an architectural best practices document for the
coding agent using principles rather than rigid rules.

Instead of "always log errors to this specific file," they wrote:

- Use test-driven development
- Use dependency injection
- Don't swallow errors

AI systems are good at applying judgment in context. When you give AI a
principle like "don't swallow errors," it can figure out what that means
in hundreds of situations you did not anticipate. Rigid rules limit the
agent to exactly one behavior.

**Meta-pattern:** People who leverage AI to build their AI tooling go
much faster. Principles-based guidance is fractal — it helps you build
directly, helps you build agents, and those agents can build more than
one thing.

## Principle 3: If the Agent Builds It, the Agent Can Maintain It

One member created a "meta-agent framework" coordinating between Claude
Code, Codex, Copilot, and Goose. They implemented a writer-critic loop
where one agent produces output and another validates it. Their goal:
enable the agent to set up infrastructure rather than doing it themselves.

**The insight:** If the agent sets it up, the agent understands it,
which means the agent can self-correct and self-heal long after you have
forgotten how the system works.

When you build something yourself, six months later you must recover
context — configuration details, edge cases, reasons for choices. That
context switching is non-trivial.

When an agent builds with you and you keep the conversation context and
artifacts, you can reinvoke the agent with all associated memories. No
context switching. The documentation is the build process itself.

**Implication:** Default to involving AI in the construction process,
not just the execution. Let it help set things up. Keep the conversation
going. When something breaks in 6 months, come back to that conversation.

## Principle 4: Your System Can Be Infrastructure, Not Just a Tool

Most people built a personal productivity tool. But at least one member
built something different:

- Postgres for structured data + vector database for semantic search
- An API endpoint letting other applications query their second brain
- Working toward a reusable SDK so other developers can connect any
  application to their knowledge base

Another builder went deep with Qdrant for vector search, Neo4j for
graphing relationships, and Postgres as the system of record, with
multiple Claude agents coordinating through a "skills plus evidence
layer" providing built-in receipts showing what sources informed each
output.

**A tool solves a problem. Infrastructure enables others to build on
top of the solution.** Design with infrastructure in mind and you create
far more leverage.

Technical skills have tremendous value in 2026. Engineers were able to
do much more interesting things with their projects because they have
the domain knowledge to know where to push AI. But learning technical
skills has never been easier — you can learn them with AI.

## The New Build Model: Community + AI

The people who got systems working fastest were not those who followed
the tutorial most carefully. They were those who combined community
knowledge with AI collaboration:

1. Hit an obstacle
2. Post in the community
3. Get a pointer from someone who solved a similar problem
4. Work with Claude or ChatGPT to implement the fix in their own context

One member built the entire system in two hours by giving the
architecture document to Claude and saying "just solve it" — after
reading through community discussion first.

**Community provides a pattern library.** AI provides implementation
muscle. Your job is to provide context, judgment, and intent — deciding
how larger principles should be expressed in a way that works for you.

## The Zapier Automation Walkthrough

The complete flow:

1. **Slack trigger** — new message in SB inbox channel
2. **Anthropic API call** — Claude classifies into categories with
   confidence score
3. **Code step** — cleans response, parses JSON, flattens structure
4. **Path split** — routes by destination (people, projects, ideas,
   admin)
5. **Notion record creation** — in appropriate database
6. **Inbox log entry** — original text, routing, confidence, thread
7. **Slack reply** — "Filed as People: Sarah Chen, confidence 87%.
   Reply 'fix' if wrong."
8. **Needs review path** — low-confidence items get logged with review
   status and request for clarification

## Lessons for Second Brain Builders

- Zapier has limitations at scale — no branching and reconverging
- Storage backend matters less than you think — Notion, Obsidian,
  YAML all work
- Capture interfaces should be where you already live
- Emerging split between session-based and always-on approaches
- Movement toward AI-agent-generated interfaces on demand rather than
  fixed dashboards
