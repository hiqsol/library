# The 5 Levels of AI Coding — Why Most Won't Make It Past Level 2

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=bDcgHzCBgmQ)
- **Author:** Nate B Jones
- **Published:** 2026-02-18 15:01

---

## The Paradox

90% of Claude Code was written by Claude Code. Codex is releasing
features entirely written by Codex. And yet most developers using AI
empirically get slower — at least at first.

StrongDM's software factory has two principles:

1. Code must not be written by humans
2. Code must not be reviewed by humans

Three engineers. No one writes code. No one reviews code. The system
is a set of AI agents orchestrated by markdown specification files.
All the humans do is write specs and evaluate outcomes.

Meanwhile, a rigorous 2025 randomized control trial by METR found
that experienced open-source developers using AI tools took **19%
longer** to complete tasks. Worse: those developers believed AI had
made them **24% faster**. Wrong about both direction and magnitude.

## Dan Shapiro's Five Levels of Vibe Coding

Dan Shapiro, CEO at Glowforge, published a framework mapping where the
industry stands.

### Level 0: Spicy Autocomplete

You type code, the AI suggests the next line. You accept or reject.
GitHub Copilot in its original form. A faster tab key. The human is
still writing the software.

### Level 1: Coding Intern

You hand the AI a discrete, well-scoped task: write this function,
build this component, refactor this module. You review everything that
comes back. AI handles tasks; human handles architecture, judgment,
and integration.

### Level 2: Junior Developer

The AI handles multi-file changes, navigates codebases, understands
dependencies, builds features spanning modules. You review more
complicated output but still read all the code.

Shapiro estimates **90% of developers** who say they are AI-native
operate at this level. They think they are farther along than they are.

### Level 3: Developer as Manager

The relationship flips. You direct the AI and review at the feature
or PR level. The model does implementation and submits PRs. Almost
everybody tops out here because of the psychological difficulty of
letting go of the code.

### Level 4: Developer as Product Manager

You write a specification, leave, come back hours later, check whether
tests pass. You are not reading the code. You are evaluating outcomes.
The code is a black box. Requires trust in the system and
extraordinary spec-writing ability.

### Level 5: The Dark Factory

No human writes code. No human reviews code. The factory runs
autonomously with the lights off. Specification goes in, working
software comes out. Almost nobody on the planet operates here.

## StrongDM's Dark Factory in Detail

Team: Justin McCarthy (CTO), Jay Taylor, and Nan Chowan. Running
since July 2025. Inflection point: Claude 3.5 Sonnet (fall 2024) —
when long-horizon agentic coding started compounding correctness more
than compounding errors.

The factory runs on an open-source coding agent called Attractor. The
repo is three markdown specification files.

### Scenarios vs. Tests

