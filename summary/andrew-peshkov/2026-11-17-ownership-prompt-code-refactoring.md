---
title: Ownership Prompts Trade Cleaner Refactoring for More Scope and Cost
author: Andrew Peshkov
channel: Threads
url: https://www.threads.com/@and.all506/post/Df2GaEBG6-B
date: 2026-11-17 15:02
tags: ai, development, technology
---

# Ownership Prompts Trade Cleaner Refactoring for More Scope and Cost

[article](../../articles/andrew-peshkov/2026-11-17-ownership-prompt-code-refactoring.md)

Anthropic tested this sentence with Claude Fable 5.2:

> You are the owner and long-term maintainer of this codebase, and its design is up to you.

On small coding tasks, duplicated code was consolidated in fewer than 10% of runs without the
sentence and about 75% with it. The result measures consolidation behavior, not general architecture
cleanliness, correctness, or maintainability. Anthropic does not publish the evaluation's full
sample, scoring method, uncertainty, or independent replication.

## The caveats

The ownership prompt also produced substantial costs and side effects:

- output tokens rose by about 70–80%;
- the model made unrequested changes, often adding tests and documentation;
- some runs changed existing feature behavior;
- pull-request summaries often omitted small changes.

The token increase does not imply an identical increase in every user's total bill. Input tokens,
caching, tool use, effort, pricing, and task structure also affect cost.

Adding "No drive-by refactors, renames or cleanups" did not reliably narrow the instruction. The
model still consolidated duplicates in more than half of runs. Ownership and minimal scope are
conflicting signals; Anthropic recommends omitting ownership language when the user wants the code
changed as little as possible.

## Assessment of the thread

Andrew Peshkov accurately preserves the key percentages and points out that Simon Willison's quoted
excerpt ends before Anthropic's caveats. Willison links to the complete documentation and labels his
page as a quotation, so the excerpt is incomplete rather than presented as a full risk analysis.

The claim that default behavior creates duplicates and workarounds in more than 90% of cases is too
strong. Not consolidating existing duplication does not prove that a run created a new defect.

The thread's story that users had damaged open-source forks by placing the sentence in a global
configuration has no examples or repository evidence. It is a plausible warning, not a verified
incident series. "Owner mode" is prompt shorthand, not a formal Claude setting.
## Practical rule

Use ownership framing for deliberate maintenance where broad edits, higher token use, tests, and
architectural cleanup are acceptable. Avoid it as a global default for third-party repositories,
release branches, narrow patches, regulated systems, or tasks that require minimal changes.

Always inspect the raw Git diff, test existing behavior, review every touched file, and compare the
patch with the requested scope. The ownership sentence changes initiative and scope; it does not add
permissions, sandboxing, rollback, or reliable self-reporting.
