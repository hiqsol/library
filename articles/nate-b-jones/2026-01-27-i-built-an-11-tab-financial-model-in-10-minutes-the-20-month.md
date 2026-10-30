---
title: I Built an 11-Tab Financial Model in 10 Minutes
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=f-v0fJgBqhk
date: 2026-01-27 15:01
tags: ai
---

# I Built an 11-Tab Financial Model in 10 Minutes

[summary](../../summary/nate-b-jones/2026-01-27-i-built-an-11-tab-financial-model-in-10-minutes-the-20-month.md)

## Claude in Excel: A Phase Change in Knowledge Work

Anthropic launched Claude as a native sidebar add-in inside Microsoft
Excel, opening it from a tight enterprise beta to anyone on the Pro
tier ($20/month). This is not an incremental improvement — it is a
phase change in what knowledge work means.

The add-in provides complete structural awareness of the workbook:
every tab, every formula, every cell reference. It can trace formula
relationships at the cell level. If you ask it to update an
assumption, it modifies cells while preserving formula dependencies.
Every action gets logged in a transparent change trail — critical for
finance models that get audited, reviewed, and handed to successors.

The underlying engine is Opus 4.5, Anthropic's most powerful model.
Complex multi-tab workbooks require a model that can hold the entire
structure in context and reason across tab dependencies. When building
an 11-tab workbook, the context window maxed out — but Opus 4.5
gracefully recovered. After clearing the chat with 6 tabs done and 5
remaining, the model examined the existing structure, inferred what
the remaining tabs should contain, and completed the build without
additional instruction beyond "pick up where you left off."

## The 11-Tab Rent vs. Buy Model

Built in 10 minutes — the time to make a cup of coffee:

- Summary dashboard with recommendation
- Input tab (adjustable by zip code)
- Opportunity cost analysis comparing down payment against S&P 500
  returns
- Sensitivity analysis (suggested by Claude, not the user)
- Tax analysis tab referencing specific input cells for itemized
  expenses
- All tabs dynamically linked — changes cascade through the model

The level of detail is sufficient to build an entire personal rent
vs. buy application using a tool like Lovable directly from this
spreadsheet.

## What Works and What Does Not

**Transformative:**
- Core capability is genuinely weeks-to-minutes fast
- 3-4 tab models build easily in single prompts
- 8+ tab models require one or two chat handoffs
- Claude searches for and populates certain data itself (housing
  prices by zip code, historical S&P returns, standard benchmarks)
- Claude suggests analyses the user did not ask for
- AI thinks at the level of the cell, formula, and sheet structure

**Still requires human input:**
- Specialized data not easily publicly available (had to manually
  paste METR benchmark data, compute training scale data)
- Charts are functional but not pretty — last-mile formatting takes
  about 5 minutes
- Complex builds max out chat context windows (workaround: start
  fresh and tell Claude to examine existing work)
- Minor column formatting issues

Norway's sovereign wealth fund estimates 213,000 hours saved using
Claude in Excel during the enterprise beta.

## The Data Partnership Strategy

Since last summer, Anthropic has been assembling licensed partnerships
with institutional data providers through the Model Context Protocol
(MCP):

- **LSEG** — live market data
- **Moody's** — credit ratings, company information across 600
  million entities
- **S&P Capital IQ** — financials
- **FactSet** and **Morningstar** — research
- **PitchBook** — private company intelligence

Any language model can help write a SUM formula. What a generic model
cannot do is pull this morning's pricing from the London Stock
Exchange, cross-reference against Moody's credit ratings, check
against S&P fundamentals, and update a comparable company analysis
— all inside the application you already use.

The strategic logic: the quality of AI outputs depends on input
quality. Anthropic may not out-train OpenAI on base model
capabilities, but they can out-connect and out-workflow them. These
data partnerships create capabilities competitors will take time to
replicate — not for technical reasons, but because replication
requires negotiating licenses with providers already committed to
someone else.

Anthropic also packaged six pre-built agent skills productizing
workflows junior analysts spend their days on: discounted cash flow
models, comparable company analysis, and similar tasks. Each
represents hours of analyst work compressed into a prompt.

## The Strange Microsoft-Anthropic Coopetition

Microsoft and Anthropic are in a $30 billion partnership where
Anthropic purchases massive Azure compute. Microsoft hosts Anthropic's
models and collects infrastructure revenue. Claude is available inside
Copilot Studio. Claude Opus powers Microsoft's researcher agent in
Microsoft 365 Copilot as an alternative to OpenAI.

Microsoft is simultaneously hosting Claude, competing against Claude
with Copilot for Excel, and collecting billions from Anthropic for
Azure — coopetition at unprecedented scale.

A telling product difference: Copilot for Excel requires files saved
to OneDrive with autosave enabled (every change commits to the
cloud). Many finance teams hate this because they want control over
when work gets saved. Claude in Excel works with local files. This
reflects Microsoft's cloud-first strategy versus Anthropic's
willingness to meet users where they are — a gap created by
Microsoft's own strategic choices that a competitor exploits from
inside Microsoft's own application.

## Four Strategic Implications

1. **Model providers and platforms are separating.** Microsoft does
   not need to win the model war — it can offer multiple models and
   let the market decide. Microsoft wins if any model provider wins,
   because Microsoft controls the distribution surface.

2. **Vertical integration is where competition happens.** Anthropic
   is not trying to beat Copilot as a general-purpose assistant.
   They are building a specialized tool better for finance by
   combining model capability with domain-specific data and
   workflows.

3. **The "one AI to rule them all" thesis keeps dying.** The future
   is multiple specialized AI systems optimized for different domains.
   Claude for finance, Copilot for quick edits, something else for
   legal work.

4. **Infrastructure providers win regardless.** Microsoft collects
   Azure revenue from Anthropic. Amazon hosts Anthropic on AWS.
   All model providers need massive compute. The AI wars may matter
   less for infrastructure returns than most investors assume.

## The Bigger Picture

The model race was Act One. Capabilities are converging. The winners
of the next phase will not be whoever trains the best model — it will
be whoever builds the most durable relationships with the industries
they serve.

There are more than a billion people on Excel. For all of them, the
tools to do weeks of analytical work in minutes are now accessible
for $20/month. The spreadsheet is where numbers become decisions.
Any AI that lives there, understands dependencies, and connects to
institutional data is no longer a chatbot — it has become
infrastructure.
