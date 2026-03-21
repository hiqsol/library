---
title: How Boris Cherny Uses Claude Code
author: Boris Cherny
channel: Boris Cherny
url: https://x.com/bcherny/status/2007179832300581177
date: 2026-01-02 19:58
tags: ai, development
---

# Summary: How Boris Cherny Uses Claude Code
Boris Cherny described his own Claude Code setup as "surprisingly vanilla," but the thread shows a
highly structured workflow based on parallel sessions, durable project memory, custom commands,
subagents, hooks, permissions, and MCP integrations.
## Key Points
- Cherny runs `5` terminal Claude sessions in parallel and numbers the tabs `1-5`.
- He uses system notifications so he knows when one of those sessions needs input.
- He also runs `5-10` sessions on `claude.ai/code` in parallel with the terminal sessions.
- He sometimes hands off local sessions to the web, uses `--teleport`, and starts sessions from his
  phone throughout the day.
- `CLAUDE.md` is central to the workflow. One screenshot shows a concrete build-test-lint routine
  with `bun`, typechecking, testing, and pre-PR checks.
- Another screenshot shows Cherny hardening a rule after a mistake by changing an `enum` guideline
  into a stricter "never use enum" instruction.
- The setup uses plan mode explicitly for nontrivial work.
- Custom slash commands compress repeated workflows. One visible example is `/commit-push-pr`.
- The thread also points to personal commands around PR comments, issue fixing, next-task routing,
  and cleanup.
- Cherny keeps specialized agents in `.claude/agents`, including `build-validator`,
  `code-architect`, `code-simplifier`, `oncall-guide`, and `verify-app`.
- Hooks automate post-edit cleanup. One screenshot shows a `PostToolUse` hook running
  `bun run format || true` after `Write|Edit`.
- Permissions are tuned rather than left as constant interruptions.
- Visible allowlist examples include `bq query`, `bun run build`, `bun run lint:file`,
  `bun run test`, `bun run test:file`, `bun run typecheck`, `bun test`, `cc`, `comm`, and `find`.
- The thread also indicates a preference for `ask` as the default permission mode and using
  `--dangerously-skip-permissions` only in safer isolated environments like Docker.
- MCP is part of the setup. One screenshot shows a Slack MCP server configured in `.mcp.json`.
- The workflow assumes long-running sessions are normal; one screenshot shows a Claude session
  thinking for `1d 2h 47m` and spending `2.4m` tokens.
## Data Points
- Thread date: 2026-01-02 19:58 UTC.
- Thread metrics at capture: 1,287 replies, 6,921 retweets, 53,689 likes, 102,521 bookmarks,
  7,938,469 views.
- Terminal sessions named by Cherny: `5`.
- Parallel web sessions named by Cherny: `5-10`.
- Visible subagents in screenshot: `5`.
- Long-running session duration shown in screenshot: `1d 2h 47m`.
- Long-running session token count shown in screenshot: `2.4m`.
- Preserved media in article: `11` screenshots.
## Reader Takeaway
The setup works because Cherny has pushed repeated judgment into files, commands, hooks, and
policies, leaving human attention for orchestration across many simultaneous Claude sessions.
