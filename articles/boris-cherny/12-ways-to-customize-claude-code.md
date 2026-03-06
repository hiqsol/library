# 12 Ways to Customize Claude Code

- **Source:** [X thread by Boris Cherny](https://x.com/bcherny/status/2021699851499798911)
- **Supplemental mirror:**
  [lucas recap quoting the thread](https://x.com/lucas_flatwhite/status/2021732731894608126)
- **Author:** Boris Cherny
- **Published:** 2026-02-11 21:36

---

Boris Cherny framed Claude Code's growth around one idea: developers adopt the tool not only
because the defaults are good, but because the product is unusually easy to shape around personal
and team workflows.

The original X thread was only partially recoverable directly from mirrors, so this article
reconstructs the full thread from the root post, one directly recovered reply, and a same-day recap
that quoted the numbered points and preserved thread images.

## Core Thesis

Claude Code is meant to be molded to the engineer, not the other way around. The thread organizes
that idea into a practical checklist:

- tune the terminal experience
- choose the right effort level for the task
- install plugins, MCPs, skills, and custom agents
- reduce friction with permissions and sandboxing
- add status lines, keybindings, hooks, and output styles
- commit shared settings so teams benefit from the same improvements

## 1. Configure the Terminal

The first customization layer is the shell itself.

- Run `/config` to set light or dark mode.
- Enable notifications in iTerm2, or wire up a custom notifications hook.
- In IDE terminals, Apple Terminal, Warp, or Alacritty, run `/terminal-setup` so `Shift+Enter`
  inserts a newline instead of forcing you to escape with `\`.
- Run `/vim` if you want Vim-style editing.

Reference: <https://code.claude.com/docs/en/terminal-config>

![Claude Code terminal configuration screenshot](https://pbs.twimg.com/media/HA6EwD8bsAQnna5.jpg)

## 2. Adjust the Effort Level

Cherny's second point is to deliberately choose how much reasoning budget a task deserves.

- Run `/model` and pick the preferred effort level.
- `Low` favors speed and lower token usage.
- `Medium` aims for a balance.
- `High` spends more tokens for stronger reasoning.
- In the recap, Cherny is described as preferring `High` for all tasks.

## 3. Install Plugins, MCPs, and Skills

Customization scales when it becomes reusable.

- Use `/plugin` to install plugins.
- Plugins can bring in LSP integrations, MCP servers, skills, custom agents, and custom hooks.
- Teams can rely on Anthropic's marketplace or stand up an internal marketplace.
- Shared marketplace configuration belongs in `settings.json`, committed to the repo so teammates
  inherit it automatically.

## 4. Create Custom Agents

Claude Code can be split into role-specific workers instead of one generic assistant.

- Add Markdown files to `.claude/agents`.
- Each agent can define its own name, color, tools, allow/block lists, permission mode, and model.
- You can also set the default agent for the main conversation.
- The thread points to both the `agent` field in `settings.json` and the `--agent` CLI flag.
- `/agents` is the starting command.

## 5. Pre-Approve Common Permissions

The thread treats permissions as a productivity surface, not just a safety feature.

- Run `/permissions` to manage allow and block lists.
- Cherny describes Claude Code's permission model as combining prompt-injection detection, static
  analysis, sandboxing, and human oversight.
- Safe commands are pre-approved by default.
- Teams should commit shared permission rules in `settings.json`.
- The recap includes wildcard examples such as `Bash(bun run *)` and `Edit(/docs/)`.

## 6. Turn On Sandboxing

Sandboxes reduce both risk and approval spam.

- Run `/sandbox` to enable the open source sandbox runtime.
- The thread says it supports both file isolation and network isolation on the local machine.
- As of February 11, 2026, Windows support was described as coming soon.

## 7. Add a Status Line

The status line is presented as a lightweight dashboard for the current session.

- Run `/statusline`.
- Claude can generate a status line from your existing shell setup, such as `.bashrc` or `.zshrc`.
- The status line can expose model, directory, remaining context, cost, and other live signals.
- Cherny says people on the Claude Code team use very different status lines, which reinforces the
  theme of personal tailoring.

## 8. Customize Keybindings

Keyboard control is another way to make the tool feel native.

- Run `/keybindings`.
- Re-map any key you want.
- Changes apply immediately.

## 9. Add Hooks

Hooks are the most powerful customization point in the thread because they intervene in Claude's
lifecycle deterministically.

Examples mentioned in the recap:

- route permission requests to Slack or Opus automatically
- nudge Claude to keep going when a turn ends
- preprocess or postprocess tool calls, such as for logging

The thread's pragmatic advice is simple: ask Claude to add the hook for you and iterate from there.

## 10. Customize Spinner Verbs

This is a smaller detail, but it matters because it makes the tool feel personal.

- Replace or extend the verbs used in the loading spinner.
- Commit the shared configuration if the team wants a common style.

## 11. Use Output Styles

Output style changes how Claude explains itself while it works.

- Use `/config` to select an output style.
- `Explanatory` is meant for learning a new codebase while Claude narrates frameworks and patterns.
- `Learning` is meant to coach the user through the code-change process.
- Teams can also define their own house style so Claude sounds and structures work the way they
  prefer.

## 12. Commit Shared Settings and Keep Going

Cherny's closing advice is not one feature, but a rule for scaling customization.

- If a setting improves your workflow, commit it so the team gets the benefit.
- Scope can live at multiple levels: repo-wide, subdirectory-specific, personal, or company-wide.
- The recap says Claude Code currently supports `37` settings and `84` environment variables.
- It also advises using the `env` field in `settings.json` instead of wrapper scripts.

## Images Preserved with the Thread

The same-day recap preserved four images associated with the thread:

![Thread recap image 1](https://pbs.twimg.com/media/HA6jDqpbsAIHXVE.jpg)
![Thread recap image 2](https://pbs.twimg.com/media/HA6jDqibsAIC3dq.png)
![Thread recap image 3](https://pbs.twimg.com/media/HA6jDqcbUAA42AD.jpg)
![Thread recap image 4](https://pbs.twimg.com/media/HA6jDqka8AAEBTX.jpg)

## Takeaway

The thread is less about hidden tricks than about a product philosophy. Claude Code is being
positioned as an adaptable working environment: terminal, permissions, agents, hooks, styles, and
team defaults all become part of the tool's real value.
