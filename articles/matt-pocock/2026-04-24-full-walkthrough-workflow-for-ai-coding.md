---
title: "Full Walkthrough: Workflow for AI Coding"
author: Matt Pocock
channel: AI Engineer
url: https://youtu.be/-QFHIoCo-Ko?is=wdO-18sTfE4cUNQZ
date: 2026-04-24 15:15
tags: ai, development
---

# Full Walkthrough: Workflow for AI Coding

Matt Pocock presents AI coding as an application of established software-engineering
practice, not a replacement for it. His workflow keeps humans in charge of product intent,
architecture, and judgment while giving agents bounded, testable work they can execute.

The tutorial follows a course-platform gamification feature, but the method is general:
align on the idea, record the destination, split the journey into dependency-aware slices,
implement with feedback, review from fresh context, perform human QA, and feed findings
back into the backlog.

This is Pocock's working method, not a universal prescription. He repeatedly invites teams
to tune it to their own codebases, constraints, and failure modes.

## 1. Design for the model's smart zone

Pocock borrows Dex Horthy's distinction between an LLM's **smart zone** and **dumb zone**.
A fresh context has the least strained attention relationships and tends to produce the
model's best work. As tokens accumulate, its decisions become less reliable.

Pocock's rough marker is about **100,000 tokens**, or around **40%** in one example. He says
a one-million-token window may mostly extend the dumb zone compared with a 200K window;
large windows can still be useful for retrieval, such as searching several copies of
*War and Peace*, without preserving equal coding quality throughout.

The practical response is to size each task so exploration, implementation, and testing
fit inside a fresh smart-zone session. A large feature should become several bounded jobs,
not one heroic conversation.

Baseline context matters too. The system prompt is present for every turn, so Pocock keeps
it tiny. He has seen setups begin with **250K tokens** of instructions, which he says puts
the agent in the dumb zone before useful work starts. He recommends displaying exact token
usage in the coding UI so context pressure remains visible.

Pocock distinguishes clearing from compacting:

- **Clear** deletes the working conversation and returns to the stable baseline prompt.
- **Compact** summarizes the accumulated session and carries that history forward.

He prefers clearing whenever durable artifacts can restore the facts an agent needs.
Compaction leaves summarized "sediment" in context; a clean restart is more predictable.
The desired pattern is therefore deliberate amnesia backed by PRDs, issues, commits, tests,
and repository knowledge that a fresh agent can recover.

Subagents can protect the parent context. In the demo, an exploration subagent used about
**93.7K Opus tokens** in its isolated context, then returned only a summary to the parent.
This spends tokens, but avoids filling the orchestrating agent with every exploration step.

## 2. Start with alignment: the `grill me` skill

The initial brief says students sign up for courses, complete a few lessons, then drop off.
The proposed response is gamification. That is an idea, not yet an implementable feature.

Pocock normally starts work by clearing context and invoking a small `grill me` skill with
the brief. Its central instruction is to interview the user relentlessly until both sides
share an understanding. It walks branches of the decision tree, resolves dependencies one
at a time, recommends an answer with each question, and asks questions individually.

This stage is not primarily about generating a plan. Drawing on Frederick P. Brooks's
*The Design of Design*, Pocock calls the target a shared **design concept**: a vocabulary
and mental model held by the human and agent together. He argues that ordinary plan mode
is too eager to produce a document before it has asked enough questions.

The gamification interview surfaces decisions the original brief omits:

- Which actions award points, and in what amounts?
- Should video-watch events count, despite being noisy and gameable?
- Should existing lesson completions receive points retroactively?
- What is the level progression curve?
- Are streaks independent, or do they award points?
- Where should the interface live? The demo chooses the dashboard.

Pocock often accepts a strong model recommendation, but the decision remains visible to the
human. A real grilling session may contain **40**, **80**, or about **100 questions** and
last an hour. The workshop shortcut makes the model answer **22** of its own questions;
that is explicitly a demo acceleration, not the ideal process. The resulting conversation
uses about **25K tokens**, much of which Pocock regards as valuable alignment material.

