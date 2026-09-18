---
title: "Field Guide to Fable: A Research System for UI Generation"
author: Thariq Shihipar
channel: AI Engineer
url: https://youtu.be/9fubhllmsBU?is=xiEOaLziyYvJUVrx
date: 2026-07-06 16:00
tags: ai, development
---

# Field Guide to Fable: A Research System for UI Generation

## Scope and evidence

This article interprets Thariq Shihipar's talk as a method for researching and building UIs.
It uses only the supplied transcript and video description, not outside documentation.
The talk is a field guide, not a formal paper about a UI model or a released benchmark.
Here, “research system” means an empirical workflow for discovering requirements with Fable.
It does not imply that the talk presents Fable's training recipe, architecture, or UI scores.

Caption caveat: the source is an automatic transcript and may mishear names or terms.
The title and supplied context identify the speaker as Thariq Shihipar of Anthropic.

## Research goal: reveal capability and requirements

Shihipar's central goal is to learn how to work with a new class of model before its rules
are fully understood. He calls the unused potential between a model and its harness
“capability overhang.” In his account, tools, prompts, and interfaces determine which
otherwise inaccessible abilities users can reach.

For UI generation, that makes discovery a joint problem. The system must discover what
Fable can do, while the user must discover what they actually want. Shihipar describes a
specification as a map and the codebase, constraints, and real world as the territory.
An “unknown” appears whenever the territory presents a decision the map did not specify.

His four-part field guide is to unhobble Claude, find unknowns, process the loss attached
to changing work, and become less constrained by old trade-offs. The UI-relevant core is
the second part: turn unspoken taste and omitted constraints into artifacts and decisions.

## Evaluation design: an empirical loop, not a benchmark

The talk reports no controlled study, dataset split, sample size, user study, or UI metric.
It gives no Fable win rate, accessibility score, render accuracy, latency, or token cost.
Accordingly, its evaluation design is best read as Shihipar's practitioner loop:

1. Inspect the real environment before committing to a specification.
2. Generate materially different prototypes rather than one polished guess.
3. Let the user react to visible alternatives and expose tacit preferences.
4. Ask questions whose answers could change the architecture.
5. Implement against references, while logging deviations at unknowns.
6. Review the result and have Fable quiz the user on what changed and why.

This loop evaluates progress by information gained, not by a single aggregate score.
For a production UI team, the talk supports testing whether each pass reduces unresolved
unknowns and whether the operator can explain the resulting implementation. Those are
implementation-oriented criteria inferred from Shihipar's workflow, not reported metrics.

## Data generation: manufacture useful context

Shihipar does not describe Fable's training data. His “data” is working context generated
before and during implementation. It can be organized into six streams.

**Blind-spot passes.** Ask Fable to inspect the relevant code, diffs, or team context and
identify unknown unknowns. Shihipar gives a new authentication provider as an example:
the model can inspect the auth module and search likely sources for recurring gotchas.

**Prototype variation.** For design work, ask for one HTML page containing four widely
different design directions. Shihipar says visible options help surface “know it when I
see it” preferences that the user could not state in advance.

**Interviews.** Once a direction exists, ask Fable to interview the user. Shihipar advises
adding context about the person, project, and stage, then prioritizing questions that
would change the architecture.

**References.** Give the model another map: existing code, a design artifact, or an HTML
mock-up. Shihipar argues that Fable can interpret a reference even when the destination
uses a different language or system.

**Implementation notes.** When Fable encounters an unspecified decision, have it log the
choice, deviation, and context. The notes become a trace for review rather than allowing
silent design drift.

**Quizzes.** Ask Fable to test the operator's understanding before a pull request or merge.
Shihipar presents this as a way to keep the human in the loop and able to represent the
work accurately.

## Model and system design

Shihipar says Anthropic's models are “grown, not designed”: data, feedback, and compute
shape them, while teams learn their behavior empirically. He compares this work more to
biology than physics because the rules remain partly unknown and capability is uneven.

His system-design implication is that the harness is part of the effective model. A chat
model may possess facts yet fail at a task that Claude Code can solve with retrieval and
code execution. The extra tools let the system build and test its own context rather than
requiring a user to paste an enormous codebase into a chat window.

Shihipar also says Anthropic removed 80% of Claude Code's system prompt. He attributes the
change to newer models benefiting from fewer examples and constraints: examples may limit
a model that can imagine better approaches. His design advice is to supply context rather
than accumulating prohibitions. This is a reported Anthropic practice, not a causal result
from an experiment described in the talk.

Interaction design also changes with capability. Shihipar compares an ask-user-question
tool that barely worked with Opus 4, could conduct long interviews by Opus 4.5, and could
produce HTML reports with embedded questions under later models and Fable. The point is
not only better text; it is a move from chat turns to generated interactive documents.

## A UI generation workflow

### 1. Inspect before drawing

Ask for a blind-spot pass over the product surface, component library, routes, state,
authentication, data contracts, and nearby implementation history. Require a ranked list
of decisions that could materially alter the UI or architecture.

