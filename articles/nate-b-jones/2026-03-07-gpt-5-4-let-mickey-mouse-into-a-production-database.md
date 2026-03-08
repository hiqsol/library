# GPT-5.4 Let Mickey Mouse Into a Production Database — Nobody Noticed

- **Source:** [YouTube — Nate B Jones / AI News & Strategy
  Daily](https://www.youtube.com/watch?v=-_vL1KXd2rc)
- **Author:** Nate B Jones
- **Published:** 2026-03-07 17:00

---

## The Carwash Test

Nate asked ChatGPT 5.4 in thinking mode: "I need to wash my car. The carwash is
100 meters away. Should I walk or drive?" GPT-5.4 thought about it and said walk,
then gave a long explanation, mentioning at the very end that "maybe you'll need to
reposition the car." Claude Opus 4.6 wrote one sentence: "Drive. You need the car
at the carwash." Gemini 3.1 Pro also got it right and noted it was a trick question.

Every frontier model got this right except GPT-5.4 thinking — the model OpenAI
positioned as its most capable system for professional work wrote a careful,
well-structured, completely wrong answer to a question a child would get right.

## Blind Evaluation Methodology

Nate ran GPT-5.4 through a blind eval suite against Claude Opus 4.6 and Gemini 3.1.
Six structured evaluations with independent judging — outputs labeled by number so
the judge never knew which model produced what. A separate AI-fluent reviewer
verified results. Models were also tested on real tasks: the kind of work you'd hand
to a model on a Tuesday afternoon and expect to use on Thursday morning.

**TLDR:** GPT-5.4 is not the best model, not the worst — by far the most
interesting. Interesting for reasons that have almost nothing to do with benchmarks.

## Scorecard: Where GPT-5.4 Loses

### Writing Quality

GPT-5.4 is a big upgrade from 5.2 at writing — much better. But it has a tin ear
for tone. On both creative and business writing evaluations, Opus 4.6 won. When
given a challenging author to mimic (Shakespeare, PG Wodehouse), GPT-5.4 produced
poor results. On business writing, it could not clearly summarize and articulate
thinking as well as Opus 4.6.

### Verbal Creativity

Nate gave models a JP Morgan deck (the most boring financial deck imaginable) and
asked them to find the funniest phrase, identify a pun, and rewrite it emphasizing
the pun. Opus 4.6 delivered a triple-layered pun dissected across three semantic
layers. GPT-5.4 found a real pun, explained it correctly, and delivered a competent
rewrite — it did not fail. Gemini fabricated the source, the title, and the URL
twice.

### Product Judgment

Nate gave Opus 4.6 and GPT-5.4 the same gnarly two-sided product problem with a
non-obvious correct answer. GPT-5.4 got it wrong — very logically, but wrong. Opus
4.6 got it right. Nate believes good writing skills are closely linked to product
management skills, and being able to write well helps make good product decisions.

### The Pipeline Problem: Infrastructure Without Judgment

GPT-5.4 builds infrastructure without judgment — the carwash problem at scale. It
constructs elaborate, well-engineered systems and then fails to notice whether the
output makes sense. Examples from the "eval from hell":

- Let a fake customer named Mickey Mouse through to production database
- Let a $25,000 carwash order from "test customer" through
- Produced 394 flagged items in a flat list with zero categorization, zero priority,
  zero filtering — technically fulfilled but not actionable by a human (Claude
  produced 19 actionable flags)
- Found 278 customers when correct number after deduplication was 176 (Claude had
  194 — still too many but much closer)
- Created 13 business status values when the business needed 4-5 (Claude normalized
  to 6)

**Pattern:** GPT-5.4 treats tasks as pipelines to execute, not problems to
understand. It will build a beautiful complete system and pull in data, but will not
stop to ask why.

## Scorecard: Where GPT-5.4 Wins

### Quantitative Modeling

Given the prompt to build a spreadsheet projecting the Seattle Seahawks 2026 season
win probabilities, GPT-5.4 produced a six-tab workbook with Pythagorean win
expectation, ELO-like rating system with offseason retention decay, Poisson binomial
season distribution, and a methodology tab that honestly cataloged its own
assumptions, shortcuts, and limitations. Opus 4.6 produced a cleaner, better-
formatted three-tab workbook using a simple Bradley-Terry model — more readable but
not as rigorous.

GPT-5.4 also wrote a self-critique of its own work more honest than most consulting
deliverables, identifying exactly where it oversimplified and what it could improve.

### File Processing

In the "eval from hell" (schema migration from a shoebox of business data — hand-
written receipts, multiple database schemas, different hashes, a complete mess),
GPT-5.4 discovered and processed 461 out of 465 files — 99.1% coverage. It handled
CSVs, Excel, JSON, PDFs, VCF contacts, handwritten receipt images via OCR, corrupted
JSON backups, and a monster multi-tab spreadsheet.

Claude discovered all the files but could not parse Excel because it chose not to
install OpenPyXL (a 3-second pip install) — a judgment failure by Opus 4.6. GPT-5.4
had OpenPyXL pre-installed as part of OpenAI's tool philosophy.

Box also independently published scores on document processing finding a clear lead
for GPT-5.4.

### Competitive Self-Knowledge

GPT-5.4 gets roughly 90% correct knowledge about itself — best coverage of its own
capabilities on text, coding, media, and open-weight models. It understands the
landscape of AI and what models have what capabilities in ways no other model does.

## The Thinking Mode Toggle

The single most important finding: the chasm between GPT-5.4's thinking mode and
auto mode.

**Epistemic calibration test:** In thinking mode, GPT-5.4 competed for first place —
nailed the exact Higgs Boson mass, retrieved the correct Apple closing price, got the
current matrix multiplication exponent correct. In auto mode, it named 2024 Nobel
laureates for a 2025 question, cited a matrix multiplication bound from 2020, and
dropped from first place to dead last.

Same model, same questions, dramatically different results. Not everybody will click
thinking mode. The auto switcher should accurately invoke thinking where thinking
tasks are needed — Nate did not see that happening enough.

## Speed Trade-Off

On the eval from hell, GPT-5.4 took 56 minutes to complete. Claude finished in 15,
Gemini in 21. But GPT-5.4 produced a 4,000+ line migration script, an 11,000+ line
migration report, and 30 database tables. Claude produced 1,800 lines of code, a
concise report, and 13 tables. GPT-5.4's time was spent well — output was much more
exhaustive; Claude's was more usable but less complete.

PowerPoint capability: GPT-5.4 is much better than 5.2 at building PowerPoints — on
par with Sonnet 4.6, with Opus 4.6 having a slight edge.

## The Peter Steinberger Connection and OpenAI's Direction

Peter Steinberger was hired just weeks before this release. This is the first major
model drop since OpenClaw. OpenClaw got started with Peter using Codex to build
OpenClaw, with most GitHub users preferring Claude for their open-source work.
Peter was hired to build at OpenAI a secure, stable, big-company version of
OpenClaw.

GPT-5.4 is not that, but it has big flashing neon arrows pointing in that direction:

- Computer use capabilities — think OpenClaw
- Long-running task performance — think OpenClaw
- Tool search — agentic architectural innovation
- Reasoning effort controls for agentic system builders

The word that appears most often in the release notes is not "intelligence" or
"reasoning" — it's "agent." The model is positioned as infrastructure for agentic
systems that operate software, manage tools, sustain workflows across hours, and
coordinate with external services.

GPT-5.4 is folding 5.3 Codex's coding abilities into the mainline model — similar
to what Claude did when it brought Claude Code into CoWork, but with a ChatGPT
approach.

## Pricing Signal

The pricing increase makes sense if you assume agents will run for hours consuming
tokens continuously, not humans typing one question at a time.

## Recommendations

1. **Test in thinking mode, not auto.** The default version most users encounter is
   measurably weaker on factual accuracy, retrieval, and useful work.
2. **Agentic system builders:** GPT-5.4's tool search and computer use are genuinely
   useful. Progressive tool discovery at runtime (vs loading all definitions up
   front) changes cost structure for massive tool ecosystems.
3. **Writing-dependent work:** Opus-class models still produce much better writing.
4. **Spreadsheets and quantitative modeling:** GPT-5.4 is a step forward for hard
   math, not for formatting.
5. **Speed-sensitive work:** Use Gemini or Opus — both are much faster with frontier
   performance.
6. **Deep Claude ecosystem users:** Switching cost is too high unless you have
   problem types requiring extraordinary completeness on very difficult tasks.

## Strategic Takeaway

Models are converging on capability but diverging on philosophy. Features like
progressive tool discovery are more compelling for meaningful work at scale than
benchmark scores. OpenAI is shipping a model optimized to be the substrate that AI
agents run on — and they've committed to monthly shipping cadence (5.5 likely next
month). Both OpenAI and Anthropic are publishing more engineering detail — read the
engineer blog posts, not the press releases.
