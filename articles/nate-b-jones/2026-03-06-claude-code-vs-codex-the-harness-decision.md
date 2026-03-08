# Claude Code vs Codex: The Harness Decision That Compounds Every Week

- **Source:** [YouTube — Nate B Jones / AI News & Strategy
  Daily](https://www.youtube.com/watch?v=09sFAO7pklo)
- **Author:** Nate B Jones
- **Published:** 2026-03-06 16:00

---

## The Model vs the Harness

When you use an AI coding agent, you interact with two things: the model
(intelligence, generates responses) and the harness (everything else). The harness
determines where the AI does its work, whether it remembers between sessions,
what tools it can reach, how it coordinates tasks, and how deeply your team's
dependency grows each week.

The model determines how smart your AI is. The harness determines how usefully it
fits into your work — how it collaborates, what it can touch, what it remembers,
how it fails, and what happens when you want to switch tools in 6 months.

Nobody compares harnesses. Every comparison is about "brains in a jar." This would
be a minor blind spot if harnesses were roughly the same — but they are diverging
fast and on purpose.

## The 78% vs 42% Number

At the AI Engineer Summit in January 2026, Anthropic presented results from the
CORE benchmark (tests agents' ability to reproduce published scientific results).
The same Claude model — identical weights, identical training — scored 78% running
inside Claude Code's harness but only 42% inside Small Agents (a different harness
by another startup).

Same brain, different body, nearly double the performance. This is not prompt
engineering — it's a structural difference in how the harness manages context,
hands off state between sessions, connects tools, and verifies results.

## Two Fundamentally Different Architectures

### Claude Code: The Collaborator at Your Desk

Runs in your actual terminal — your shell, environment variables, SSH keys.
Philosophy: "bash is all you need." Rather than building dozens of specialized
tools, the agent uses composable Unix primitives (grep, git, npm) and chains them
together. Keeps context window lean because tool descriptions are expensive. Gives
the agent access to everything a human engineer would have.

Trade-off: the trust boundary is your entire workstation.

**Memory approach:** Structured artifacts — a progress file (claude-progress.txt)
every coding agent reads at session start and updates at session end, plus a
feature list stored as JSON. Combined with git commits, these create a trail any
new agent instance can follow.

**Key design choice:** The harness forces incrementalism. Without it, models try
to build everything at once ("one-shotting"), run out of context mid-
implementation, and leave half-finished work. The harness structures tasks into a
single JSON (not Markdown — the model is less likely to corrupt structured data)
and prompts the agent to work on exactly one feature per session.

**Verification:** Uses browser automation (Puppeteer MCP server) to test features
end-to-end the way a human would.

### Codex: The Contractor in a Clean Room

Runs tasks in isolated cloud containers. Your code is cloned into the container.
Internet access disabled by default. The agent works independently — thinks
privately and slides finished results under the door.

**Memory approach:** Makes the codebase remember. Architectural decisions, bug
principles, everything gets encoded as documentation in the repo. Anything not in
the repo is illegible to the agent and doesn't exist.

**Entropy problem:** Codex replicates whatever patterns exist in the repo,
including uneven or suboptimal ones, leading to drift. Initial response: spending
every Friday manually cleaning up "AI slop" — didn't scale. Solution: encoded
golden principles into the repo, built automated cleanup where background Codex
tasks scan for deviations and open targeted refactoring PRs. The repo eventually
polices itself.

**Key insight from OpenAI's team:** Built a million-line internal product over
five months using only Codex agents — zero manually written code, ~1,500 pull
requests, initially driven by just three engineers. Early progress was slower than
expected not because Codex couldn't write code, but because the environment was
underspecified.

## Five Dimensions of Harness Divergence

### 1. Execution Philosophy

- **Anthropic:** "Bash is all you need." GitHub MCP server's 38 tools consume
  15,000 tokens of tool descriptions. GitHub CLI achieves the same with far fewer
  tokens.
- **OpenAI:** Wired Chrome DevTools protocol directly into Codex agent — DOM
  snapshots, screenshots, navigation. Every Codex agent gets its own ephemeral
  observability stack (VictoriaLogs + VictoriaMetrics) per git worktree. "Make the
  service start in under 800ms" becomes a testable acceptance criterion because the
  agent can measure startup time.

One gives the agent your hands (powerful, dangerous); the other builds it custom
hands in a controlled room (safer, less reach).

### 2. State and Memory

- **Anthropic:** Agent remembers via artifacts (progress files, CLAUDE.md).
  Compounding asset — more context accumulates, better each session works.
- **OpenAI:** Codebase remembers via repo documentation. Progressive disclosure
  system of focused cross-linked docs the agent navigates, enforced with linters
  (themselves written by Codex) whose error messages double as remediation
  instructions.

### 3. Context Management

Both learned: more context isn't better if it's not curated. OpenAI tried one big
agents.md — failed. Anthropic: stores tools/skills as files, agents retrieve them
just-in-time via tool search (semantic search of available capabilities).

- **Claude Code:** Manages context through compacting the context window and
  delegating to sub-agents with their own windows.
- **Codex:** Each task runs in a clean sandbox — tasks don't compete for space.

Claude is better when one task needs deep codebase understanding. Codex is better
for many independent parallel tasks.

### 4. Tool Integration

Anthropic created MCP (Model Context Protocol) — open standard now backed by
OpenAI, Google, Microsoft, governed by Linux Foundation. Claude Code built around
MCP from the start.

**Anthropic's skills:** Markdown files and scripts on the filesystem. Agent sees
only short names and descriptions (~50-100 tokens), reads full skill definition
only when it decides to use one. Context management as harness design.

**OpenAI's app server:** Bidirectional JSON-RPC harness exposing git, test runners,
Chrome DevTools, app logs, metrics as RPC endpoints. Per-worktree instances with
screenshots and DOM snapshots.

Both speak MCP, but integration philosophies are so different that Composio's
testing team had to build a custom proxy adapter to get Codex working with Figma
and Jira MCPs.

### 5. Multi-Agent Architecture

- **Claude Code:** Spawns sub-agents with dedicated context windows, shared task
  lists, dependency tracking. One sub-agent builds API, another builds frontend,
  third writes tests — they message each other. Uses fast/cheap Haiku for code
  exploration, hands results to Opus for decisions.
- **Codex:** Each task in its own isolated sandbox. Coordination through the
  codebase (git branches that get merged). Isolation means agents can't interfere,
  can't cascade failures — inherently safer for autonomous operation. Parallelism
  still not quite at Claude Code's level per Calvin French-Owen.

## Calvin French-Owen's Workflow

Calvin (helped launch Codex web product, uses both tools extensively) picks his
coding agent based on time available and desired autonomy:

- **Claude Code:** Planning, orchestrating terminal, explaining codebase. Opus
  spins up sub-agents simultaneously, delegates exploration to fast Haiku instances,
  and "is more creative in terms of suggesting things the developer forgot to
  mention."
- **Codex:** Actual code implementation — "the Codex code just straight up has
  fewer bugs."

Workflow: starts with Claude Code, keeps it open, flips to Codex for
implementation. Periodically has Codex review Claude's work — catches mistakes
Claude missed. Views them as complementary architectures, not interchangeable tools.

## The Lock-In Nobody Is Pricing

Calvin's skill evolution illustrates compounding lock-in:

1. Added /commit skill (consistent commit and push)
2. Needed separate worktrees → added /worktree
3. Always planned first → added /implement
4. Started chaining implement calls → added /implement-all
5. At least six layers of workflow automation, each built on the previous

Each layer specific to Claude Code's harness architecture — its skill system,
context forking, sub-agent model. Moving to a different harness means rebuilding
the entire compounding chain in an architecture that may not support the same
abstractions. Multiply by every engineer on the team, every project, all the
Markdown files accumulated, all MCP connectors deployed.

Analogous to early cloud wars: in 2010, AWS and Azure both offered VMs and object
storage. Technically the same, strategically incorrect to treat them as
interchangeable. We're in the 2010 era of AI coding tools.

## Recommendations

- **Developers:** The era of picking one tool is ending. Extract most value by
  using both platforms and routing work based on what the task needs.
- **Engineering leaders:** The decision is not which tool to standardize on but
  which architectural philosophy to organize the team around. This is a process
  design problem, not a procurement problem.
- **Non-technical senior leaders:** Your team is not asking you to buy a wrench —
  they're asking you to commit to a workbench and a way of organizing the
  relationship between humans and AI agents. This will shape velocity, security
  posture, hiring, and switching costs for years.

The right question is not which tool is cheapest. It is which architectural
philosophy matches how the team works, and how much does it cost to change your
mind. The answer to the second question goes up every quarter.

## The Bigger Picture

These harnesses are leaking into non-coding knowledge work. Claude Code was the
foundation for CoWork — basically a skin over Claude Code for knowledge work,
becoming hugely popular. Expect these different architectural approaches to spread
into marketing, product, and customer success through the rest of 2026.

The question "which model is best" has a short shelf life. The real question:
two of the most important companies in AI are making genuinely different bets about
how humans and AI agents should work together, and they are literally training
their models to work within their specific harnesses. Treat a harness decision as
a strategic commitment, because it is one.
