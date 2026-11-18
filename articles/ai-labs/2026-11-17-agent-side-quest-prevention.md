---
title: Preventing AI Coding Agents from Following Stale Instructions
author: AI LABS
channel: AI LABS
url: https://youtu.be/JhZB3spnuIY?si=9NFF6iXlqhr8LiPJ
date: 2026-11-17 17:31
tags: ai, development, technology
---

# Preventing AI Coding Agents from Following Stale Instructions

[summary](../../summary/ai-labs/2026-11-17-agent-side-quest-prevention.md)

Coding agents can treat stale comments, plans, and instruction files as active requirements. The
result may be wasted investigation, unnecessary edits, or implementation based on obsolete intent.
AI LABS presents this as Claude Code's biggest problem. Google established a narrower point: inline
bug references can measurably distract agents, but it did not rank this above every other failure
mode or release a public Claude Code fix.

The useful response is not to make current code the universal authority. It is to reduce stale
context, preserve provenance, mark document status, constrain scope, and stop for clarification when
code, plans, tests, runtime behavior, and product intent disagree.

## What Google measured

Google studied distributed traces from millions of monthly file-reading sessions involving thousands
of engineers and hundreds of millions of agent steps. It used inline `TODO(bug/...)` and
`FIXME(bug/...)` references as an observable proxy for distraction. The linked ticket supplied a
canonical status, while the user's prompt showed whether the bug was part of the requested task.

The result was a funnel with distinct denominators:

- 13% of file-reading sessions exposed an agent to one of these bug references.
- Agents ignored the reference in 94% of encounters.
- In 6% of encounters, the agent subsequently acted on the referenced bug ID.
- Of those secondary actions, 83% were not requested in the user's prompt.
- Of unprompted detours, 32% concerned fixed or verified tickets.
- Another 9% concerned obsolete or won't-fix tickets.
- A further 2% concerned duplicate or restricted tickets.
- The remaining 57% concerned open tickets.
- Within that open-ticket group, 61% stopped at lookup and 39% edited code.

The 83% figure therefore does not mean that four out of five exposed sessions went astray. If the
published percentages compose as written, unprompted secondary action occurred in roughly 0.65% of
all file-reading sessions: 13% multiplied by 6% multiplied by 83%.

AI LABS compresses the closed categories into "already fixed" and says the open group started fixing
bugs. Those descriptions overstate the source. Nine percentage points were obsolete or won't-fix,
and most open-ticket detours involved investigation rather than code edits.

## The overhead was substantial but observational

Google associated unprompted bug detours with, per session:

- 70% more agent steps;
- 77% more tokens;
- 105% more wait time.

A 105% increase is about 2.05 times the comparison wait time. Google controlled for developer,
codebase complexity, task type, model tier, files read, initial prompt length, and the step at which
the reference appeared. It used multi-way fixed effects with developer-clustered standard errors and
reported `p < 0.0001` for all three effects.

This was an observational regression, not a randomized experiment. The controls reduce measured
confounding but do not prove that a TODO alone caused all extra work. Google did not publish
absolute sample counts, confidence intervals, raw data, code, or model-specific results. The
measurements also cover specially formatted bug references, not every stale spec, memory note,
instruction conflict, or long-context failure discussed in the video.

Google illustrates two mechanisms. One agent investigating an unrelated issue encountered a TODO
whose ticket had been fixed in 2023 and spent further steps researching it. Another encountered an
open TODO, searched internal systems, modified `ModelDownloaderV1`, and later acknowledged that it
had expanded scope after a human challenged the change.

## Google's cleaner used evidence and human review

Google built agents to scan codebases for references to fixed or obsolete bugs. A closed ticket was
not enough to justify deletion. The cleaner examined ticket history, file history, and related code
changes, sometimes spanning years. It proposed a change only when it could establish that both the
reference and its underlying intent were obsolete.

Google reports removing thousands of obsolete references over six months, with more than 95% of
submitted changes accepted by human reviewers. It does not disclose the exact denominator or a
before-and-after evaluation showing that cleanup reduced the 70%, 77%, or 105% overheads. The work
supports history-aware cleanup with review, not autonomous deletion and not a released product.

