# How Boris Cherny Uses Claude Code

- **Source:** [X thread by Boris Cherny](https://x.com/bcherny/status/2007179832300581177)
- **Mirror:** [TwStalker thread page](https://twstalker.com/bcherny/status/2007179832300581177)
- **Author:** Boris Cherny
- **Published:** 2026-01-02 19:58

---

Boris Cherny described his personal Claude Code setup as "surprisingly vanilla," but the thread
shows a workflow that is simple mainly because it has been systematized well. The setup is built
around parallel sessions, a strong `CLAUDE.md`, reusable commands, narrow subagents, and explicit
permission policy.

Because X itself is hard to read anonymously, this article reconstructs the thread from public
mirrors and recovered screenshots. The specific commands, filenames, and visible examples are
preserved where they were legible.

## 1. Run Many Claudes in Parallel

Cherny's baseline is concurrency.

- He runs `5` terminal Claudes in parallel and numbers the tabs `1-5`.
- He relies on system notifications to know when one needs input.
- He also runs `5-10` Claude sessions on `claude.ai/code` in parallel with local sessions.
- He sometimes hands off local work to the web with `&` or moves between terminal and web with
  `--teleport`.
- He also starts sessions from the Claude iOS app and checks them later.

This is not a "one chat window" workflow. It is active queue management across many sessions.

![Parallel terminal sessions](https://pbs.twimg.com/media/G9rtc4EasAELEzh.jpg)
![Parallel web sessions](https://pbs.twimg.com/media/G9reZjqaYAA9btU.jpg)

## 2. Let `CLAUDE.md` Carry Operational Knowledge

The thread and screenshots make `CLAUDE.md` look like the core memory file for the workflow.

One screenshot shows a concrete development recipe:

- always use `bun`, not `npm`
- make changes
- typecheck fast
- run tests
- lint before committing
- before opening a PR, run `lint:claude` and `test`

Another screenshot shows Cherny asking Claude to harden a rule after a mistake:

- old rule: prefer `type` over `interface`; avoid `enum`
- new rule: prefer `type` over `interface`; **never use `enum`**

This is the same pattern he later recommends publicly: every mistake should become a durable rule.

![CLAUDE.md workflow](https://pbs.twimg.com/media/G9rfKYRbkAA6Q3w.jpg)
![CLAUDE.md correction example](https://pbs.twimg.com/media/G9rhsVFasAIUCYj.jpg)

## 3. Use Plan Mode Early

One recovered screenshot shows Cherny asking Claude to improve progress-notification rendering and
explicitly entering plan mode.

The implication is consistent with his later thread: put thought into planning first, then let
execution follow from a better plan.

![Plan mode prompt](https://pbs.twimg.com/media/G9rjZcwasAQpPN6.png)

## 4. Build Custom Slash Commands

Cherny's setup includes small high-frequency commands that compress common workflows.

One visible example is:

- `/commit-push-pr` -> "Commit, push, and open a PR"

The mirror-based reconstruction also points to several other personal commands associated with the
thread, including workflows around PR comments, fixing GitHub issues, finding the next task, and
cleanup.

![Custom slash command example](https://pbs.twimg.com/media/G9rj3eFasAEK_8J.jpg)

## 5. Split Specialized Work into Subagents

A screenshot of `.claude/agents` shows several named agent files:

- `build-validator.md`
- `code-architect.md`
- `code-simplifier.md`
- `oncall-guide.md`
- `verify-app.md`

This is a practical pattern: instead of one generic Claude, keep a small stable roster of
specialists whose job boundaries are already encoded.

![Subagent files](https://pbs.twimg.com/media/G9rnUzEasAElFcN.png)

## 6. Add Hooks for Deterministic Cleanup

One screenshot shows a `PostToolUse` hook matching `Write|Edit` and running:

`bun run format || true`

That captures the real point of hooks in this workflow: use them to make routine hygiene automatic
instead of depending on memory.

![PostToolUse hook example](https://pbs.twimg.com/media/G9rrnTxasAAMoZ_.jpg)

## 7. Tune Permissions Instead of Fighting Them

Cherny's screenshots show a broad allowlist for trusted read and build operations rather than a
constant prompt loop.

Visible examples include:

- `Bash(bq query:*)`
- `Bash(bun run build:*)`
- `Bash(bun run lint:file:*)`
- `Bash(bun run test:*)`
- `Bash(bun run test:file:*)`
- `Bash(bun run typecheck:*)`
- `Bash(bun test:*)`
- `Bash(cc:*)`
- `Bash(comm:*)`
- `Bash(find:*)`

The reconstructed thread also indicates that he generally prefers `ask` by default and reserves
`--dangerously-skip-permissions` for safer isolated environments like Docker.

![Permissions allowlist](https://pbs.twimg.com/media/G9rlDa-asAAXlHx.jpg)

## 8. Connect External Systems with MCP

One screenshot shows a `.mcp.json` entry for the Slack MCP server:

`https://slack.mcp.anthropic.com/mcp`

This reflects the broader pattern in Cherny's other thread: connect Claude to the systems where
work already lives instead of forcing all context through manual copy-paste.

![Slack MCP configuration](https://pbs.twimg.com/media/G9rl_pQb0AAILz8.jpg)

## 9. Be Comfortable with Long-Running Sessions

The thread includes a screenshot of a session status line reading:

`Reticulating... (1d 2h 47m · 2.4m tokens · thinking)`

That is a reminder that this setup is not optimized around short chat turns. It assumes some work
should keep running, thinking, and reporting progress over much longer windows.

![Long-running Claude session](https://pbs.twimg.com/media/G9ro4W5bEAAQ3ug.jpg)

## Takeaway

Cherny's setup is "vanilla" only in the sense that it avoids ornamental customization. The real
design is operational:

- many sessions in parallel
- persistent rules in `CLAUDE.md`
- custom commands for repeated tasks
- subagents for specialized work
- hooks for cleanup
- explicit permission policy
- MCP connections into real systems

It is a clean example of treating Claude Code as a working environment, not just a prompt box.
