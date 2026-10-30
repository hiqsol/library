---
title: "Full Walkthrough: Workflow for AI Coding"
author: Matt Pocock
channel: AI Engineer
url: https://youtu.be/-QFHIoCo-Ko?is=wdO-18sTfE4cUNQZ
date: 2026-04-24 15:15
tags: ai, development
---

# Full Walkthrough: Workflow for AI Coding

[article](../../articles/matt-pocock/2026-04-24-full-walkthrough-workflow-for-ai-coding.md)
## Core idea
- Pocock applies classic engineering discipline rather than treating AI as a code compiler.
- Humans own intent, architecture, taste, and review; agents execute bounded work.
- Fresh contexts keep agents in the smart zone; long contexts drift into the dumb zone.
- His rough coding threshold is about 100K tokens, even with a one-million-token window.
- Keep system prompts tiny, watch token use, and prefer clear restarts over compaction.
## Align and define the destination
- Start with `grill me`, which asks one recommended, decision-focused question at a time.
- Sessions can reach 40, 80, or about 100 questions and last an hour.
- The goal is a shared design concept, not a prematurely polished plan.
- Product, domain, and engineering experts should join when one person lacks an answer.
- Planning is human-in-the-loop; implementation can become AFK once ambiguity is removed.
- Turn the aligned conversation into a PRD that defines the destination and scope.
- Include user stories, module changes, testing decisions, and excluded work.
- Do not over-optimize the PRD; Pocock values alignment and later QA more.
## Plan the journey
- Convert the PRD into independently grabbable issues with explicit blockers.
- Treat the Kanban board as a DAG that exposes safe phases and parallel work.
- Demand tracer bullets: thin vertical slices through data, service, route, and UI.
- The demo's first useful slice awards lesson points and shows them on the dashboard.
- Review decomposition yourself; naming a sound principle does not ensure the agent follows it.

## Implement and verify
- Tune one observed `once.sh` Ralph iteration before running an unattended loop.
- Let AFK agents select eligible work, implement it, run checks, and commit the result.
- Use red-green-refactor: one failing test, minimal passing code, then cleanup.
- Pocock says TDD reduces tests that merely confirm an agent's own implementation.
- Tests, types, builds, and observable behavior steer agents that would otherwise code blind.
- The demo reaches 284 passing tests after the agent fixes a TypeScript error.
- Reset context before AI review so the reviewer begins in the smart zone.
- Then review tests first, inspect implementation, and perform manual human QA.
- QA finds a missing `point_events` table despite green tests and type checks.
- Turn QA findings into new Kanban issues; review is part of the loop, not only a final gate.

## Architecture and scale
- Favor deep modules: simple interfaces around substantial, coherent, testable behavior.
- Treat them as gray boxes whose contracts humans understand while agents fill the interior.
- Put module maps and test boundaries in PRDs and issues, not only global instructions.
- Let implementers pull standards as needed; push mandatory standards into reviewer prompts.
- Sandcastle runs issues in parallel Docker sandboxes, Git worktrees, branches, and reviews.
- A planner selects unblocked issues; implementers code; reviewers inspect; a merger integrates.
- Pocock uses Claude Sonnet to implement and Claude Opus to review.
- Use three throwaway UI prototypes for fast human visual feedback before commitment.
- Share research, prototypes, and PRDs across the team; the path is iterative, not waterfall.
- Remove completed PRDs that may rot; Pocock closes GitHub Issues to preserve marked history.

## Caveat
- This is Pocock's preferred, customizable workflow, not a universal prescription.
- Exact captioned commands for `acceptEdits`, Vitest, type-checking, and migration are uncertain.