## Stale instruction files are a separate measured problem

The video's claim that Claude Code and Codex followed an outdated instruction file roughly nine
times out of ten comes from a separate 2026 preprint, not Google's analysis and not a documented AI
LABS experiment. The study used 40 small synthetic Python projects, 16 binary convention conflicts,
two agents, two conditions, and 320 runs.

Without a sentence giving existing code precedence, 649 of 720 choices, or 90.1%, followed the stale
file. With the sentence, 658 of 720 choices, or 91.4%, followed the code. Claude Code moved from
7.5% to 94.4% code-following; Codex moved from 0.8% to 88.3%.

This is strong evidence for the tested convention-conflict setup. It is not proof that existing code
should defeat an approved product requirement, migration plan, security policy, or incomplete ticket
in a real repository. The study used small synthetic projects, narrowly restricted commands, fresh
copies, and specific model and agent versions.

AI LABS' login example is plausible but anecdotal. Its project originally planned both email and
Google sign-in. During implementation, the team requested email-only sign-in but did not update the
spec. A later agent comparing code with the plan could mistake the removed Google option for missing
work. The video does not provide prompts, model versions, repeated runs, controls, or raw outputs
for a separate ten-run test of this example.

## Instruction files should stay concise and specific

Anthropic documents `CLAUDE.md` as persistent context, not guaranteed configuration. User-level and
repository-root files load at launch, while files deeper in the tree may load when Claude works in
those directories. Claude attempts to follow them, but vague or conflicting rules may be ignored or
resolved unpredictably. An arbitrary specs directory is not automatically loaded merely because it
exists, although agents may discover it while searching.

Anthropic recommends keeping `CLAUDE.md` concise, under 200 lines as a guideline, and removing facts
that the agent can derive from code. A separate study of `AGENTS.md`-style context files found more
than 20% higher average inference cost without a significant task-success improvement in its tested
settings. That does not prove every long `CLAUDE.md` imposes exactly the same cost.

Codex has a related hierarchy for `AGENTS.md`. Both products can be influenced by stale persistent
instructions, but their measured rates differed. Saying agent choice makes no difference is too
strong.

## Memory and long context need qualified treatment

Claude Code can retain corrections and confirmed approaches in auto memory, but it does not write a
memory after every session. Memory has no fixed time-to-live and remains until the user or Claude
changes it. Only the first 200 lines or 25 KB of `MEMORY.md` load at startup; detailed topic files
can load on demand, and Claude is prompted to merge or remove stale entries.

Chroma's Context Rot work evaluated 18 models across controlled retrieval and question-answering
experiments. It found degradation as context increased, often in model-, task-, and
position-specific ways. It did not directly test failed attempts accumulated during coding sessions.
The extrapolation is reasonable but remains an extrapolation.

A fresh session can help when switching unrelated work. Anthropic also recommends writing a durable
spec and beginning implementation in a fresh session. Restarting is not sufficient by itself: useful
decisions, changed requirements, and the definition of done must first be persisted accurately.

## Use authority rules, not a universal source of truth

AI LABS proposes three ticket states: `completed`, `in progress`, and `not started`. These are
useful, but the narration also mentions dropped work without defining a `dropped` state. A workable
schema should include at least `cancelled`, `superseded`, and `blocked`, plus who changed the
status, when, and why.

The video then recommends treating code as authoritative unless a ticket is in progress. That rule
is safer when expressed as a conflict policy:

1. Detect disagreements among code, tests, plans, tickets, configuration, and runtime behavior.
2. Determine which source is designated as authoritative for this kind of decision.
3. Check dates, versions, status, owners, and repository history.
4. Report the conflict with evidence.
5. Ask before changing behavior when intent remains ambiguous.

Code may be buggy, incomplete, behind an approved migration, or unable to encode business and
security intent. A plan may be current even when implementation is not. Tests may preserve an old
contract. Runtime behavior may depend on flags, databases, infrastructure, or external services. No
single source wins every conflict.

## Constrain scope without hiding serious risks

