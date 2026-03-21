---
title: One Simple System Gave All My AI Tools a Memory. Here's How.
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=japT66frdhM
date: 2026-03-13 00:00
tags: ai
---

# One Simple System Gave All My AI Tools a Memory. Here's How.

**Abbreviations:**
- **MCP** — Model Context Protocol
- **SaaS** — Software as a Service

---

## The Memory Problem

Agents are the fastest-growing category in software. OpenClaw alone has
spawned over 1.5 million autonomous agents in just a few weeks. Every one
of them has the same limitation: they cannot remember you. Every new session
starts from zero. Every tool switch wipes the slate.

Open Brain — a personal database (Supabase) connected to any AI through an
MCP server — solves persistent memory. Thousands of people built it. The
follow-up question was simple: what do you actually do with a memory system
once you have it?

## From Chatting Through a Keyhole to a Full Interface

When you use Open Brain through a chatbot, you are chatting through a
keyhole — text-only, infinite scroll, no visual structure. You can ask your
agent what is on the family schedule this week and get a text list back. But
you cannot get a calendar that highlights scheduling conflicts and
proactively surfaces context like "remember to pack the kids' school lunch."

That requires two things working together: agent reasoning across data, and
a way for humans to see and interact with the same data visually. Most
interfaces offer one or the other. Open Brain needs both.

## Architecture: One Table, Two Doors

The solution starts from the ground up: a structured table in your Open
Brain Supabase instance. The table is the single source of truth. Two
interfaces access it through different doorways:

1. **Agent door (MCP):** the agent connects through MCP the way it already
   does. It can query the table, write new rows, update existing rows, and
   reason across everything in it alongside every other table in Open Brain.
   Nothing changes about how the agent side works.

2. **Human door (visual web app):** a view that lets you see what is in
   your tables — maintenance log, family schedule, job search pipeline —
   formatted for scanning, not conversation. You can browse by category,
   sort by date, see conflicts highlighted, and edit directly.

There is no sync layer, no export layer, no middleware integration that
might break or lag or lose data. When the agent writes to the table during
a conversation, the entry is immediately visible the next time you pull up
the view on your phone. When you update a field on your phone, the change
is immediately there the next time the agent queries the table. Both sides
read and write to the same rows. Consistency is architectural.

## Building the Visual Layer

The agent side is trivial if you already have Open Brain — create a table,
add columns, and the agent reaches it through MCP immediately.

The human side takes more effort. The process:

1. **Describe what you want** to Claude or ChatGPT: "I want a
   mobile-friendly view of my maintenance table showing every appliance,
   warranty date, and last service date. Highlight anything expiring in
   30 days."
2. **Iterate on the preview.** Adjust layout and highlighting through
   conversation until it matches what you need.
3. **Deploy to Vercel.** Vercel is a free hosting service (paid plans
   exist but are unnecessary for personal use). Create an account, upload
   the application, and Vercel provides a live URL you can open on any
   device. Bookmark it on your home screen — it behaves like an app. No
   app store, no subscription.

Once deployed, both doors are open. The agent reaches the table through
MCP. The visual reaches the same table through a database connection. One
source of truth, two interfaces, each built for what it serves best.

## Use Case 1: Household Knowledge Base

Every household runs on information that lives nowhere: paint colors, kids'
shoe sizes, the plumber from two years ago, the guest Wi-Fi password. The
answer always exists somewhere — a text thread, a receipt in a drawer,
someone's memory — and you can never find it when you need it.

Feed that information into an Open Brain table as you encounter it. You are
talking to Claude about something else and mention the paint color: "Save
this — the living room paint is Benjamin Moore Hale Navy, bought at
Sherwin-Williams in October." Claude writes the entry in two seconds. The
same conversation could happen in ChatGPT or OpenClaw — the data lands in
the same table.