Meeting transcripts and domain-expert input can seed the same process. If one developer
cannot answer a product, architecture, or implementation question, Pocock recommends
bringing the relevant product owner, developer, or domain expert into the session. The
agent becomes a relentless third participant in pair or mob planning.

This is a **human-in-the-loop** task. Pocock rejects the suggestion to Ralph-loop the
interview: choosing what to build cannot be reduced to unattended execution. Repeatedly
bad or excessive questions should instead become edits to the reusable skill, including
explicit stop conditions where needed.

## 3. Separate the destination from the journey

Once alignment is strong enough, the workflow creates two different artifacts:

1. A **destination document** describing the intended outcome and definition of done.
2. A **journey representation** describing small, ordered paths to reach that outcome.

The product requirements document is the destination. Pocock invokes `write a PRD` after
`grill me`, although the PRD skill can conduct its own interview when used alone. His
preferred template includes:

- the user's problem and a proposed solution;
- user stories, formal or Cucumber-like if useful;
- implementation and testing decisions;
- proposed modules to modify; and
- an out-of-scope section that records exclusions and helps define done.

In the demo, the PRD describes a gamification service, level thresholds, and roughly
**18 user stories**. Crucially, it also identifies modules and test boundaries. This is not
"specs to code" with the codebase ignored. Pocock argues that developers must keep shaping
the code because the code, not the prose specification, is the enduring battleground.

Pocock usually does not closely reread the generated PRD prose. That is a personal practice,
not a claim that planning needs no review. The high-value review happened interactively
during grilling, and the route through issue decomposition is reviewed again. He treats the
PRD mainly as a durable summary that lets a fresh agent recover the agreed destination.

For the workshop, PRDs and issues are local Markdown files under `issues`. In his normal
work, Pocock uses GitHub Issues. He cites his `mattpocock/course-video-manager` repository,
through which he recorded about **1,000 videos** and closed **744 issues** containing PRDs
and implementation work.

He advises against endlessly optimizing a "perfect PRD" with a deep-thinking model. In his
experience, extra polishing yields less value than early alignment and later QA. The plan is
a guide to the destination; implementation and observation reveal the real journey.

## 4. Turn the journey into a Kanban dependency graph

A long, numbered, multiphase plan still tends to serialize work. Pocock instead uses a
Kanban backlog whose tickets state their blockers. Conceptually, this is a directed acyclic
graph, or **DAG**:

- an unblocked foundational issue can run first;
- two issues that depend on it can then run in parallel; and
- a later issue begins only when all of its predecessors are complete.

The demo's initial decomposition contains five tasks around schema and the gamification
service, streak tracking, lesson and quiz wiring, retroactive backfill, and final dependent
work. One task is blocked by nothing, wiring depends on tasks 1 and 2, backfill depends only
on task 1, and the final task depends on the preceding work.

Pocock's `PRD to issues` skill explores the repository when needed, drafts slices, quizzes
the user, and creates independently grabbable tickets with explicit relationships. In the
workshop, he has to correct an ambiguous redirect: rather than "create them in issues," the
agent must create **local Markdown files** that reference the local PRD. Precise output
location and format matter.

## 5. Demand tracer bullets, not horizontal layers

AI often decomposes systems horizontally: complete the schema, then the API, then the UI.
Pocock argues that this leaves the agent "coding blind." No full feedback path exists until
late, so assumptions pile up before integration exposes them.

He instead asks for **tracer bullets**, the term from *The Pragmatic Programmer*. A tracer
round glows along its route; in software, a thin vertical slice makes the implementation
path visible by crossing all necessary layers and producing an observable result.

The model initially violates that instruction by making "create the gamification service"
the first isolated task. Pocock corrects it with one concrete sentence: "The first slice is
too horizontal." The revised first slice is **award points for lesson completion, visible
on the dashboard**. It includes minimal data, service, route, and UI work in one testable
flow. Later tickets extend a path already proven end to end.

Naming a principle does not guarantee that an agent follows it. Pocock recommends inspecting
ticket shape because decomposition is cheap to review and has high leverage. Older software
books supply useful natural-language concepts for prompts, but humans must verify the
result rather than reward vocabulary alone.

## 6. Mark the boundary between human work and AFK work

