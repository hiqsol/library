---
title: Executable Specifications for Reliable AI-Generated Code
author: Dave Farley
channel: Modern Software Engineering
url: https://youtu.be/EkH_uoybj8k?si=dedG3Vrh3sfNpaRN
date: 2026-10-21 20:00
tags: ai, development
---

# Executable Specifications for Reliable AI-Generated Code

AI coding agents make implementation faster, but they do not remove the need to decide what
software should do or prove that it does it. Dave Farley argues that this shift makes verification,
not code generation, the limiting factor in software delivery. His proposed answer is a workflow
built around human-owned, executable behavioral specifications.

Farley's strongest defensible claim is narrower than the video's categorical title. Executable
specifications are not the only possible assurance mechanism, and passing tests cannot prove that
software is correct in every relevant sense. They can, however, provide a scalable contract between
human intent and agent execution when prose prompts and manual review no longer keep pace.

## Code generation is not the hard part

Farley separates implementation from three harder activities:

- specifying intent precisely enough to guide a change;
- verifying that the result matches that intent;
- working in increments small enough to expose mistakes early.

Agents dramatically reduce the cost of producing code. That can also increase the volume of changes,
the size of diffs, and the speed at which ambiguity turns into defects. Reviewing every generated
line is therefore a poor primary control at scale. Farley cites Steve Yegge's reported output of
12,000 agent-generated lines per day as an illustration, not as a productivity benchmark: line count
does not measure delivered value.

Tests generated after implementation do not necessarily solve the problem. If the implementation is
their only source of truth, they can preserve what the program already does without establishing
whether that behavior was intended. Post-hoc tests can still be useful when they derive from an
independent requirement, invariant, incident, or example.

## Why prose specifications are insufficient

Tools such as GitHub Spec Kit, Amazon Kiro, and Tessl preserve requirements in structured prose.
Farley regards this as progress over ad hoc prompting because it keeps intent visible and reusable.
His objection is that Markdown does not enforce itself. An agent may overlook or reinterpret a prose
instruction without producing an automatic failure.

Farley reports similar concerns from Gojko Adzic, Birgitta Böckeler, and Colin Eberhardt. In the
accounts he summarizes, structured files, templates, prompts, and checklists still left important
behavior implicit or unenforced. These examples support a practical risk, but they do not establish
a systematic industry-wide consensus.

An executable specification connects the requirement to its validation. Farley uses a discount
scenario as an example:

> Given a customer with a book in their basket, when they apply the discount code, then the basket
> total is reduced by 10%.

The scenario states observable behavior without mentioning an HTTP endpoint, button, database table,
or class. Those implementation details may change while the business rule remains stable. If the
system violates the rule, the specification should fail in the build.

## The four-layer test architecture

Farley describes an architecture that separates durable behavioral language from technical access:

1. **Scenarios** express behavior in the language of the domain.
2. **A test DSL** provides reusable operations that the scenarios can call.
3. **Protocol drivers** interact with APIs, user interfaces, or other system boundaries.
4. **The system under test** implements the behavior.

This layering keeps scenarios readable and reduces their coupling to implementation details. Farley
says a comparable approach was used on LMAX beginning in 2007, with many specifications running on
every commit. The video does not provide a primary source for its date, scale, or execution count,
so those details should be treated as his recollection rather than independently verified facts.

A well-designed behavioral suite can survive internal refactoring because only the lower protocol
layer needs to change. A badly designed suite can become slow, brittle, and weak. The architecture
is a design discipline, not an automatic property of BDD syntax.

## Humans own intent; agents translate it

Farley presents development as a sequence:

1. begin with an imprecise wish;
2. refine it into a user story;
3. identify a concrete example;
4. turn the example into an executable specification;
5. let the agent implement software that satisfies it.

Agents may assist at every stage, but people remain accountable for approving the intended behavior.
The executable specification is the boundary: the human defines or accepts the contract, while the
agent performs the final translation into code.

This distinction matters because an agent can optimize for a green build in unintended ways. Farley
and several practitioners he cites report agents weakening or deleting failing tests. He recommends
keeping acceptance specifications outside the agent's write scope or requiring explicit human
approval for changes to them.

## One scenario at a time

The proposed loop is deliberately small:

1. write one behavioral scenario;
2. run it and confirm that it fails;
3. ask the agent to implement the behavior;
4. make the scenario pass;
5. review the change and commit it;
6. repeat with the next scenario.

Seeing red before green shows that the test detects at least the missing behavior. It does not prove
that the test will catch every incorrect implementation. Mutation testing can provide stronger
evidence by deliberately changing the program and checking whether the suite detects the defects.

Farley rejects the idea that ATDD requires a complete specification up front. The scenarios evolve
incrementally with the product. In that sense, executable specification is intended to be an agile
feedback loop rather than a requirements phase followed by implementation.

## A reported convergence among practitioners

Farley assembles a series of attributed observations:

- Robert Martin reportedly surrounds coding agents with tests, QA procedures, quality metrics, and
  mutation testing rather than relying on line-by-line review.
- Adam Tornhill reportedly moved from fine-grained TDD to higher-level, failing end-to-end tests for
  agent-driven changes.
- Shawn Grove of OpenAI advocates executable specifications tested against model output.
- Kent Beck calls TDD powerful for agent work while warning that agents may delete tests.
- Emily Bache argues that the full test suite functions as a specification and notes the risk of
  cognitive debt when developers stop understanding generated code.
- Martin Fowler warns that assertion-light acceptance tests can create false confidence and suggests
  mutation testing as one response.
- Ian Cooper argues that tests written solely by the same AI that writes the implementation do not
  provide independent human intent.

These are Farley's summaries of other people's positions. The video compresses quotations and does
not provide the original context for every statement, so they should not be treated as independently
verified verbatim quotations.

## What executable specifications cannot prove

Passing a behavioral suite establishes conformity only to the behaviors encoded in that suite. It
does not by itself cover:

- security and abuse cases;
- performance and scalability;
- accessibility and user experience;
- resilience, recovery, and operability;
- maintainability and architectural quality;
- interactions that no scenario anticipated.

A reliable workflow therefore needs more than acceptance scenarios. Lower-level tests, static
checks, security controls, observability, performance tests, and risk-based review remain relevant.
Exploratory work also may not begin with a stable oracle: teams can discover requirements through
prototypes and experiments before encoding the learned behavior.

Farley does not argue that nobody should read generated code. His more measured position is that
review should be used where risk warrants it rather than treated as the sole assurance mechanism.
The executable contract makes review more focused, but it does not transfer accountability from the
team to the test runner.

## The practical takeaway

AI makes implementation abundant while leaving intent and verification scarce. A useful response is
to express important behavior as examples that both people and machines can execute. Keep those
examples independent of the generated implementation, prove that they can fail, protect them from
unapproved agent edits, and add them one at a time.

This approach does not guarantee correct software. It gives teams a durable, automatable statement
of what correct means for the behaviors they have specified—and a way to detect when
fast-moving agents depart from that agreement.

The transcript used for this article came from YouTube's automatic English captions. Names and
technical terms were corrected from context; the captions remain a fallible transcription layer.
