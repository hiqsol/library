# Dario Amodei Made One Mistake, Sam Altman Got $110 Billion

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=pTtueIqrg0Q)
- **Author:** Nate B Jones
- **Date:** ~March 2026

---

## The Week That Reshaped AI Power Dynamics

On a Friday night, while Anthropic CEO Dario Amodei was still drafting his
principled stand against the Pentagon, Sam Altman announced on X that OpenAI
had signed a deal to deploy models in the classified networks of the Department
of Defense. Hours later, the United States and Israel began bombing Iran. By
Saturday morning, Claude was the number one app in the app store and Anthropic
was designated a supply chain risk to national security — an action never before
taken against an American company.

These events are connected by a logic most commentary has missed.

## Iran and AI in Modern Combat

The Wall Street Journal reported that US Central Command used Claude for
intelligence assessments, target identification, and combat simulations during
the strikes against Iran — hours after the president ordered all federal
agencies to stop using Anthropic technology. The model was simply too deeply
embedded in operational workflows to rip out in real time, even after a
presidential order.

This was not new. Claude had been used in the January operation to capture
Nicolas Maduro in Venezuela, deployed through Anthropic's partnership with
Palantir on Amazon's top-secret cloud. The Pentagon had awarded contracts
worth up to $200 million through the Chief Digital and AI Office for frontier
AI prototyping. The classified deployment was running almost exclusively on
Claude deployed with Palantir.

AI models are no longer supplemental to intelligence operations. They compress
the observe-orient-decide-act loop so that real-time reactions are feasible
where they previously took days of analyst work.

## What Amodei Actually Said

In his February 26th statement, Amodei wrote that he "believes deeply in the
existential importance of using artificial intelligence to defend the United
States." He said Anthropic supports 98-99% of Pentagon use cases and that
partially autonomous weapons are "vital to the defense of democracy." Then he
said something deeply significant:

> "Even fully autonomous weapons may prove critical for our national defense."

Amodei's objection is not moral — it is technical. He is saying the models
are not reliable enough yet. His positions on autonomous weapons are contingent
and time-limited, a function of model capability (which is accelerating
rapidly), not necessarily ethics.

Anthropic's demand for human-in-the-loop oversight was already codified in
DoD Directive 3000.09. Anthropic was asking for what the law already provides.
The Pentagon likely refused to write it into the contract because doing so
would give Anthropic a legal basis to object to specific deployments.

Defense Secretary Pete Hegseth gave Anthropic a deadline: allow unrestricted
use for any lawful military purpose, or be designated a supply chain risk.
Anthropic refused. Hegseth designated the company and announced a six-month
phase-out.

## How Altman Played the Same Table

OpenAI's deal was announced Friday night, hours after Anthropic's designation.
Altman admitted the deal was "definitely rushed" and the optics didn't look
good. But the substance matters.

OpenAI's agreement includes three stated red lines: no mass domestic
surveillance, no autonomous weapons, no high-stakes automated decisions like
social credit systems — nearly identical to what Amodei was asking for.

The difference is implementation. OpenAI's cloud-only deployment architecture
with embedded engineers physically prevents integration into weapons hardware.
Staff were told the government agreed to let OpenAI build its own safety stack.

Amodei chose to go public when wrestling with the department. Altman went
private. The defense establishment rewards deference and punishes public
defiance. Whether Amodei was right on the substance is a different question
from whether he played the game well. In terms of game theory, he lost.

## The $110 Billion Round

On the same day as the Pentagon deal, OpenAI announced the largest private
financing in history — $110 billion — valuing OpenAI at $730 billion pre-money,
$840 billion post-money. For context, total US venture capital investment
across every startup in 2023 was $170 billion. OpenAI raised 65% of that in
a single transaction.

### Investors

| Investor  | Amount     | Notes                                           |
|-----------|------------|-------------------------------------------------|
| Amazon    | $50B       | $15B unconditional; $35B contingent on IPO/AGI  |
| Nvidia    | $30B       | Paired with Vera Rubin architecture deployment  |
| SoftBank  | $30B       | Total OpenAI investment now $64.6B              |
| Microsoft | Did not participate | Traded exclusivity for 20% revenue share through 2032 |

