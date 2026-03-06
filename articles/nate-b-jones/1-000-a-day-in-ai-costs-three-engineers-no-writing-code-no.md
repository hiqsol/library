# $1,000 a Day in AI Costs, Three Engineers, No Writing Code, No Code Review

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=-bQcWs1Z9a0)
- **Author:** Nate B Jones
- **Date:** 2026-02-20 15:00

---

## The Token Is the New Unit of Work

OpenAI is rumored to be working on a $20,000/month AI employee. But
the real story is that across Anthropic, OpenAI, and other AI-native
organizations, the new unit of work is the token.

For 60 years, the unit of work in software was the instruction —
deterministic, human-written code executed by a machine. That era is
done. A token is not an instruction; it is a unit of purchased
intelligence. You describe what you want, feed it context, and buy
enough intelligence to get a result.

The human's job is shifting up: from writing the logic to specifying
the outcome and managing the intelligence budget that produces it.

## The Numbers Anchoring the New Paradigm

- **StrongDM** CTO Justin McCarthy: three-person team targets
  **$1,000/day** in token spend. No handwritten code.
- **Cursor** (Anthropic's single largest customer): AWS costs spiked
  from **$6M to $12M** between May and June 2025
- **Anthropic** itself spent **$2.66 billion** on AWS through September
  2025 against ~$2.55B in cumulative revenue — more than 100% of
  topline to AWS alone
- **Perplexity** spent **164%** of its entire 2024 revenue across AWS,
  Anthropic, and OpenAI combined

These companies are not finding expensive ways to do things. They are
operating a fundamentally different paradigm.

## The Price Curve and Jevons' Paradox

Per-token inference costs have been falling at rates that make Moore's
Law look gentle — **10x to 200x per year** depending on benchmark.
GPT-4 equivalent performance cost $20/million tokens in late 2022;
roughly $0.40 today. Claude 4.5 Sonnet runs at $3/million input tokens.

When a resource gets cheaper, you use enormously more of it (Jevons'
Paradox). Steam engines got more efficient and coal consumption
exploded. Cloud computing got cheaper and AWS bills went up.

Satya Nadella invoked Jevons' Paradox by name after the DeepSeek
moment: "As AI gets more efficient and accessible, we will see its
use skyrocket."

## Enterprise Spending

- Average organization: **$85,000/month** on AI, up 36% year-over-year
- Share planning to spend over $100K monthly: doubled from 20% to 45%
- A16Z enterprise survey: average enterprise LLM spend hit **$7M** in
  2025 (up from $4.5M), projections of **$11M+** in 2026
- Spending has shifted from innovation budgets to centralized IT and
  business unit budgets — "let's explore" to "this is critical"

OpenAI reportedly plans multiple agent pricing tiers:
- $2,000/month for knowledge worker agents
- $10,000/month for specialized agents (coding/software)
- $20,000/month for AI research agents

Enterprise buyers are doing the math and concluding that even at
$20,000/month, the price is cheap relative to human professionals.

## Token Management as Core Competency

The scarce resource has changed. The bottleneck is no longer developer
time — it is the ability to convert tokens into usable economic value.

What is scarce: knowing how to aim tokens, structure context, route
tasks to the right model at the right cost, build agent loops that
sustain quality, and measure whether purchased intelligence produces
needed outcomes.

Enterprises are building internal platforms that route work to the
right model at the right price: Haiku for cheap stuff, Opus for hard
stuff, Sonnet for the middle.

**Cursor's cautionary tale:** Cursor sends essentially all its revenue
to Anthropic in API costs. When Anthropic raised caching prices,
Cursor's costs exploded overnight, forcing them to gut the unlimited
$20/month plan and introduce a $200/month tier. Users revolted. Part
of Cursor's response: build their own model.

Token economics is now a core business competency. Companies one
supplier pricing change away from crisis.

## Three Developer Career Tracks

The standard "AI replaces developers or doesn't" framing is not
helpful. What is actually happening is rapid differentiation into
three tracks:

### Track 1: The Orchestrator

Does not write code. Specifies outcomes and manages the intelligence
that produces them. Core skills: system design, specification writing,
quality evaluation, token economics. Think factory managers for
intelligence. Compensation correlates with token budgets, not lines
of code.

### Track 2: The Systems Builder

Builds infrastructure orchestrators use — agent frameworks, evaluation
pipelines, context management systems, routing layers. Deep technical
work closer to systems engineering. Smaller in volume, much higher
compensation ceiling. Leverage is company-wide.

### Track 3: The Domain Translator

Combines enough technical fluency to work with AI systems and enough
deep domain expertise to know which problems are worth solving. The
dental practice management specialist is now a developer. The
construction scheduling expert is now a developer, though they may
not know it yet.

Value goes up as intelligence gets cheaper — more niche problems
become economically viable.

**Most exposed:** the middle of the old distribution — developers
who write competent application code but lack deep systems or domain
expertise. Generic code production is going to zero at the same rate
as the cost of tokens.

## Organizational Restructuring

Organizations structured around headcount are being rebuilt around
intelligence throughput. An org with 500 engineers writing code by
hand may produce less than one with 50 engineers managing agents —
given better specs, evaluation frameworks, context engineering, and
higher token budgets per engineer.

**AI-native companies** run at **3-5x** revenue per employee vs.
traditional SaaS. A $10M ARR AI startup might operate with 15 people;
a traditional SaaS company would need 55-70.

**Klarna** had a disastrous initial AI rollout (had to rehire customer
service staff), but still sees revenue scaling per employee into seven
figures — far above average SaaS.

## The Solopreneur Opportunity

When intelligence is purchasable by the token and building costs keep
falling, the minimum viable team for software approaches one.

Going independent is less of a lifestyle trade-off and increasingly a
rational economic choice for anyone with deep domain knowledge and
sufficient AI fluency.

Silicon Valley bet: the first one-person billion-dollar company
happening in 2026. More interesting than the headline: the downward
pressure on team size everywhere. "Two pizza teams" are becoming
half-pizza teams.

## The Market Split

The market is splitting along generalized scale vs. specialized
precision:

| Axis | Top | Rest of Market |
|------|-----|----------------|
| **Who** | Enterprises, funded AI-native cos | Small builders, startups |
| **How** | Token volume, horizontal platforms | Specificity, niche markets |
| **Moat** | Capital and infrastructure | Distribution and trust |
| **Compounds with** | Model upgrades | Domain knowledge |

The startup playbook: know a market so well that a $200/month Claude
Max subscription aimed precisely creates more value than a $20,000/month
enterprise agent budget pointed at the wrong problem.

Both strategies are more leveraged than the old model where everything
was denominated in time and handwritten code.
