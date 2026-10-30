---
title: Stop Accepting AI Output That "Looks Right"
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=-FhtPUkXKO4
date: 2026-03-10 00:00
tags: ai
---

# Stop Accepting AI Output That "Looks Right"

[summary](../../summary/nate-b-jones/2026-03-10-stop-accepting-ai-output-looks-right.md)

**Abbreviations:**
- **AI** — Artificial Intelligence
- **GDP-val** — General Domain Professional Validation (benchmark)
- **MCP** — Model Context Protocol
- **PRD** — Product Requirements Document
- **SaaS** — Software as a Service

---

## The Most Valuable AI Skill Is Saying No

The most valuable AI skill is not prompting, workflow design, or model
selection. It is rejection — the ability to look at AI output and say "this
is wrong, and this is why." Skilled AI practitioners reject far more output
than they accept: wrong framing, sloppy reasoning, confident-sounding
analysis that would not survive contact with anyone who actually understands
the domain. Even with excellent prompts, domain experts with high taste
standards still say no constantly.

Learning to say no is the missing skill in the "judgment and taste" category
that the industry keeps gesturing at. Every skilled rejection creates
institutional knowledge that did not exist before. Those rejections can
compound into durable constraints — if anyone bothers to capture them.
Almost nobody does.

## Your Rejections Are More Worth Than Your Prompts

When someone rejects AI output, three things happen simultaneously. The
person applies domain expertise the AI does not have. They identify a
specific gap between "this looks right" and "this is actually correct." And
they articulate a constraint that was not an explicit rule before.

Examples across knowledge work:

- A **strategy partner** sends back an AI-generated competitive analysis:
  "Where is our proprietary insight on customer switching costs? Any firm
  with access to the same model could have produced this framing."
- A **loan officer** rejects a covenant tracking prototype: "You cannot
  treat a debt service coverage ratio the same as a minimum net worth
  requirement — those have completely different monitoring triggers."
- An **editor** kills a draft: "The thesis is buried in paragraph four.
  Lead with provocation."

These rejections are not null events. They are knowledge creation events.
But for almost everybody, the knowledge evaporates — it lives in an email
thread, a chat window, a Slack message. Nobody captures it. Nobody compounds
it. The same rejection happens again tomorrow.

## Generation Is Solved — Verification Is the Bottleneck

Most AI skill markets focus on generation: prompting, workflow design, tool
selection, multimodel orchestration. All aimed at producing more and
producing faster. But production has been solved.

OpenAI's GDP-val — the most rigorous measurement against actual knowledge
work — shows frontier models beating or tying professionals with an average
of 14 years of experience 70% of the time on head-to-head comparisons. The
models do it 100 times faster for less than 1% of the cost. Tasks are
created by those professionals, graded by those professionals in a
double-blind manner. The models still win most comparisons.

The interesting reading is not about AI capability or workforce demise. If AI
matches your best people's output 70% of the time on well-specified tasks,
what determines the other 30%? What happens to the 70% that looks right on
the surface but fails in production? The answer in both cases: someone has
to look at the output and know. And knowing means saying no — a lot.

## Three Dimensions of Rejection as a Competency

### Recognition

The ability to detect that something is wrong. This depends on domain
experience and is hard to shortcut. Junior analysts will not catch flawed
regulatory assumptions without the deep experience senior analysts have.
Loan officers will not spot covenant logic errors without having seen enough
deals.

Recognition is the product of years of practice and the reason experienced
domain experts are becoming more valuable, not less, as AI floods
organizations with output. The person who has reviewed 2,000 deals and can
feel when something is off is becoming the most important person in the
building — not despite AI, but because of it.

Inside the boundary of expertise, AI is a force multiplier: a domain expert
with strong recognition and AI tools can evaluate 10 times the output they
could before. Outside that boundary, AI multiplies confidence, not
expertise — and that is worse.

### Articulation

The ability to explain why something is wrong in a way that produces a
usable constraint. "This isn't right" is just a rejection. "This isn't
right because you're treating all requirements identically, and the PRD
needs to be structured this way" — that is a constraint.

Articulation is the difference between taste that stays in someone's head
and taste that can be encoded, shared with a team, and applied at scale.
It is a learnable skill, but almost nobody teaches it.

GDP-val's methodology illustrates why this matters. Every task went through
five rounds of expert review. Each review contained a rejection event — an
expert saying "this is not representative enough" or "this isn't clear
enough for evaluation." That iterative refinement through rejection made
the benchmark useful. The expert taste did not just evaluate the AI — it
built the evaluation infrastructure.

### Encoding

The practice of making constraints persist beyond the moment of rejection.
This is where everything breaks down. Someone articulates a constraint, it
lives in an email, and next quarter a different team makes the same mistake
because the constraint was never captured anywhere durable. The reasoning
has to be recreated from scratch.

