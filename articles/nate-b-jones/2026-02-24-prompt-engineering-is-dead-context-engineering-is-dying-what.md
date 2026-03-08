# Prompt Engineering Is Dead, Context Engineering Is Dying — What Comes Next

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=QWzLPn164w0)
- **Author:** Nate B Jones
- **Published:** 2026-02-24 15:00

---

## The Klarna Case: When AI Succeeds at the Wrong Thing

In January 2026, Klarna reported its AI agent does the work of 853 full-time
employees and has saved $60 million. In the same earnings cycle, its CEO
admitted the AI strategy cost something far more valuable — and he is still
trying to buy it back.

The AI worked too well. It resolved 2.3 million conversations in the first
month across 23 markets in 35 languages. Resolution times dropped from 11
minutes to 2. The CEO projected $40 million in savings. Then customers
started complaining: generic answers, robotic tone, no ability to handle
anything requiring judgment.

CEO Sebastian Siemiatkowski told Bloomberg: "While cost was a predominant
evaluation factor, the result was lower quality." Klarna began frantically
rehiring the human agents it had gutted.

The interesting reading in 2026: the agent was extraordinarily good at
resolving tickets fast — and that was the wrong goal. Klarna's real
organizational intent wasn't "resolve tickets fast." It was "build lasting
customer relationships that drive lifetime value in a competitive fintech
market." A human agent with five years at the company knows this difference
intuitively. She knows when to bend policy, when to spend three extra
minutes because the customer's tone signals churn. The AI agent had a prompt
and context. It did not have intent.

## The Three Disciplines

### Prompt Engineering (the first discipline)

Individual, synchronous, session-based. You sit in front of a chat window,
craft an instruction, iterate. A personal skill with personal value. This
is the era that produced a thousand "how to write the perfect prompt" blog
posts. Most of them are terrible.

### Context Engineering (the current discipline)

Anthropic published the foundational piece in September 2025. LangChain's
Harrison Chase put it bluntly: "Everything's context engineering. It
describes everything we've done at LangChain without knowing the term
existed."

Context engineering is where the action is right now: building RAG pipelines,
wiring MCP servers, structuring organizational knowledge for agent access.
It is necessary but not sufficient.

### Intent Engineering (the next discipline)

Context engineering tells agents what to know. Intent engineering tells
agents what to want. It is the practice of encoding organizational purpose
— goals, values, trade-off hierarchies, decision boundaries — into
infrastructure that shapes how agents make decisions autonomously.

It is the layer that would have told Klarna's agent: "Yes, you can resolve
this ticket in 90 seconds, but the customer has been with us for years and
their tone indicates frustration. Spend the extra time. Offer them a
specialist. The goal is retention."

## The Scale of the Problem

Deloitte's 2026 State of AI in the Enterprise report (3,000+ leaders,
24 countries): 84% of companies have not redesigned jobs around AI
capabilities. Only 21% have a mature model for agent governance.

Investment is massive: 57% of respondents put 21-50% of digital
transformation budgets into AI automation; 20% invested over half — on
average $700 million for a $13 billion revenue company.

Yet 74% of companies globally report no tangible value from AI. McKinsey
found 30% of AI pilots failed to achieve scaled impact. These numbers
coexist with the investment numbers because organizations have solved
"can AI do this task?" and completely failed to solve "can AI do this task
in a way that serves organizational goals at scale with appropriate
judgment?"

## The Microsoft Copilot Lesson

85% of Fortune 500 companies adopted Copilot. Only 5% moved from pilot to
larger deployment (Gartner). Only ~3% of the total Microsoft 365 user base
adopted Copilot as paid users. Bloomberg reported Microsoft slashing
internal sales targets. Employees resisted — Reddit threads describe
organizations downgrading licenses because employees preferred Claude or
ChatGPT.

The fundamental issue: deploying an AI tool across an organization without
intent alignment is like hiring 40,000 employees and never telling them
what the company does, what it values, or how to make decisions. You get
usage metrics in a dashboard and no measurable impact.

## The Three-Layer Intent Gap

### Layer 1: Unified Context Infrastructure

Every team building agents rolls its own context stack. One pipes Slack
through custom RAG, another exports Google Docs to a vector store, a third
built an MCP server for Salesforce but not Jira, a fourth doesn't know the
others exist. This mirrors the shadow IT crisis of the early cloud era —
except agents don't just access data, they act on it.

