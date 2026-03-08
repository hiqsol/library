# Summary: 10 Claude Code Tips from the Team
**Author:** Boris Cherny
**Published:** 2026-01-31 23:32
Boris Cherny shared ten usage patterns sourced from the Claude Code team and emphasized that there
is no single right setup. The core message is to experiment until Claude Code matches your own
workflow and to turn repeatable practices into reusable system behavior.
## Key Points
- The top team recommendation is parallelism: run `3-5` git worktrees, each with its own Claude
  session.
- Some teammates name worktrees and use shell aliases like `za`, `zb`, and `zc`.
- One pattern is to keep a dedicated analysis worktree for logs and BigQuery.
- Complex tasks should begin in plan mode, with heavy effort invested in the plan itself.
- One teammate uses one Claude to draft the plan and a second Claude to review it as a staff
  engineer.
- If implementation goes sideways, the team switches back to plan mode and re-plans.
- `CLAUDE.md` should be updated after corrections so Claude does not repeat the same mistake.
- Cherny says Claude is unusually good at writing rules for itself.
- Some engineers keep task or project notes directories and point `CLAUDE.md` at them.
- If something is done more than once a day, the team suggests turning it into a skill or command.
- Example commands include `/techdebt` and context-dump commands spanning Slack, GDrive, Asana, and
  GitHub.
- The team uses Slack MCP and Docker logs so Claude can fix bugs with minimal micromanagement.
- Cherny's prompting advice is to raise standards: ask Claude to grill you, prove behavior, or
  scrap a mediocre fix and implement the elegant one.
- Several teammates like Ghostty and use `/statusline`, color-coded tabs, and `tmux`.
- Voice dictation matters because speaking can be around `3x` faster than typing.
- Subagents are used both to add compute and to keep the main context window clean.
- Permission requests can be routed through hooks to another model for threat scanning.
- Claude Code is also used for analytics via `bq`, with a BigQuery skill checked into the repo.
- Cherny says he has not written SQL in `6+ months`.
- For learning, the team uses `Explanatory` and `Learning` output styles, HTML slide decks, ASCII
  diagrams, and spaced-repetition-style skills.
## Data Points
- Thread date: 2026-01-31 23:32 UTC.
- Thread metrics at capture: 903 replies, 5,824 retweets, 50,727 likes, 104,051 bookmarks,
  8,984,837 views.
- Parallel worktrees recommended: `3-5`.
- Example shell aliases: `za`, `zb`, `zc`.
- External context dump example: `7` days of Slack, GDrive, Asana, and GitHub.
- Voice speed claim: roughly `3x` typing speed.
- Model named in permission hook example: `Opus 4.5`.
- SQL abstinence claim: `6+ months`.
- Preserved media in article: `6` thread images.
## Reader Takeaway
The practical edge comes from codifying habits: work in parallel, plan explicitly, continuously
improve `CLAUDE.md`, and convert repeated tasks into skills, hooks, and structured subagents.
