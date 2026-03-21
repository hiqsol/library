---
title: Claude Code vs Codex — The Harness Decision
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=09sFAO7pklo
date: 2026-03-06 16:00
tags: ai
---

# Summary: Claude Code vs Codex — The Harness Decision

The harness — everything surrounding the model (runtime environment, memory,
tool access, task management) — matters more than the model itself. Same Claude
model scored 78% in Claude Code's harness vs 42% in Small Agents on the CORE
benchmark (AI Engineer Summit, January 2026). Same brain, nearly double the
performance.

**Claude Code architecture:** Runs in your terminal with full machine access.
"Bash is all you need" — composable Unix primitives instead of specialized
tools. Memory via structured artifacts (progress files, CLAUDE.md, git
commits). Forces incrementalism — one feature per session, tasks in JSON not
Markdown. Sub-agents with dedicated context windows, uses cheap Haiku for
exploration, Opus for decisions.

**Codex architecture:** Isolated cloud containers, internet disabled by default.
Memory via repo documentation — anything not in repo doesn't exist. Addressed
"AI slop" entropy with automated cleanup Codex tasks that scan for deviations
and open refactoring PRs. OpenAI built a million-line product with zero manual
code, ~1,500 PRs, initially 3 engineers over 5 months.

**Five divergence dimensions:**
1. Execution: bash primitives (lean tokens) vs Chrome DevTools + per-worktree
   observability (VictoriaLogs/Metrics)
2. Memory: agent remembers (artifacts) vs codebase remembers (repo docs +
   linters whose errors double as remediation instructions)
3. Context: compacting + sub-agent delegation vs clean sandbox per task
4. Tools: MCP-native with just-in-time skill loading (~50-100 token headers)
   vs bidirectional JSON-RPC app server. Composio had to build custom proxy
   to get Codex working with Figma/Jira MCPs
5. Multi-agent: orchestrated collaboration with messaging vs isolated sandboxes
   coordinating through git branches

**Calvin French-Owen's workflow:** Claude Code for planning and exploration,
Codex for implementation ("just straight up has fewer bugs"). Has Codex review
Claude's work — catches mistakes. Built 6+ layers of workflow automation
specific to Claude Code's harness. Moving means rebuilding entire chain.

**Lock-in:** Not vendor subscription lock-in — lock-in to a model-maker's
philosophy of how work should happen. Analogous to AWS vs Azure in 2010.
Switching costs go up every quarter as teams build more infrastructure around
their chosen architecture. These harnesses are leaking into non-coding
knowledge work (Claude Code → CoWork).

**Key message:** Stop comparing models, start comparing harnesses. Treat the
harness decision as a strategic commitment. The era of picking one tool is
ending — route work based on what the task needs.
