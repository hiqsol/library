# Prompting Just Split Into 4 Skills — Summary

**Date:** 2026-02-27 15:00

Models have stopped being chat partners and started being workers running
for days/weeks. Opus 4.6, Gemini 3.1 Pro, GPT-5.3 Codex all shipped
autonomous agent capabilities. Longest Claude Code sessions doubled between
Oct-Jan 2025, then doubled again. Telus: 13,000 custom AI solutions.
Zapier: 800+ internal agents.

**The 10x gap:** Same model, same Tuesday. Person A (2025 skills) gets 80%
right, spends 40 min cleaning up. Person B (2026 skills) writes an 11-min
structured spec, hands off, makes coffee, comes back to a finished deck.
Does 5 more before lunch. A week's work in a morning.

**Toby Lutke** runs structured evals on every model release. His insight:
context engineering = stating a problem so completely the task is solvable
without additional info. It made him a better CEO communicator. His
provocative take: corporate politics is bad context engineering for humans.

**The four disciplines (cumulative, not interchangeable):**

1. **Prompt Craft** — Original skill. Synchronous, session-based. Clear
   instructions, examples, guardrails, output format. Now table stakes.
   The 1998 equivalent of sending email.

2. **Context Engineering** — Curating the entire token environment. System
   prompts, tools, docs, memory, MCP. Your 200-token prompt = 0.02% of
   what the model sees. 10x practitioners build 10x better context
   infrastructure, not 10x better prompts.

3. **Intent Engineering** — What agents should want. Goals, values, trade-
   off hierarchies, decision boundaries encoded as infrastructure. Klarna:
   2.3M conversations resolved but optimized for speed not satisfaction.
   Had to rehire humans. Intent sits above context like strategy above
   tactics.

4. **Specification Engineering** — Documents autonomous agents execute
   against over extended time horizons. Entire organizational corpus as
   agent-readable specs. Anthropic's fix for Opus 4.5 failures: not a
   better model but spec engineering (laser agent + progress log +
   incremental coding sessions).

**Five primitives to learn:**
1. Self-contained problem statements (no unstated assumptions)
2. Acceptance criteria (3 sentences an observer can verify)
3. Constraint architecture (musts, must-nots, preferences, escalation)
4. Decomposition (<2hr sub-tasks with clear I/O boundaries)
5. Evaluation design (3-5 test cases with known-good outputs per task)

**Key insight:** Specification done right is what clear thinking has always
looked like, made explicit because machines don't let us be lazy. AI is
enforcing communication discipline the best leaders practiced intuitively.
One-person businesses have the greatest current advantage — just convert
Notion to be agent-readable.