Amazon's layered logic: equity guarantees a cloud contract, the cloud contract
locks in Trainium chip consumption, chip consumption funds Amazon's long-term
silicon ecosystem. AWS becomes exclusive third-party distributor for OpenAI
Frontier (enterprise agent platform). They are co-developing a stateful
runtime environment on Bedrock.

Microsoft renegotiated in late 2025, removing its right of first refusal on
new cloud workloads but securing a 20% revenue share through 2032. Microsoft
essentially traded exclusivity for a long-term tax on OpenAI's growth.

### Circular Financing

Bloomberg mapped the structure: Nvidia invests in OpenAI, which buys Nvidia
chips (booked as revenue). Amazon invests in OpenAI, which consumes AWS
(booked as cloud revenue). SoftBank invests in OpenAI, which deploys on
Stargate infrastructure SoftBank co-owns. Whether this is a flywheel or a
house of cards depends on whether end-user demand materializes at scale.

## Infrastructure: Stargate and Beyond

Stargate (joint venture with SoftBank, Oracle, Abu Dhabi's MGX) targets
$500 billion in AI infrastructure and 10 GW capacity by 2029. Phase 1
delivered 200+ MW in September 2025; Phase 2 targets ~1 GW by mid-2026.

Total committed compute across all architectures: roughly 26 GW across
Nvidia, AMD, and custom Broadcom silicon — the electricity consumption of
a mid-sized country.

Cloud commitments: $250B to Microsoft Azure through 2032, $38B to AWS,
~$300B to Oracle. Combined: nearly $700 billion.

Against this spending, OpenAI's annualized revenue topped $20 billion by
late 2025. Projections: $100B by 2029, $280B by 2030. Losses projected at
$14 billion this year, cumulative $44 billion, profitability not until 2029.
An IPO approaching $1 trillion is planned to close the funding gap.

## Anthropic's Position Is Stronger Than It Looks

Despite the supply chain risk designation:

- Amazon invested $8B in Anthropic (alongside $50B in OpenAI)
- Anthropic's $14B annualized revenue with 10x year-over-year growth
- November 2025 deal with Microsoft and Nvidia brought $15B, pushed
  valuation to $350B
- Claude available on all three major clouds — the only frontier model
  with that distribution breadth
- $30B Azure compute commitment for Nvidia Grace Blackwell and Vera Rubin

But enterprise contracts — the recurring revenue justifying the valuation —
are most directly threatened by the designation. Unlike OpenAI, which now
has a defense contract anchoring a broader government procurement pipeline,
Anthropic's government business is being unwound.

## The Enterprise Battle That Actually Matters

Everyone is incentivized to get massive AI workloads into enterprises.
Agents are wonderful for token consumption — they 100x or 1000x what a
human can type. The fight will be won or lost on sticky long-term enterprise
contracts.

Cloud providers are playing every side: AWS backs Anthropic and OpenAI;
Google backs Anthropic and has its own model and defense contracts; Microsoft
backs everyone (or doesn't). They are allies of token volume, not allies of
any single model provider.

Key considerations for enterprise leaders:

- The stateful runtime creates lock-in that simple model swaps cannot undo
- Government contracts are becoming the most durable revenue in technology
- The circular financing structure centralizes risk — if revenue
  disappoints, the capital structure strains immediately
- The model layer is commoditizing over a 3-4 year horizon
- The infrastructure layer is consolidating at a breathtaking rate
- The regulatory layer is being shaped by defense contracts, not legislation

## The Provocative Question

The conventional fear is: what if revenue disappoints? But given agent
workloads consuming tokens at 100-1000x human rates, the risk may be on the
other side. Is there a possibility that even the biggest capital expenditure
in human history is underbuilt?

Amodei stood on principle and got designated a national security risk. Altman
played a quiet game and got the keys to the kingdom. Amazon placed chips on
every number. The Pentagon proved that AI models are now so embedded in
American war fighting that even a presidential order cannot remove them.

The numbers are a bet that AI compute will become as fundamental to
civilization as electricity. OpenAI is betting it can own the grid.