Pocock divides work into two modes:

- **Human-in-the-loop:** ambiguity, product choices, research, prototypes, architecture,
  destination alignment, backlog design, QA, and consequential review.
- **AFK:** sufficiently clear implementation tasks that an agent can perform while the
  human is away from the keyboard.

He describes this as a human day shift and an AI night shift. Humans decide and queue work;
agents execute the prepared backlog. The point of detailed planning is not ceremony. It is
to create a long runway of unambiguous, bounded work that can safely continue unattended.

AFK is a ticket property, not a blanket permission. The demo's implementer is told to choose
only issues marked AFK and to emit a defined "no more tasks" signal when none remain. If a
task encounters a product decision, it should return to the human-reviewed side of the
boundary rather than invent policy.

## 7. Begin automation with one observable Ralph iteration

A Ralph loop repeatedly asks an agent to take a small step toward a defined destination.
Pocock prefers more structure than a raw "keep improving until done" loop, so Ralph selects
work from the prepared issue graph.

The demo's `once.sh` performs one iteration. It:

1. reads and concatenates the local issue Markdown files;
2. retrieves the last **five Git commits**;
3. loads the implementation prompt;
4. starts Claude Code with the backlog and commit context; and
5. lets it select and implement one eligible issue.

The transcript describes Claude Code permission mode as "accept edits"; the exact spelling
may be `acceptEdits`, but the displayed command is not confirmed. It also does not clearly
explain why the last five commits are included, so no rationale should be inferred.

The selection policy roughly prioritizes critical bugs, development infrastructure,
tracer-bullet work, polish, quick wins, and refactors. The agent explores the repository,
uses TDD, runs feedback loops, commits the result, and leaves reviewable output.

Pocock strongly recommends tuning the one-shot prompt while watching it before wrapping it
in an unattended loop. Multiplying a flawed iteration only multiplies its failure mode. His
full AFK runner uses a Docker sandbox, but conference attendees do not install its image.

In the live run, the agent chooses **issue 02**, creates a migration and gamification code,
and commits the result. Pocock presents the completion summary as typical Ralph output.

## 8. Make TDD and repository feedback do the steering

Pocock calls test-driven development "absolutely essential" for getting the most from coding
agents where it is practical. His repository skill teaches **red-green-refactor**:

1. Write one test for the next behavior.
2. Run it and confirm that it fails for the intended reason.
3. Add the minimum implementation needed to make it pass.
4. Refactor while keeping the test green.

In the example, a test uses the existing test-database infrastructure and initially fails
because the gamification service does not yet exist. The spoken command is almost certainly
`npx vitest`, but the auto-caption says "NPX V test," so the exact command remains uncertain.

Pocock argues that test-first work makes it harder for an agent to "cheat." When an agent
writes all implementation first and adds tests afterward, those tests may merely encode its
own assumptions. A failing test written first instruments the desired behavior before the
implementation can redefine it.

Tests are only one feedback loop. The agent also runs `npm run test` and a type-check script,
finds a TypeScript error, fixes it, and finishes with all tests passing. Pocock reports
**284 tests** in the repository at that point. The exact type-check command is uncertain:
the transcript says `npm run type check`, while the real script may be `npm run typecheck`
or another repository-specific spelling.

Pocock's broader claim is that repository feedback sets the ceiling on AI coding quality.
Before changing prompts or models, improve tests, type checking, linting, build checks, and
observable end-to-end behavior. Without fast feedback, the agent is coding blind.

TDD is not equally easy everywhere. Pocock explicitly says to use it "where you can pull it
off," and mature front-end behavior remains difficult to judge through text-only checks.

## 9. Review with fresh AI context, then perform human QA

The implementing agent should not immediately review its own work in the exhausted context
that produced it. Pocock's sequence is:

1. finish implementation and automated checks;
2. clear the context;
3. review the diff and tests in a fresh smart-zone context; and
4. conduct human code review and manual QA.

Pocock says tokens are cheap relative to review and that fresh-context AI review catches
many bugs. It is still automated review, not a substitute for human judgment. For human
code review, he starts with the tests, checks whether they specify reasonable behavior,
then reads the implementation and exercises the product.

