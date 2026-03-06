# OpenAI Is Slowing Hiring, Anthropic's Engineers Stopped Writing Code — Summary

Sam Altman admitted he still has not changed his workflow despite knowing
he should use AI more. Meanwhile Andrej Karpathy inverted from 80% manual
coding to 80% AI agents in weeks. Ethan Mollick: "Projects from 6 weeks
ago may already be obsolete." Capability jumped; adoption has not.

December 2025 convergence: in 6 days, three frontier models shipped —
Gemini 3 Pro, GPT 5.1 Codex Max (then 5.2), Claude Opus 4.5. All
optimized for sustained autonomous work (hours/days, not minutes). Opus
4.5 priced 2/3 cheaper with a new effort parameter. Context compaction
enables coherence over longer sessions. Reports: models can code a week
autonomously, up to 3M lines.

Key orchestration patterns: RALPH (Jeffrey Huntley) — a bash script
running Claude Code in a loop using git as memory, fresh agent on context
fill. Gas Town (Steve Yagi) — maximalist multi-agent workspace. Claude
Code's native task system (late January) — each task gets its own sub-
agent with isolated 200K-token context, 7-10 running simultaneously,
automatic unblocking on completion.

Dario Amodei at Davos: Anthropic engineers "don't write code anymore —
the model writes the code." AI has entered a self-acceleration loop:
building the next AI systems using AI. This is why OpenAI is slowing
hiring — Altman says existing engineers' span with AI is so high that
new hire expectations now include doing weeks of work in 10-20 minutes.

GPD-val benchmark: GPT Thinking beat humans 38% of the time; GPT 5.2 Pro
reached 74%. On 3/4 of scoped knowledge tasks, AI output is now preferred
over human expert output.

Power user patterns: (1) Assign tasks via declarative specs, do not ask
questions. (2) Accept imperfection and iterate — RALPH embraces failure
loops. (3) Invest in specification and review, not implementation.
(4) Run multiple agents in parallel — some devs go from a few PRs/day
to dozens. (5) Let agents run overnight with guardrails. (6) Actually try
it — most people have not run agent loops beyond a few minutes.

Karpathy: model errors resemble a hasty junior developer — wrong
assumptions, failing to surface trade-offs. These are supervision
problems, not capability problems. Maggie Appleton: "When agents write
code, design becomes the bottleneck."

Speed is a foot gun: moving fast without thinking through requirements
produces mountains of useless code. Technical leaders should set explicit
policy per codebase based on risk profile.

If Amodei is right that AI handles end-to-end software engineering within
6-12 months, the gap between current practice and full automation has
never been larger. Every parallel agent multiplies productivity.