Andrej Karpathy's framework — that AI systems improve fastest where success
can be verified — has direct implications. Verification infrastructure does
not magically emerge. It is built from encoded rejections: test suites with
acceptance criteria, quality gates, business rules. These are outputs of
people looking at work and saying no with enough precision that the "no"
could be made permanent.

## The Constraint Library Flywheel

When rejections become durable, reusable constraints, a flywheel emerges.
You are not scaling experts — you are scaling the encoded residue of expert
judgment.

- A **consulting firm** that encodes partner rejections across thousands of
  engagements builds a repeatable institutional quality bar no competitor
  can replicate by subscribing to the same AI APIs.
- A **media company** that captures editorial judgment across thousands of
  pieces develops a scalable taste that helps individual editors extend
  their attention.

Companies that have done this informally for years already dominate their
markets:

- **Epic Systems** did not win in healthcare by having better technology. It
  spent decades encoding clinical workflows from thousands of hospitals into
  a deeply integrated platform. The development team went onsite, shadowed
  doctors, watched workflows, absorbed domain constraints. The result: a
  system handling over 300 million patient records so embedded in clinical
  operations that switching costs are structural. The moat is not the
  software — it is the encoded judgment about what the software needs to get
  right, built rejection by rejection, workflow by workflow, failure by
  failure.
- **Bloomberg** did the same in financial data. Any vertical SaaS company
  that truly owns a niche is doing some version of this.

What is new is that AI makes the encoding cycle faster. AI generates a
provocation, the expert rejects it, the rejection gets encoded, the library
grows. The taste bar improves every cycle because you are saving all those
nos.

## The Largest Structural Gap in the AI Ecosystem

The infrastructure to capture rejections at scale has not existed in the age
of AI. Almost nobody is talking about how to scale your nos. Every
organization using AI generates rejections at the grassroots level — and
nearly every one falls on the floor.

The right solution is not a separate tool, spreadsheet, database, or
dashboard, because people will not context switch. Capture has to happen
where the work happens — inside the conversation, as a side effect of the
rejection already being performed.

Jones built a solution for this: a constraint library accessible via MCP
server backed by a database, designed to log and encode rejections without
leaving the chat tool. The goal is to stop dropping rejections on the floor
at both personal and small-team scale.

## Implications for Hiring and Talent Development

A constraint library accessible via MCP server has a secondary effect on
talent. Junior professionals who would otherwise lack access to the taste of
a senior expert can query the library and get that perspective immediately.

Positions where people develop recognition can be accelerated — juniors get
a sense of "does this hit the bar?" quickly and start accessing accumulated
context. This addresses a growing crisis: the mixing between juniors and
seniors that used to happen naturally in various disciplines has eroded, and
without it, nobody learns. A constraint library is a mechanism to make taste
learnable and transmissible.

Taste is individual to a particular team and firm. There is no universal
taste library. But the structure for building one can be shared.

## The Frontier of AI Value Is the Frontier of Your Taste

Karpathy's framework — what you can verify, you can automate — has a
corollary: the frontier of AI value is identical to the frontier of your
organization's taste. Where your capacity to verify quality extends, AI
creates more value. Where it does not, AI generates compounding silent
risk — an organization that generates more and more while understanding
less, until it no longer knows where the bar is.

The anti-slop strategy is not "be more careful," "give lectures," or "write
better prompts." It is developing, institutionalizing, and eventually
automating the human skill of rejection so it can scale.

### For Executives

The competitive moat is not which AI vendor you choose — models are
commoditizing. The moat is the depth and durability of your organization's
encoded taste. Audit where domain experts sit. Ask whether their rejections
are being captured or evaporating. Start treating encoded domain judgment as
an asset class.

### For Team Managers

Create space for articulation. When someone rejects AI output, challenge
them to explain why and socialize that explanation. A team that articulates
rejections builds shared understanding of quality that persists across
projects, personnel changes, and tool migrations. A team that silently
fixes AI output is not growing.

### For Individual Contributors

The most valuable professional development is not learning the newest tool —
tools change. It is deepening your ability to recognize when something is
not working, practicing articulation of what is wrong and how to fix it,
and helping stand up a system where that taste can scale.

### For Entrepreneurs

Build products that enable scaling taste. But it cannot be a new pane of
glass or a new website — nobody will context switch. It needs to be
seamless, costing zero additional attention. The capture must be a side
effect of work already being done.

The job now is learning to say no to new and more interesting things,
articulating what is wrong with current AI outputs at high fidelity, storing
those constraints somewhere durable, and using them to both improve AI
outputs and train people earlier in their careers. So much else is becoming
commoditized. But being able to say "this is what's really excellent" — that
is the skill worth getting excited about.
