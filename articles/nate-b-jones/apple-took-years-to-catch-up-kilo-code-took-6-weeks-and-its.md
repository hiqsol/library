# Apple Took Years to Catch Up, Kilo Code Took 6 Weeks

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=2sY7Pcm2j2g)
- **Author:** Nate B Jones
- **Date:** ~January 2026

---

## xAI Closes $20 Billion Series E

xAI announced its upsized Series E round at an implied valuation of
$230 billion — in the same bracket as OpenAI and Anthropic. Capital
is earmarked for continued expansion of the Colossus supercomputers
in Memphis, Tennessee. The company ended 2025 with over 1 million
H100 GPU equivalents across Colossus 1 and 2. Grok 5 is currently
in training.

xAI claims roughly 600 million monthly active users across X and
Grok apps, making it the largest consumer-facing AI deployment
outside of Google and OpenAI.

The raise coincided with a safety crisis: Grok generated
inappropriate deepfakes of real people including minors, triggering
regulatory probes in the EU, UK, India, Malaysia, and France.
Despite this, xAI landed a Department of Defense deal — Grok is now
the DoD's AI agents platform and also powers prediction markets
Polymarket and Kalshi.

Three labs now have clear runway to survive the multi-year scaling
race: OpenAI, Anthropic, and xAI. Google is effectively the fourth
due to search revenue funding AI as a side bet. Everyone else
operates against shorter timelines.

The Grok safety failures are instructive: xAI closed its largest
round while facing active investigations in five countries. Investors
have a very long-term perspective and are willing to look past
initial issues, assuming AI products will mature over time.

## Amodei and Hassabis at Davos: The Day After AGI

Dario Amodei (Anthropic) and Demis Hassabis (Google DeepMind) sat on
the same stage and agreed AGI is coming faster than anyone outside
the major labs realizes.

**Amodei's position (more aggressive):**
- AGI will emerge in 2026 or 2027
- Driven by accelerating feedback loop of AI writing its own code
- Anthropic engineers rarely write code by hand anymore — AI does it,
  humans review
- Significant risk to entry-level professional positions

**Hassabis's position (more conservative):**
- 50% probability of AGI by end of the decade
- Jobs are not particularly easy to automate — if you get 95% of a
  job's skills, you increase the value of the 5% that remain human
- Three areas where current AI falls short: memory, continuous
  learning, and long-term reasoning
- Current models have a memory wall, do not learn after release, and
  long-term reasoning is not where it should be

The Hassabis view appears more consistent with current evidence:
AI has profound impact but the human remainder is essential and ends
up supercharging the humans who provide it. Despite predictions of
massive employment disruption, aggregate layoff data across the
economy does not clearly show AI-driven impact.

## Apple Admits Defeat on Foundation Models

Apple and Google announced a multi-year collaboration where next-
generation Apple foundation models will be based on Google's Gemini
models and cloud technology.

Key details:
- Deal reportedly costs Apple $1 billion per year
- Google is building a custom 1.2 trillion parameter Gemini model
  specifically for Apple
- Far beyond what Apple's own models can currently achieve

This is a significant loss for OpenAI. ChatGPT has gone from being a
potential OS on the phone to secondary tier, with Gemini becoming the
default AI layer on both Android and iOS. This puts more pressure on
Sam Altman and Jony Ive to deliver a third device giving OpenAI
distribution.

## DeepSeek Publishes Engram

On January 12th, DeepSeek released a paper introducing Engram, a
conditional memory architecture. The key insight: transformers lack
native knowledge lookup ability. Tasks that should be solved
quickly — like recognizing "Diana, Princess of Wales" — instead
require multiple layers of attention to progressively compose
features. Models spend expensive reasoning tokens on what should be
simple lookups.

Engram takes short sequences (2-3 tokens) and uses hash functions to
look them up in a massive embedding table, filtering retrieved
patterns against current context via a gating mechanism. This yields
substantial performance jumps without spending many tokens — an
extremely token-efficient way to retrieve information with potential
to give models factual memory.

## Kilo Code Launches App Builder

Founded by GitLab co-founder Sid Sijbrandij and CEO Scott, Kilo Code
launched its app builder after a six-week sprint. The company raised
$8 million in seed funding.

Kilo's positioning targets actual engineers rather than non-technical
users — distinguishing itself from Lovable. Following the GitLab
playbook: ship in open source, compete on breadth, deliver a
comprehensive platform rather than point solutions.

Notable speed: five engineers shipped the first internal demo in 3
days. Six weeks later it launched publicly. Their public roadmap
(which would be 12-18 months at most companies) reportedly represents
just 5 more weeks of work.

The vibe coding market is maturing from "AI can write code" to "which
differentiated tool fits my workflow." The question is whether there
is room for a fourth player between Lovable, Cursor, Claude Code,
and Codex. One of the most powerful AI use cases in 2026 is giving
engineers more tools to scale how they build.