### 2. Generate a divergent comparison surface

Have Fable build an HTML comparison page with four genuinely distinct directions. Vary
information architecture, density, hierarchy, interaction, and visual language, rather
than merely changing colors. This operationalizes Shihipar's prototype example.

### 3. Turn reactions into requirements

Review the alternatives and record what the user selects, rejects, or combines. Then ask
Fable to translate those reactions into explicit rules and identify any contradictions.
This step converts unknown knowns, such as visual taste, into inspectable context.

### 4. Interview for consequential unknowns

Ask questions that could change data flow, component boundaries, responsiveness,
permissions, or interaction states. Shihipar's advice is to prioritize architectural
consequences, not exhaust the user with low-impact preference questions.

### 5. Ground implementation in references

Attach the chosen HTML mock-up and relevant code as maps. Ask Fable to implement in the
actual stack without assuming that a visual reference specifies every behavior. Require
it to flag conflicts between the artifact and the codebase.

### 6. Log deviations and validate comprehension

Record every consequential choice that was not present in the map. After implementation,
review the notes, inspect the UI, and let Fable quiz the operator. A successful handoff
requires both a usable artifact and a human who understands its important decisions.

## Findings, examples, and comparisons

Shihipar's Pokémon example isolates the harness effect. A normal chat model reportedly
fails to identify names ending in “aw,” while Claude Code fetches the list and filters it
with a script, yielding Croconaw and Drednaw. He uses the contrast to argue that tool use
can expose capabilities that factual recall and unaided reasoning do not reliably reach.

For context management, Shihipar contrasts the imagined path of ever-larger pasted
contexts with Claude Code's ability to search and construct its own context through shell
and environment access. In his interpretation, giving the model “arms” mattered more
than relying only on a huge context window.

For outputs, he describes a progression from Markdown, to plans that explain intended
work, to detailed HTML reports. For requirement gathering, he describes a similar shift
from a fragile question tool to interviews and embedded HTML questionnaires. Together,
these examples frame generated UI as both an output and a research instrument.

For productivity, Shihipar says work that once took him weeks in an old startup codebase
could now take hours. He also reports creating the talk's deck with Fable in about four
hours. These are personal examples, not controlled estimates of general productivity.

## Metrics: what is reported and what remains open

The only concrete quantities in the source are operational anecdotes and system changes:

- Anthropic removed 80% of the Claude Code system prompt, according to Shihipar.
- He contrasts an instruction to ask 40 specification questions with earlier tool limits.
- His UI prototype prompt requests four widely different design directions.
- He reports making the presentation deck in about four hours with Fable.
- He characterizes some formerly multi-week work as achievable in hours.

The talk does not compare Fable against named UI generators, human designers, or a
baseline model on identical tasks. It also does not report completion rate, defect rate,
user preference, accessibility, visual similarity, cost, speed, or maintainability.
Any evaluation program adopting this field guide should define those measures separately.

A useful extension would count unresolved unknowns, logged deviations, prototype rounds,
and architecture-changing answers, then pair them with standard product checks. That is
a proposed measurement layer derived from the workflow, not an Anthropic result.

## Limitations and risks

First, the evidence is a conference talk and description rather than a research report.
Several claims are experiential, and the transcript supplies no method for replication.
Second, automatic captions may have corrupted model names, version numbers, or wording.
Third, Fable's architecture, training data, safety design, availability, and costs are not
specified, so the talk cannot support conclusions about their effects.

Fourth, generating multiple polished prototypes can create false confidence. A visible
mock-up may omit loading, empty, error, permission, and responsive states. Shihipar's map
and territory distinction implies that teams must inspect the actual environment rather
than treat generated HTML as a complete specification.

Fifth, speed does not establish value. Shihipar explicitly warns that building is easier
while generating value remains hard, and that finding valuable work still takes many
attempts. His “good, fast, cheap” challenge is an ambition to test trade-offs, not evidence
that every trade-off has disappeared.

Finally, staying in the loop requires more than approving screenshots. The operator must
understand architecture, review deviations, and be able to explain the work. Shihipar's
quiz step is a practical check, but the talk does not validate it as a safety measure.

## Implementation lessons

1. Treat prompts as provisional maps, not exhaustive specifications.
2. Equip the model to inspect the codebase and test claims in the environment.
3. Use divergent UIs to elicit tacit taste before investing in one direction.
4. Ask fewer, higher-impact questions, especially those affecting architecture.
5. Prefer references and context to long lists of restrictive examples.
6. Require a decision log whenever the implementation departs from the map.
7. Review edge states and real constraints that static HTML can conceal.
8. Measure quality and value separately from generation speed.
9. Keep the human accountable for understanding and communicating the result.
10. Revisit the harness as models change; Shihipar says old prompting rules may constrain
    newer capabilities.

The field guide's lasting contribution is a stance rather than a benchmark: explore the
model empirically, expose unknowns through interfaces, and make deviations inspectable.
In Shihipar's framing, UI generation works best when the UI is not merely the answer. It
is the laboratory in which users and models discover what the answer should be.
