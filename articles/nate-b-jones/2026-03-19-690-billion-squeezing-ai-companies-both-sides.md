# $690 Billion Is Squeezing AI Companies From Both Sides. Most Don't See It Coming.

**Source:** [YouTube – Nate B. Jones](https://www.youtube.com/watch?v=3FbqaD1MCUA)
**Date:** 2026-03-19
**Author:** Nate B. Jones

---

## The Perplexity Problem

On February 25th, Perplexity launched **Perplexity Computer** — a cloud-native, multi-model
orchestration system routing work across 19 frontier models. It spawns sub-agents, persists for
months, runs asynchronously, retains memory across sessions, and delivers finished artifacts while
you sleep. It runs Claude Opus 4.6 as reasoning core, Gemini for deep research, Grok for speed,
ChatGPT 5.2 for long context. Available for $200/month on the Perplexity Max tier.

It is a great product. It is also a company in a structural trap. Those two things are not
contradictory.

Perplexity is targeting $650M+ in revenue in 2026. Their search API already powers four of the
Magnificent 7 in production. They killed their ad business in February because they understood
trust is the new distribution.

And yet: their core reasoning engine runs on a direct competitor's model. Their deep research runs
on another competitor. Their speed layer runs on a third. Every model provider they depend on is
simultaneously building the exact product Perplexity Computer competes with.

---

## How January–February 2026 Redrew the Map

A compressed timeline of the events that hardened the structural picture:

- **Late January:** OpenClaw hits 100K GitHub stars (now 200K+), fastest growing repo in GitHub
  history. Cisco's security team finds a third-party skill performing data exfiltration and
  prompt injection without user awareness. People keep showing up anyway.
- **January 13:** Anthropic launches Claude Co-work in research preview ("Claude Code for the
  rest of your work").
- **February 5:** Claude Opus 4.6 ships with a 1M token context window. Within days, iShares
  expanded tech software ETF records its worst 2-day stretch since 2008. ~$250 billion wiped
  from SaaS stocks.
- **February 11:** Co-work ships on Windows. 70% of desktop computing now has access.
- **February 14:** Peter Steinberger (OpenClaw creator) officially joins OpenAI.
- **February 18:** Perplexity confirms it abandoned advertising. Trust over ad revenue.
- **February 24:** Anthropic Enterprise Agents launch with deep connectors, private plug-in
  marketplaces, pre-built templates.
- **February 25:** Samsung unveils Galaxy S26 agentic AI phone. Google previews Gemini agents
  with App Functions framework. Perplexity ships Computer. All on the same day.

In roughly six weeks, the industry stratified into layers with fundamentally different structural
economics.

---

## The Stack and Who Sits Where

Three layers emerged with clarity:

- **Bottom:** Model providers own the weights
- **Middle:** Orchestration and application layers combine models into products
- **Top:** Distribution owners control where users encounter agents

Hovering over everything: **cloud providers spending $690 billion per year on infrastructure they
must fill with tokens.** That number is not decorative. It is the force driving every structural
decision in the stack.

The problem for the middle layer is structural, not executional. When a technology stack
consolidates, the layer between platform owner and customer is the one that gets squeezed. It
happened to travel agents. It happened to media companies. It happens to enterprise middleware.
The common thread: if you don't own the layer below or the relationship above, you're borrowing
time.

---

## The Squeeze From Both Directions

**From below:** Every upstream model provider can replicate what middle-layer companies do, or
change pricing and access terms to compress margins. Reports surfaced of Anthropic banning users
who powered OpenClaw with Claude credentials. If that logic extends to orchestration layers,
Perplexity's dependency risk stops being theoretical.

**From above:** OpenAI launched **Frontier** — an enterprise platform that connects data
warehouses, CRM systems, and internal applications into a semantic layer. It onboards agents with
institutional knowledge, grants them identity and permissions, and builds evaluation loops. That
is the context layer — which was supposed to be the middleware moat. Harvey, Sierra, Decagon, and
ABridge are already committed as Frontier partners.

When the moat above and the floor below are both moving toward you, execution quality does not
save you. Perplexity Computer is extremely well executed. It does not solve the structural problem.

---

## Four Durable Positions in the Middleware Layer

Not all middleware is doomed. Four structural positions survive.

### Position 1: Know Which Context to Platform and Which to Retain

Three types of enterprise context have different defensibility:

- **Structural context** — how systems connect, where data lives, what permissions exist. This is
  commodity plumbing. Frontier's connectors handle it. If your moat is wiring Salesforce to Jira,
  expect to be eaten in 12–24 months.
- **Operational context** — how decisions actually get made, the informal knowledge in senior
  heads. Frontier approximates it. The rate of change determines defensibility: if operational
  context updates quarterly from regulatory filings, the platform keeps up. If it updates hourly
  from live physical operations, the platform cannot.
- **Proprietary context** — data and judgment that exist nowhere else. A trading desk's risk
  models. A drug company's experimental data. A manufacturer's sensor data from proprietary
  production lines. Platforming this means giving the provider what makes you *you*. Enterprise
  buyers will not do it.

Defensible middleware lives where context is either proprietary (enterprise won't hand it to the
platform) or operational and fast-changing (platform can't keep up).

### Position 2: Become Infrastructure the Agents Call

This may be Perplexity's most durable play — and it's their search API, not Computer.

Data feeds, verification services, domain-specific APIs, compliance-checking services: picks and
shovels of the agent era. The agent providers are your customers, not your competitors. Quarter's
earnings transcript API powering Perplexity Finance is the model — Quarter doesn't compete with
Perplexity, it's infrastructure Perplexity cannot function without.

### Position 3: Own the Customer Workflow Deeply

When Anthropic shipped private plug-in marketplaces, they enabled something important: an agent
that learns how a specific legal team reviews specific NDAs. Ripping it out means rebuilding all
of that institutional encoding. That switching cost is real.

Stop thinking about model selection. Think about integration depth. The question is not which
model you use. It is how many institutional workflows break if someone rips your system out.

### Position 4: Own the Trust and Verification Layer

February 2026 revealed three incompatible trust architectures deployed simultaneously:
- OpenClaw: local, no enforced security
- Perplexity Computer: cloud, curated sandboxes
- Google Gemini agents: OS-level containment

As agents proliferate, someone needs to audit what they do, verify outputs, and enforce policy.
Model providers are focused on capabilities. The gap between *agents are doing real work* and
*we can prove what agents did* is wide and growing. This is analogous to what accounting firms
did when financial complexity outpaced regulation. No one has solved it yet. It is a large
building opportunity.

---

## Three Dead Ends

**1. Fighting for which cloud runs your tokens.** It's zero sum — there are only so many tokens.
AWS securing Frontier agents means those tokens don't go to Azure or Google Cloud. Getting in
the way of that is not a viable business.

**2. Margin without differentiation.** Token volume can grow 10x and a middleware layer can still
get squeezed to zero if model providers absorb the functionality. Every one of the four durable
positions above focuses on *tokens that mean something*. Baseline orchestration doesn't.

**3. Competing for the enterprise relationship the hyperscalers are already locking in.** When
OpenAI and Anthropic deploy forward-deployed engineers alongside customers, they build the
relationship that determines AI purchasing for the next few years. A vertical startup fighting
for that conversation needs a champion who is AI-fluent and already understands why the
hyperscaler won't solve their specific problem. That's a harder sales path. There is no other way.

---

## The Hyperscalers Are Not Neutral Referees

They need to fill $690 billion per year in infrastructure. OpenAI's target of $250–280 billion in
revenue in a few years requires capturing enormous downstream token generation. This is not
optional — it is structural. None of these companies can afford to be neutral platform providers.

Vertical integration examples:
- AWS secured exclusive third-party distribution for Frontier and is co-building the stateful
  runtime environment on Bedrock
- Microsoft takes a 20% revenue share from OpenAI through 2032
- Google invested $3 billion in Anthropic while building its own agent layer into Android
- Amazon backs both OpenAI and Anthropic while building custom Trainium silicon

The 2025 framing was "cloud providers win regardless." The 2026 question is which layers generate
the most tokens and which hyperscalers can own them to justify their infrastructure buildout.

---

## The Lesson Perplexity Actually Teaches

Computer is not the way out of the middleware trap. The search API is. That got far less press.

The decision to kill advertising signals that leadership understands the structural game: they are
in the accuracy business, the high-value customer business, and the agent infrastructure business.

For everyone else: if you are not Anthropic, OpenAI, Google, Meta, AWS, or Azure, your strategic
imperative is not to compete with them directly. It is to find the position where their incentives
align with your existence rather than your replacement.

The categories where that's possible — proprietary context they can't take, infrastructure they
need, workflow depth they won't build, governance the ecosystem needs — are narrower than most
pitch decks suggest. But they are real.

The clock running on generic middleware positions is the capability jump clock. Every model
generation that collapses your differentiation narrows the window to reposition. Everybody else
is renting their space. The landlords are getting hungrier.