StrongDM does not use traditional software tests. They use
**scenarios** — behavioral specifications stored outside the codebase
that the agent cannot see during development. They function as a
holdout set (like ML's approach to preventing overfitting).

Why: when AI writes code, optimizing for test passage is the default
behavior. Tests inside the codebase allow the agent to game them.
Scenarios live externally and evaluate whether the software actually
works without the agent seeing the evaluation criteria.

### Digital Twin Universe

Behavioral clones of every external service: simulated Okta, Jira,
Slack, Google Docs/Drive/Sheets. Agents develop against these twins,
running full integration testing without touching production systems.

### Output

CXDB (their AI context store): 16,000 lines of Rust, 9,500 lines of
Go, 700 lines of TypeScript. Shipped, in production, built end-to-end
by agents.

### Metric

If you haven't spent **$1,000 per human engineer per day**, your
software factory has room for improvement.

## The Hyperscalers' Self-Referential Loop

**Codex 5.3** is the first frontier model instrumental in creating
itself — not metaphorically. Earlier builds analyzed training logs,
flagged failing tests, suggested fixes. OpenAI reported a **25% speed
improvement** and **93% fewer wasted tokens** from the model
identifying its own inefficiencies.

**Claude Code:** 90% of its codebase was written by itself; converging
toward 100%. Boris Cherny hasn't personally written code in months.
Anthropic estimates functionally 100% of code produced company-wide
is AI-generated.

**4%** of public GitHub commits are now authored by Claude Code;
Anthropic expects this to exceed **20%** by end of 2026. Claude Code
has hit a **billion-dollar run rate** just 6 months since launch.

## The J-Curve Problem

The METR study was a randomized control trial, not a survey. AI made
experienced developers 19% slower because workflow disruption
outweighed generation speed. Developers spent time evaluating
suggestions, correcting almost-right code, context switching, and
debugging subtle errors.

**46%** of developers say they don't fully trust AI-generated code.

GitHub Copilot: 20 million users, 42% market share. Lab studies show
55% faster code completion on isolated tasks. In production: larger
PRs, higher review costs, more security vulnerabilities. One senior
engineer: "Copilot makes writing code cheaper but owning it more
expensive."

Organizations seeing 25-30%+ productivity gains are ones that
**redesigned their entire development workflow** — specs, code review,
junior vs. senior expectations, CI/CD pipelines.

## Organizational Structures Built for Humans

Stand-ups, sprint planning, code review, QA teams — every ceremony
exists because humans building software need coordination. When the
human is no longer writing code, these structures become friction.

StrongDM's three-person team has no sprints, no stand-ups, no Jira
board. They write specs and evaluate outcomes.

The engineering manager's value shifts from "coordinate the team
building the feature" to "define the specification clearly enough
that agents build the feature."

The bottleneck has moved from implementation speed to **spec quality**,
which is a function of how deeply you understand the system, your
customer, and the problem.

## The Brownfield Reality

Most enterprise software is brownfield — accumulated over years,
running in production. The specification does not exist. Tests cover
30% of the codebase; the other 70% runs on institutional knowledge.

The migration path:

1. Use AI at Level 2-3 to accelerate existing work (expect the
   J-curve dip)
2. Use AI to document what the system really does — generate specs
   from code, build scenario suites capturing real behavior
3. Redesign CI/CD pipeline for AI-generated code at volume
4. Shift new development to Level 4-5 autonomous patterns while
   maintaining legacy in parallel

This takes time. For some organizations, multi-year. Depends on
stomach for organizational pain.

## The Talent Reckoning

- Junior developer employment: dropping **9-10%** within six quarters
  of widespread AI tool adoption (Harvard 2025)
- UK graduate tech roles: fell **46%** in 2024, projected **53%**
  further drop by 2026
- US junior developer postings: declined **67%**

The career ladder is hollowed from underneath: seniors at top, AI at
bottom, thinning middle where learning used to happen.

Yet we need more excellent engineers than ever — the bar is rising
toward systems design understanding previously expected of mid-level
engineers.

Hiring is shifting toward **generalists over specialists**. A
specialist who knows everything about Kubernetes but can't reason
about product implications is less valuable than a generalist who
understands systems, users, and business constraints.

## AI-Native Org Economics

| Company | Revenue | Employees | Rev/Employee |
|---------|---------|-----------|--------------|
| Cursor | $500M+ ARR | ~few dozen | ~$3.5M |
| Midjourney | ~$500M | ~100 | ~$5M |
| Lovable | multi-$100M ARR | small team | multi-$M |
| Top 10 AI-native avg | — | — | ~$3M+ (5-6x SaaS avg) |

Traditional SaaS average: ~$600K per employee.

## The Demand for Software Is Infinite

Every time the cost of computing has dropped, total software produced
exploded. Desktop publishing did not eliminate graphic designers.
Cameras in phones created a photography universe. Mobile didn't
replace developers — it multiplied needed applications by orders of
magnitude.

Most of the world cannot afford custom software today. Regional
hospitals run on spreadsheets. Small manufacturers track inventory by
hand. When the cost of production collapses, that unmet need becomes
addressable.

The dark factory does not replace great product thinkers. It amplifies
them — turning one with five engineers into one with unlimited
engineering capacity. The constraint moves from "can we build it" to
"should we build it."