A persistent rule to avoid unrelated work directly addresses Google's eager-agent example. Agents
should not silently fix TODOs, refactor nearby modules, or add features outside the request. They
can report unrelated findings separately.

A rigid "touch nothing else" rule also needs an exception for critical security, correctness,
privacy, or data-loss risks. The safe response is to stop, explain the risk, and request authority,
not to modify unrelated systems silently.

Before building a request that changes an existing decision, an agent can compare it with current
plans and ask whether the change is intentional. If confirmed, update the relevant source of intent
before implementation. This would have prevented AI LABS' email-login code and login plan from
diverging.

## A sweep should produce evidence, not automatic cleanup

AI LABS proposes a Claude Code skill that scans for obsolete notes and plans, checks each against
the application and repository history, and reports findings before taking action. A second agent
reviews each claim without seeing the first agent's hypothesis. Human approval determines what is
updated, archived, or removed.

This resembles Google's cautious cleanup process, but the implementation and reported result are
proprietary and unevaluated. A second instance of the same model is not independent evidence. It may
share the first model's assumptions, source errors, and blind spots. The checker needs citations,
explicit criteria, and access to primary evidence.

Each proposed finding should include:

- the exact file, line, symbol, ticket, and revision;
- the allegedly obsolete claim and current conflicting evidence;
- relevant commits, owners, dates, and status changes;
- the reason it appears obsolete or merely conflicting;
- confidence and plausible counterevidence;
- the proposed action and its rollback path.

Use version control and backups, exclude secrets and generated or vendored trees, restrict write
permissions, and require review. A closed ticket alone must never authorize deletion.

## Archives and hooks are not a security boundary

The video suggests moving historical files into an archive and adding a `PreToolUse` hook that
blocks the agent from reading them. Claude Code hooks can deny tool calls, but a complete policy
must cover all relevant tools, shell commands, path aliases, symlinks, case behavior, and direct
file inclusion. Anthropic notes that direct `@file` inclusion can bypass `PreToolUse` because it is
not a tool call.

Inspect generated hooks before enabling them. They execute automatically and can block legitimate
work, expose paths or data, or run unsafe shell commands. An archive is an organizational aid, not a
confidentiality boundary, and historical material should remain discoverable to humans when needed.

## Practical operating policy

A conservative workflow combines the strongest parts of the evidence:

- keep persistent instructions short, versioned, dated, and owned;
- give plans and tickets explicit lifecycle states and supersession links;
- persist requirement changes before ending the session that made them;
- begin unrelated tasks, or implementation after durable planning, with clean context;
- prohibit silent scope expansion while allowing critical risks to be reported;
- make conflicts visible rather than choosing an authority blindly;
- use code and repository history as evidence, not universal truth;
- have cleanup agents propose cited, reversible changes;
- require human review for deletion, archival, hooks, and behavior changes;
- measure false positives, review cost, token use, latency, and regressions.

The video's central warning is sound: agents act on context more literally and at greater scale than
humans may expect. Its strongest evidence is specific, not universal. Google measured a narrow class
of TODO-driven detours; a separate preprint tested stale convention files; AI LABS supplied broader
workflow advice. Keeping those layers separate produces a useful policy without turning anecdote or
marketing into established fact.

## Sources

- Google Developers Blog, *Agent Distraction*.
  https://developers.googleblog.com/agent-distraction/
- Anthropic, *Manage Claude's memory*.
  https://docs.anthropic.com/en/docs/claude-code/memory
- Anthropic, *Manage context*.
  https://docs.anthropic.com/en/docs/claude-code/context-window
- Anthropic, *Hooks reference*.
  https://docs.anthropic.com/en/docs/claude-code/hooks
- Anthropic, *Best practices for Claude Code*.
  https://docs.anthropic.com/en/docs/claude-code/best-practices
- OpenAI, *Custom instructions with AGENTS.md*.
  https://developers.openai.com/codex/guides/agents-md
- Chroma Research, *Context Rot*.
  https://research.trychroma.com/context-rot
- *Stale Instruction Files Override the Code in Coding Agents*.
  https://arxiv.org/html/2610.30571
- *Evaluating AGENTS.md*.
  https://arxiv.org/html/2602.11988