The demo proves the distinction. After tests and type checks pass, Pocock logs in as student
**Emma Wilson**, opens **Introduction to TypeScript**, continues learning, and completes a
lesson. SQLite fails because the required `point_events` table is missing. Automated checks
did not catch the migration or environment integration problem.

A possible migration command is captioned roughly as "NPM DB migrate push." Its exact
spelling is not established and should not be copied as a verified command.

For Pocock, manual QA is also where human taste and product intent return to the system.
He warns that automating idea generation, planning, implementation, and QA end to end can
produce software that fails, misses its purpose, or lacks taste. His blunt description of
that result is "slop."

QA is not merely a final gate. Defects and observations become new Kanban tickets, including
new blockers, while other unblocked work can continue. The workflow is a cycle, not a
one-way spec-to-code conveyor belt.

## 10. Shape the codebase into deep, testable modules

Pocock connects agent performance to John Ousterhout's *A Philosophy of Software Design*.
A shallow architecture has many tiny modules, narrow functions, and dense interdependence.
An agent must traverse a large graph to find behavior, while tests either mock everything
or isolate units so narrowly that call order and integration behavior disappear.

A **deep module** exposes a small interface while containing substantial coherent behavior.
It provides a meaningful test boundary, lets callers depend on a simple API, and gives an
agent one place where it can understand, modify, and test an entire capability.

The gamification PRD therefore names the gamification service as the deep module, specifies
its interface and tests, and lists changes to the progress service, lesson route, and
dashboard route. Architecture is carried through concrete module maps, interfaces, routes,
and issue boundaries, not only through a global instruction file.

Pocock calls these modules **gray boxes**. The human understands each module's purpose,
interface, behavior, and conditions, but may delegate its internal implementation without
reading every line. In his view, this preserves a coherent mental model while still gaining
speed. The human owns the shape of the codebase; the agent fills in bounded interiors.

His `improve code base architecture` skill scans for clusters that could become deeper,
more testable modules. In the exercise repository it identifies candidates such as a quiz
scoring service and extracted reordering logic. It explains coupling, suggests dependency
and test strategies, and finds that quiz scoring currently has **zero tests**.

In Pocock's browser-based course video editor, a larger module spans front-end interaction
through back-end handling, coordinated with a discriminated union. Tests can verify that a
front-end action causes the correct back-end effect. Pocock describes the improvement in
agent performance as "night and day."

## 11. Push mandatory standards; let implementers pull references

Loading every coding rule into every context recreates the bloated-system-prompt problem.
Pocock separates instruction delivery into **push** and **pull**:

- **Push:** automatically include instructions, such as rules in `CLAUDE.md`, on every
  relevant invocation. They consume context whether needed or not.
- **Pull:** expose a small description of repository knowledge, usually a skill, and let
  the agent retrieve its full content only when relevant.

His preferred split is role-specific. The implementer can pull coding standards as needed,
keeping its context lean. The reviewer receives the applicable standards directly in its
prompt, because compliance is then a mandatory evaluation criterion rather than optional
reference material.

This also answers part of the architecture-and-security question: put concrete architecture
in the PRD and issues, make detailed standards retrievable during implementation, and push
the exact constraints into review. Pocock does not claim that one enormous `CLAUDE.md` can
reliably govern everything.

## 12. Scale out with Sandcastle

After a sequential Ralph loop works, Pocock scales the same issue graph with **Sandcastle**,
his TypeScript library for AFK agent loops. A Sandcastle `run` creates a Git worktree,
places it in a Docker sandbox, runs a prompt, and leaves the result on a branch for later
review and merging.

The demonstrated orchestration has four roles:

1. A **planner** reads the backlog and selects a requested number of mutually runnable,
   unblocked issues.
2. An **implementer** gets each issue number, title, and branch, then runs a Ralph-like loop
   in its own worktree and container.
3. A **reviewer** examines branches on which the implementer created commits.
4. A **merger agent** merges the accepted branches and resolves merge-time test or type
   failures.

Because each issue has blockers, the Kanban DAG naturally creates waves of parallel work.
Separate worktrees and branches isolate agents; the reviewer and merger provide explicit
control points before integration.

