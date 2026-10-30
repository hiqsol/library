---
title: Executable Specifications for Reliable AI-Generated Code
author: Dave Farley
channel: Modern Software Engineering
url: https://youtu.be/EkH_uoybj8k?si=dedG3Vrh3sfNpaRN
date: 2026-10-21 20:00
tags: ai, development
---

# Executable Specifications for Reliable AI-Generated Code

[article](../../articles/dave-farley/2026-10-21-executable-specifications-for-ai-code.md)

Dave Farley argues that AI makes implementation cheap while leaving intent and verification scarce.
The bottleneck is no longer producing code but specifying useful behavior and proving that generated
software satisfies it.

## Core argument
- Prompts and Markdown specifications preserve intent but do not enforce themselves.
- Manual review cannot remain the primary control when agents generate thousands of lines quickly.
- Tests written from code alone can preserve existing behavior without proving that it was intended.
- Humans should own or explicitly approve behavioral contracts; agents can translate them into code.

Farley favors acceptance test-driven development using BDD-style scenarios. A requirement such as a
10% basket discount should describe observable behavior without mentioning endpoints, buttons,
databases, or classes. The same artifact then serves as both specification and automated check.

## Proposed architecture
1. Domain-language behavioral scenarios.
2. A reusable test DSL.
3. Protocol drivers for APIs, UIs, and other interfaces.
4. The system under test.

This separation can keep behavior stable while technical implementations change. It is not
automatic: poor acceptance tests can still be brittle, slow, or too weak to provide assurance.

## Incremental workflow
1. Write one scenario.
2. Run it and confirm that it fails.
3. Let the agent implement the behavior.
4. Make the scenario pass.
5. Review and commit the small change.
6. Repeat.

The initial failure proves only that the test detects that particular missing behavior. Mutation
testing can probe whether the suite catches a wider range of defects. Acceptance specifications
should also be protected from agents that might weaken or delete failing tests.

## Important limits
Passing tests proves conformity only to encoded behavior. Security, performance, accessibility,
resilience, operability, maintainability, and unexpected interactions require additional controls.
Exploratory work may also need prototypes before teams know enough to write stable specifications.

Farley cites Robert Martin, Adam Tornhill, Shawn Grove, Kent Beck, Emily Bache, Martin Fowler, and
others as evidence of a growing convergence around executable specifications. These are compressed,
attributed summaries from the video, not an independently verified survey or full quotations.
The practical lesson is to replace prose-only intent with small, human-owned examples that can fail
automatically. Executable specifications do not guarantee correct software, but they create a
durable contract that scales better than prompts or line-by-line review alone.

Source transcript: YouTube automatic English captions; names and technical terms were corrected from
context, but the captions remain fallible.
