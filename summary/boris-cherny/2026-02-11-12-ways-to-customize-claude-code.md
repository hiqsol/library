---
title: 12 Ways to Customize Claude Code
author: Boris Cherny
channel: Boris Cherny
url: https://x.com/bcherny/status/2021699851499798911
date: 2026-02-11 21:36
tags: ai, development
---

# Summary: 12 Ways to Customize Claude Code
Boris Cherny argues that Claude Code's standout trait is not just its defaults, but how deeply it
can be customized to match individual and team workflows. The thread frames customization as a
major reason developers adopt the tool and why usage is accelerating.
## Key Points
- Claude Code is designed to be shaped around the engineer through hooks, plugins, LSPs, MCPs,
  skills, effort levels, custom agents, status lines, and output styles.
- Terminal setup is the first layer: `/config` for theme, notifications via iTerm2 or custom hooks,
  `/terminal-setup` for `Shift+Enter` newlines in IDE terminals, Apple Terminal, Warp, or
  Alacritty, and `/vim` for Vim mode.
- `/model` exposes effort levels: `Low`, `Medium`, and `High`, trading off token spend, speed, and
  reasoning quality. The recap says Cherny uses `High` for all tasks.
- `/plugin` installs LSP integrations, MCP servers, skills, custom agents, and hooks. Teams can
  use Anthropic's marketplace or a company marketplace and commit `settings.json` for shared setup.
- Custom agents live in `.claude/agents`, can define tools and policy, and can be made default via
  `settings.json` or `--agent`.
- `/permissions` manages pre-approved allow/block rules. The thread describes the permission system
  as combining prompt-injection detection, static analysis, sandboxing, and human oversight.
- Wildcard permission examples include `Bash(bun run *)` and `Edit(/docs/)`.
- `/sandbox` enables the open source sandbox runtime with file and network isolation. On
  February 11, 2026, Windows support was described as coming soon.
- `/statusline` generates a custom status line from shell config like `.bashrc` or `.zshrc`.
- The status line can show model, directory, remaining context, cost, and other live indicators.
- `/keybindings` remaps keys and applies changes immediately.
- Hooks let teams deterministically intervene in Claude's lifecycle, including routing permission
  requests, nudging continued work after a turn, and preprocessing or postprocessing tool calls.
- Spinner verbs and output styles can both be customized, including `Explanatory` and `Learning`.
- The closing recommendation is to commit shared settings so the whole team inherits the gains.
## Data Points
- Root thread date: 2026-02-11 21:36 UTC.
- Directly recovered reply date: 2026-02-11 21:36:22 UTC.
- Root thread metrics at capture: 166 replies, 383 retweets, 4,427 likes, 7,093 bookmarks,
  572,756 views.
- Directly recovered reply metrics at capture: 68,854 views.
- Supported effort levels named in the thread: 3.
- Shared configuration file: `settings.json`.
- Custom agent directory: `.claude/agents`.
- Scope levels mentioned for settings: codebase-wide, subfolder, personal, and company-wide.
- Claimed current totals: `37` settings and `84` environment variables.
- Preserved media: 1 directly recovered image plus 4 recap images.
## Reader Takeaway
The thread's real claim is strategic: Claude Code becomes more valuable as teams turn one-off
preferences into shared defaults, reusable agents, and policy encoded in `settings.json`.