Pocock says Sandcastle has been his standard workflow on most projects for some time. In
his model assignment, **Claude Sonnet** implements and **Claude Opus** reviews. He reserves
the stronger model for review because that is where he wants more reasoning capability.
Implementers pull standards; reviewers receive those standards directly.

Parallel output does not eliminate the human review problem. Pocock expects AI to create
more code-review work and says he does not yet know the ideal answer when long AFK runs
conflict with a preference for small, self-contained pull requests. Shorter loops or stacks
of PRs are possibilities, not settled recommendations in the tutorial.

## 13. Use prototypes and collaboration before committing

The path from idea to PRD is deliberately nonlinear. When grilling reveals uncertainty,
teams can research, compare services, test a third-party library, or build a throwaway
prototype. Findings then return to the conversation and may reshape the destination.

For front-end work, Pocock suggests asking the agent for **three clickable prototypes** on
a throwaway route. A human can compare them, choose a direction, and feed the selected
artifact and critique back into grilling. The prototype is supposed to be messy; requiring
a full PRD first would defeat its purpose of shortening the feedback loop.

He names `agent-browser` and Playwright MCP as ways for agents to navigate and inspect UIs.
His assessment at the time is that they still do not reliably produce polished front ends
inside mature products. AI can generate options, while human eyes remain responsible for
visual quality and taste.

In a team, PRDs, research, and prototypes become collaboration surfaces. Product owners,
developers, and domain experts can review them or request comments. A developer or small
controlling group can run the tight workflow, then bring the result to the wider team for
full review and a merge decision.

## 14. Retire stale planning artifacts

A completed PRD can rot as file names, architecture, and requirements change. An agent may
later find the obsolete document and incorrectly treat it as current truth. For that reason,
Pocock generally removes completed PRDs from the repository and closes the corresponding
GitHub Issue instead. The history remains retrievable, while the closed state marks it as
completed and potentially obsolete.

He presents this as a preference, not a universal answer. He has not personally evaluated
the BEADS framework, though he says it appears promising as another issue-management
approach. He also declines to turn the stale-PRD argument into a firm policy on squashing
database migrations: migrations are deterministic chronological records, and he regards
the analogy as unresolved.

## The workflow as a continuous system

Pocock's full loop can be summarized as follows:

1. Keep baseline context small and start consequential tasks fresh.
2. Use `grill me` to align humans and the agent on the design concept.
3. Research or prototype wherever the interview reveals uncertainty.
4. Capture the destination in a code-aware PRD, including scope and test decisions.
5. Convert the PRD into independently grabbable tracer-bullet issues in a Kanban DAG.
6. Review the decomposition and mark only suitable tickets AFK.
7. Tune one observable Ralph iteration before automating repeated execution.
8. Implement with red-green-refactor and repository feedback loops.
9. Run fresh-context AI review, then human code review and manual QA.
10. Feed defects and discoveries back into the issue graph.
11. Parallelize unblocked work in isolated Sandcastle worktrees when the loop is stable.
12. Merge deliberately, share with the team, and retire stale planning artifacts.

The unifying principle is feedback. Small contexts improve model attention; grilling tests
shared understanding; tracer bullets test integration early; TDD tests behavior before
implementation; automated review tests the diff from fresh context; and human QA tests the
actual product against intent and taste. In Pocock's account, AI coding works best when
classical engineering practice makes every important assumption observable and correctable.

## Transcript and command caveats

This article normalizes obvious auto-caption errors such as "traceable bullets" to
**tracer bullets**, "Claude.md" to `CLAUDE.md`, and "agent browser" to `agent-browser`.
The following command details remain uncertain and should be checked before use:

- "accept edits" may be Claude Code permission mode `acceptEdits`.
- "NPX V test" is likely `npx vitest`.
- `npm run type check` may actually be `npm run typecheck` or a project-specific script.
- "NPM DB migrate push" is not clear enough to normalize into an executable command.

The tutorial also leaves the rationale for injecting the last five commits unstated. Those
uncertainties are preserved rather than silently converted into authoritative instructions.
