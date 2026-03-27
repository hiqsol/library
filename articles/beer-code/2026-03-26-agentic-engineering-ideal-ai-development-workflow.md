---
title: "Agentic Engineering: My Ideal AI Development Workflow"
author: Kyrylo (Beer::Code)
channel: Beer::Code
url: https://youtu.be/4uLqamwjl-w
date: 2026-03-26 00:00
tags: ai, development
---

You open a chat with AI and try to cram an entire project into one
prompt: auth, CRUD, tests, deploy — all in one shot. The AI generates
something, you don't even look at it carefully. It seems to work.
Then tests break, you copy-paste tracebacks back and forth, and after
half a day you realize the result isn't what you wanted at all.

The problem isn't the tool. The problem is that you have no process,
no system — just a chat and hope.

## The one-shot trap

Many developers already use AI at work, but 66% say the biggest
problem is that AI writes code that's "almost right but not quite."
Trust in AI has dropped from 70% to 60% over the past year.
The "throw it in the chat and get results" approach simply doesn't
work on real, large projects.

## People who make it work

Boris Cherny — the creator of Claude Code, born in Odessa — says he
hasn't written a single line of code by hand since November 2025.
100% is written by AI. But he's not vibe-coding: he designs
architecture, requirements, tests, and verification. AI only
implements. His focus shifted from "how to write code" to "what
to build."

The visual difference: one-shot is a single arrow from idea to code.
Agentic engineering is a full pipeline where every stage has its own
context, checks, and outputs.

## Full feature development cycle

Kyrylo demonstrates building a salary change module in an existing
product — who changed whose salary, when, by how much.

### Phase 1: Analysis (not code)

Instead of opening an IDE, start with analysis. Using Claude's
skill system (a sequence of skill calls chained into a scenario):

- Market analysis — look at competitors, extract ideas
- Rank proposals by implementation effort vs. value
- Generate a Product Requirement Document (PRD)

At every stage, validate the AI's decisions. If something's off,
correct immediately — make the result predictable.

### Phase 2: Business analysis

Translate product thinking into developer language:
- Break the epic into 5 separate stories
- Each story has its own context and can be implemented independently

### Phase 3: Design mockups

Before writing any code, generate visual mockups:
- Connect to Figma via MCP
- Generate mobile designs, then desktop
- Review, adjust if needed

At this point: zero lines of code written, but full visual picture
of the end result.

### Phase 4: Persist context

Move requirements, stories, and epics to Obsidian (persistent
storage). Claude Code uses the same MD files for task management,
checking off items as it goes. Everything stays visual and editable.

### Phase 5: Implementation

- Activate a worktree so the feature lives in isolation
- Enable agent teams for parallel tasks (tests, code review)
- Use voice input to dictate prompts (the general flow)
- All conventions and rules live in CLAUDE.md

Claude reads project files, pulls tasks from Obsidian,
reads project documentation, and starts implementing the backend:
writing code, writing tests, running them iteratively.

### Phase 6: Code review

After each story implementation — code review. A separate skill
launches 4 agents in parallel:
1. Bug hunting
2. Requirements compliance
3. Test coverage
4. Obsidian spec matching

If problems found — auto-generated fix plan.

### Phase 7: Frontend from Figma

Connect Figma to Claude Code via MCP. Read all styles, design
system, components. Claude generates a plan, you confirm, and the
design transfers directly into code.

The result: not pixel-perfect, some icon differences, but the
general concept and flow match the design system.

## Agentic Engineering vs. Vibe Coding

Andrej Karpathy (OpenAI co-founder) coined "Agentic Engineering"
as the opposite of vibe coding:
- Vibe coding: generate and push blindly
- Agentic engineering: orchestrate agents, control quality,
  understand what's under the hood

## The evolution of software engineering

Each era made writing code cheaper but raised the bar for thinking:
1. Single file → patterns (separated responsibilities)
2. Patterns → frameworks (abstracted routing, models)
3. Frameworks → microservices (separated contexts)
4. Microservices → AI (code generation became cheap)

Competition now shifts to the level of ideas, architecture,
and product decisions. AI can't say "don't build this" — it's
optimized to answer, not to refuse. Half of engineering is choosing
what NOT to build.

## Three takeaways

1. **Design the process**, not just the tools. One connected flow
   beats five separate tools. Start with: "What does my full cycle
   look like?"

2. **AI output is a draft**, not the final result. Every response
   needs validation, business context understanding, and your edits.

3. **Cover the entire SDLC** — not just coding. Analysis,
   architecture, tests, deploy. Let AI help at every stage, but
   only if you've built a system that connects them.