MCP (donated to the Linux Foundation in December 2025) has become the de
facto standard with nearly 100 million monthly SDK downloads. But protocol
adoption and organizational implementation are different things. The
question is architectural and political: which systems become agent-
accessible? Who decides what context an agent sees across departments?

Deloitte found nearly half of organizations cited data searchability and
reusability as top challenges blocking AI automation.

### Layer 2: Coherent AI Worker Toolkit

Everyone has their own AI workflow. One person uses Claude for research and
ChatGPT for drafting. Another uses Cursor for code and Perplexity for
fact-checking. None can articulate their workflow in a transferable,
measurable, or improvable way.

The difference between individual AI use and organizational AI leverage is
the difference between one good hire and a system that makes everyone
better — between 30% gains (bolting AI onto existing workflows) and 300%
gains (rethinking workflows around AI capabilities).

Fluency doesn't scale through training alone. It scales through shared
infrastructure. Whether any individual has Slack doesn't matter. Whether
an agent can search 50 people's Slack plus docs plus project plans plus
customer data — that determines organizational-scale work.

### Layer 3: Intent Engineering Proper

OKRs were designed for people. They assume human judgment about
prioritization, trade-offs, and exceptions. Agents don't absorb company
culture through osmosis — through all-hands meetings, hallway conversations,
watching senior people handle ambiguous situations. Agents need explicit
alignment before they start working.

Organizations need machine-readable expressions of organizational intent:

**Goal structures agents can interpret and act on.** Not "increase customer
satisfaction" (a human-readable aspiration). An agent needs: what signals
indicate satisfaction, what data sources contain those signals, what actions
are authorized, what trade-offs are empowered, where the hard boundaries
are.

**Delegation frameworks.** Amazon's "customer obsession" works for humans
because they interpret it contextually. An agent needs it decomposed: when
customer request X conflicts with policy Y, here is the resolution
hierarchy.

**Feedback mechanisms that close the loop.** When an agent makes a decision,
was it aligned? How do we know?

## Why This Hasn't Been Built Yet

1. **It's genuinely new.** Before agents ran autonomously over long time
   horizons, the human was the intent layer. Long-running agents broke that
   model.

2. **Two-cultures problem.** People who understand organizational strategy
   (executives) are not the people who build agents (engineers), and vice
   versa. MIT found AI investment is still viewed as a tech challenge for
   the CIO rather than a business issue requiring leadership across the
   organization.

3. **It's extremely hard.** Most organizations have never made their goals
   explicit and structured. Goals live in slide decks, OKR documents that
   get half-read, leadership principles cited in performance reviews but
   never operationalized, and the tacit knowledge of experienced employees.

## What a Solution Looks Like

**Infrastructure level:** Composable, vendor-agnostic architecture for
agents to operate across systems. MCP is the protocol layer; organizational
implementation requires decisions about data governance, access controls,
freshness guarantees, and semantic consistency.

**Workflow level:** An organizational capability map — a shared, living
understanding of which workflows are agent-ready, agent-augmented, or
human-only. Companies doing this well will likely create a role like "AI
workflow architect" sitting between engineering, operations, and strategy.

**Alignment level:** Goal translation infrastructure converting human-
readable objectives into agent-actionable parameters. Decision boundaries,
escalation triggers, value hierarchies, and feedback loops. Google's Agent
Development Kit separates agent context into working context, session
memory, long-term memory, and artifacts, each with specific governance. A
Google DeepMind paper proposed five levels of AI agent autonomy: operator,
collaborator, consultant, approver, and observer.

## The Race That Actually Matters

If OKRs were the management innovation that let Intel align thousands of
humans in the 1970s, intent engineering is the management innovation that
lets organizations align thousands of agents in 2026 — at speeds no human
manager can supervise.

The race is not an intelligence race. The company with a mediocre model and
extraordinary organizational intent infrastructure will outperform the
company with a frontier model and fragmented, unaligned organizational
knowledge every time.

The most important AI investment in 2026 is not a model subscription. It is
organizational intent architecture: making your company's goals, values,
decision frameworks, and trade-off hierarchies discoverable, structured,
and agent-actionable.

Klarna's lesson: the AI worked brilliantly. That was the problem. The 700
human agents who got laid off took with them institutional knowledge that had
never been documented. The prompt engineering era asked "how do I talk to AI?"
The context engineering era asks "what does AI need to know?" The intent
engineering era asks the question that really matters: **what does the
organization need AI to want?**