Over a few weeks the table fills with institutional household knowledge.
The visual layer adds a search bar at the top and agent-created categories
underneath: living room, car, kids and school. You can see where knowledge
is recorded, where the gaps are, and get that mental labor out of your head
into something scalable.

## Use Case 2: Professional Relationship Management

Dozens or hundreds of professional relationships matter, but context is
scattered across emails, messages, and memory biased toward the most recent
interaction.

Ask Claude: "Anyone I've been neglecting?" It scans Open Brain and
responds: "You haven't reached out to James in a few months. Last time you
talked, he was worried about his team's reorg. That kind of thing typically
resolves in a quarter — maybe it's a good time to check in."

OpenClaw could catch the same gap autonomously and flag it on a Monday
morning without being asked — the window was closing and the data made it
obvious.

The visual layer shows at a glance which professional relationships need
attention this week, with indicators for urgency. You can filter
dynamically — show only AI-and-education contacts — and the agent can
enrich results with web search to suggest connections one degree away on
LinkedIn.

## Use Case 3: Job Search Dashboard

A job hunt is a dozen parallel work streams pretending to be one activity:
companies, roles, contacts, applications, interviews, follow-ups, resume
versions, compensation data, and your own shifting sense of what you
actually want.

Cross-category reasoning earns its keep here. Paste a job posting into
ChatGPT and ask "What do I have on this company?" It scans contacts,
conference notes, and relationship data: "You met someone from their data
team at the conference in October. Good conversation about distributed
systems — they said they were hiring." A warm introduction instead of a
cold application, surfaced by connecting data across tables.

Time bridging matters too. A contact offered to introduce you to a VP nine
days ago. You meant to follow up but life intervened. OpenClaw catches the
gap overnight: "That was 9 days ago. The window on a warm intro is roughly
2 weeks. You don't want to lose this." You did not have to ask or
remember — an autonomous agent running on a schedule caught what a
session-based chatbot never would.

The visual dashboard shows the full pipeline over coffee: active companies,
early-stage applications, interview patterns, resume version performance
("version 1.3 is doing a lot better"), and insights about company size
trends you had not noticed. The whole thing deploys for free on Vercel
with no SaaS subscription.

## Three Principles for Picking Agent-Ready Problems

### 1. The Agent Bridges Time

Agentic memory does not decay the way human memory does. Anywhere the value
comes from linking events spread across months or years, that is agent
territory. Maintenance dates, annual compliance filings, quarterly tasks
you said you would do but did not — all benefit from an agent that does not
forget.

### 2. The Agent Sees Across Categories

The power is not in any single table but in connections between tables that
humans do not cross-reference. A household knowledge base, a meal planner,
and a maintenance tracker can produce cross-connections: the dishwasher has
not been serviced in six months, so maybe stock easy-to-clean dishes.
Multiple tables talking to each other surface insights most people would
not think of proactively.

### 3. Agent Surfaces, Human Decides, Agent Executes

The agent handles memory and pattern recognition. You handle judgment and
decisions. This division keeps things clean and trustworthy. Open Brain
does not require OpenClaw or any autonomous agent — it works at whatever
level of AI you are comfortable with. Claude, ChatGPT, or a simple data
visualization over your tables already provides enormous value. When you
are ready for autonomous monitoring, the architecture supports it without
changes.

## The Long-Term Bet

Because the data layer is yours, any client can reach it: Claude for
reasoning sessions, ChatGPT for questions, OpenClaw for overnight
monitoring. MCP is becoming ubiquitous — when ChatGPT launches its own
autonomous agent, it will plug into the same MCP server.

The compounding logic is straightforward: every time the models get smarter,
every extension you have built gets more valuable automatically. The agent
reading your family schedule today is useful. Next year's model will
automatically be better at spotting conflicts, anticipating needs, and
doing things you cannot even imagine prompting for right now. All you are
doing is logging data and creating structure so that the intelligence
hundreds of billions of dollars is building goes to work for you.

When a new model drops, your whole system gets smarter. That is the
flywheel.
