# 10 Claude Code Tips from the Team

- **Source:** [X thread by Boris Cherny](https://x.com/bcherny/status/2017742741636321619)
- **Mirror:**
  [Thread Reader App unroll](https://threadreaderapp.com/thread/2017742741636321619.html)
- **Author:** Boris Cherny
- **Published:** 2026-01-31 23:32

---

Boris Cherny shared ten practices that the Claude Code team uses internally. His framing matters as
much as the tips: there is no one "correct" way to use Claude Code. The point is to experiment
until the tool matches your own workflow.

What follows is a cleaned version of the thread, preserving the specific commands, numbers, and
examples that made the advice concrete.

## 1. Do More in Parallel

Cherny calls parallelism the single biggest productivity unlock on the team.

- Run `3-5` git worktrees at once.
- Put a separate Claude session in each one.
- Use shell aliases like `za`, `zb`, and `zc` to jump instantly.
- Some people keep a dedicated analysis worktree just for logs and BigQuery.

Cherny personally uses multiple git checkouts, but says much of the team prefers worktrees.

![Worktrees and parallel Claude sessions](https://pbs.twimg.com/media/HABmmP6bwAAWgUM.jpg)

## 2. Start Complex Tasks in Plan Mode

The team treats plan mode as the default for nontrivial work.

- Start with the plan and invest heavily in it.
- One pattern is to have one Claude write the plan and a second Claude review it like a staff
  engineer.
- If implementation goes sideways, stop and re-plan instead of pushing through.
- Use plan mode for verification, not just for building.

The underlying idea is simple: a strong plan gives Claude a better chance to one-shot the
implementation.

![Plan mode example](https://pbs.twimg.com/media/HABm-MtbEAAMlsS.png)

## 3. Invest in `CLAUDE.md`

This is one of the strongest recurring themes in Boris Cherny's threads.

- After every correction, end with: `Update your CLAUDE.md so you don't make that mistake again.`
- Cherny says Claude is "eerily good" at writing rules for itself.
- Keep editing `CLAUDE.md` until the mistake rate drops in measurable ways.
- One engineer keeps a notes directory for every task or project and points `CLAUDE.md` at it.

This turns one-off feedback into compounding behavior change.

![CLAUDE.md guidance example](https://pbs.twimg.com/media/HABoHn9bQAAE-S1.png)

## 4. Create Skills and Commit Them to Git

The team does not keep good workflows in people's heads.

- If you do something more than once a day, turn it into a skill or command.
- Build a `/techdebt` slash command and run it at the end of each session to find duplicated code.
- Sync seven days of Slack, GDrive, Asana, and GitHub into one context dump with a slash command.
- Build specialized agents, including analytics-engineer-style agents that write dbt models,
  review code, and test changes in dev.

Cherny's point is that repetition should become reusable infrastructure.

## 5. Let Claude Fix Bugs End to End

The team often gives Claude the problem, not the procedure.

- Enable the Slack MCP.
- Paste a Slack bug thread into Claude and just say `fix`.
- Or say `Go fix the failing CI tests.`
- Point Claude at Docker logs to troubleshoot distributed systems.

This reduces context switching and offloads the "how" to Claude.

![Bug fixing from Slack and logs](https://pbs.twimg.com/media/HABy6cObEAQ4Rep.png)

## 6. Level Up the Prompting

Cherny's examples are less about wording tricks and more about forcing stronger thinking.

- Tell Claude to grill you on the change and not make a PR until you pass.
- Ask Claude to prove behavior differences between `main` and your feature branch.
- After a mediocre fix, say:
  `Knowing everything you know now, scrap this and implement the elegant solution.`
- Reduce ambiguity before handoff by writing detailed specs.

The message is that strong prompting often means stronger standards, not more decoration.

## 7. Improve the Terminal and Environment

The team optimizes the shell like a real operating surface.

- Cherny says several teammates like Ghostty for synchronized rendering, `24-bit` color, and proper
  Unicode support.
- Use `/statusline` to keep context usage and current branch visible.
- Color-code and name terminal tabs, sometimes with `tmux`.
- Use voice dictation because you can speak roughly `3x` faster than you type.

![Terminal and statusline setup](https://pbs.twimg.com/media/HABpv-MbEAAIskz.jpg)

## 8. Use Subagents Deliberately

The team uses subagents both for throughput and for context hygiene.

- Append `use subagents` when you want Claude to spend more compute.
- Offload narrow tasks to subagents so the main agent stays focused.
- Route permission requests to `Opus 4.5` through a hook so it can scan for attacks and
  auto-approve safe cases.

This pushes more work into structured delegation instead of one overstuffed context window.

![Subagent example](https://pbs.twimg.com/media/HAB0KLmbEAEfDJ6.png)

## 9. Use Claude for Data and Analytics

The team does not treat Claude Code as only a coding tool.

- Use the `bq` CLI inside Claude Code to pull and analyze metrics on the fly.
- The team keeps a BigQuery skill checked into the repo.
- Cherny says he has not written a line of SQL in `6+ months`.
- The same approach applies to any database exposed through a CLI, MCP, or API.

## 10. Learn with Claude

The thread closes with a learning workflow, not just a production workflow.

- Turn on the `Explanatory` or `Learning` output style in `/config`.
- Ask Claude to generate a visual HTML presentation for unfamiliar code.
- Ask it to draw ASCII diagrams of protocols and codebases.
- Build a spaced-repetition skill where you explain your understanding and Claude probes the gaps.

## Takeaway

The thread is really about compounding leverage. Parallel worktrees, plan mode, `CLAUDE.md`,
skills, MCPs, subagents, and learning loops all turn Claude Code from a chat interface into a
personal operating system for work.
