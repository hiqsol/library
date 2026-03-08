# Summary: GPT-5.4 Let Mickey Mouse Into a Production Database

- **Source:** [YouTube — Nate B Jones](https://www.youtube.com/watch?v=-_vL1KXd2rc)
- **Author:** Nate B Jones
- **Published:** 2026-03-07 17:00

---

Nate ran blind evaluations of GPT-5.4 against Claude Opus 4.6 and Gemini 3.1
with six structured tests and independent judging. GPT-5.4 is "the most
interesting model" — not best, not worst — because it swings wildly between
categories.

**Where GPT-5.4 wins:**
- Quantitative modeling — produced 6-tab workbook with Pythagorean win
  expectation, ELO system, Poisson binomial distribution vs Opus's simpler
  3-tab Bradley-Terry model
- File processing — 99.1% coverage (461/465 files) in a brutal schema migration
  eval vs Claude's 75% (failed to install OpenPyXL). Box independently confirmed
  GPT-5.4's document processing lead
- Competitive self-knowledge — ~90% accuracy on its own capabilities, best of
  any model
- Self-critique — wrote self-assessment more honest than most consulting
  deliverables

**Where GPT-5.4 loses:**
- Writing quality — tin ear for tone, lost to Opus on both creative and business
  writing
- Product judgment — got a two-sided product problem wrong that Opus got right
- Data hygiene — let Mickey Mouse and a $25K test order into production database,
  278 customers vs 176 correct (Claude: 194), 13 status values vs 4-5 needed
  (Claude: 6)
- Speed — 56 minutes on schema migration vs Claude's 15, Gemini's 21

**Critical finding:** The thinking mode vs auto mode gap is massive. In thinking
mode, GPT-5.4 competed for first on epistemic calibration (exact Higgs Boson
mass, correct Apple stock price). In auto mode, it named 2024 Nobel laureates
for a 2025 question and dropped to dead last. Same model, same questions.

**Core pattern:** GPT-5.4 treats tasks as pipelines to execute, not problems to
understand. Builds beautiful infrastructure, fails to notice if output makes
sense.

**Strategic direction:** Release notes use "agent" most often, not
"intelligence" or "reasoning." GPT-5.4 is infrastructure for agentic systems —
tool search, computer use, long-running tasks. Folding Codex coding abilities
into mainline model. OpenAI committed to monthly shipping cadence. Peter
Steinberger hire points toward enterprise-grade OpenClaw. Pricing assumes
agents running for hours, not humans typing queries.
