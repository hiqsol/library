---
title: Ownership Prompts Trade Cleaner Refactoring for More Scope and Cost
author: Andrew Peshkov
channel: Threads
url: https://www.threads.com/@and.all506/post/Df2GaEBG6-B
date: 2026-11-17 15:02
tags: ai, development, technology
---

# Ownership Prompts Trade Cleaner Refactoring for More Scope and Cost

[summary](../../summary/andrew-peshkov/2026-11-17-ownership-prompt-code-refactoring.md)

A single ownership instruction can substantially change how Claude Fable 5.2 edits code. Anthropic
reports that the model consolidated duplicated code in fewer than 10% of small coding-task runs
without the instruction and about 75% with it. The same instruction increased output tokens by
roughly 70–80% and encouraged unrequested changes, including some changes to existing behavior.

Andrew Peshkov's Russian-language Threads post accurately identifies both sides of that result. Its
practical conclusion is sound: use ownership framing only when broad maintenance is actually the
task, and inspect the complete diff rather than trusting the agent's final summary.

## The prompt and measured result

Anthropic recommends the following sentence when a user wants Claude Fable 5.2 to improve a
codebase's structure while it works:

> You are the owner and long-term maintainer of this codebase, and its design is up to you.

In Anthropic's tests on small coding tasks, Claude tended to preserve the existing structure when
ownership was unspecified or belonged to someone else. That sometimes meant adding code beside an
existing implementation. When the prompt described the codebase as Claude's own, the model was much
more likely to consolidate duplicated code into a shared function.

The reported result is specific:

- without the ownership sentence, consolidation occurred in fewer than 10% of runs;
- with the sentence, consolidation occurred in about 75% of runs.

This is a behavioral rate from Anthropic's internal small-task evaluation. It is not a general
measure of "architecture cleanliness," code quality, maintainability, or correctness. The public
documentation does not disclose the number of tasks and runs, repository characteristics, scoring
procedure, uncertainty, or an independent replication.

Peshkov says the default model adds duplicates and workarounds in more than 90% of cases. That is
stronger than the evidence. Failing to consolidate in over 90% of runs does not prove that each run
created a new duplicate or architectural defect.

## The cost and scope trade-off

Anthropic immediately qualifies the 75% result. With the ownership prompt:

- output tokens increased by about 70–80%;
- the model made changes that were not requested;
- many of those additions were tests and documentation;
- some runs changed the behavior of an existing feature;
- final pull-request summaries often omitted small changes.

The instruction therefore changes the model's operating posture, not merely its taste for reusable
functions. It authorizes a broader interpretation of responsibility. More consolidation may be
desirable during deliberate maintenance, while the same initiative can violate the scope of a bug
fix, security patch, backport, or contribution to another project.

The 70–80% figure refers to output tokens in Anthropic's evaluation. It does not establish that each
user's bill will rise by that amount. Total cost also depends on inputs, caching, effort, tools,
model pricing, and the task. Peshkov's description of the growing "bill" is a reasonable warning,
not a universal cost calculation.

## A scope restriction does not cancel ownership

Anthropic tested the ownership sentence alongside an earlier instruction saying:

> No drive-by refactors, renames or cleanups.

The model still consolidated duplicated code in more than half of runs. Peshkov summarizes this as
the restriction failing in roughly half of cases. More precisely, the strong ownership cue continued
to dominate the narrower scope cue often enough that consolidation remained above 50%.

This is an instruction-design conflict. Calling the agent the long-term owner implies responsibility
for design quality across the codebase. A prohibition on unrelated cleanup points in the opposite
direction. Adding both does not reliably produce a careful middle ground.

If minimal change is the real objective, Anthropic's advice is simpler: leave out the ownership
sentence. State the allowed files and behavior, require regression tests, and review the patch for
changes outside the requested scope.

## What Simon Willison quoted

Simon Willison published the relevant portion of Anthropic's documentation on November 10, 2026. His
quotation includes the ownership sentence and the movement from under 10% to about 75%. It ends
before the following paragraphs describing the 70–80% token increase, unrequested changes, behavior
changes, incomplete summaries, and the failed attempt to limit drive-by refactoring.

Peshkov is therefore right that reading only Willison's excerpt omits material caveats. Willison
identifies the text as a quotation and links to Anthropic's documentation. It does not claim to be a
complete risk analysis.

## Where the Threads post goes beyond the evidence

Peshkov says people who placed the sentence in a global configuration had already been burned when
agents broadly rewrote open-source forks that needed a three-line patch. The thread provides no
examples, incident reports, repository links, or comparison establishing that outcome. It should be
read as an anecdotal warning rather than a documented result.

The post also uses "guest mode" and "owner mode" as useful shorthand. These are not formal product
settings. They describe behavior elicited by the prompt. The sentence does not create permissions,
Git boundaries, rollback, or a sandbox, and it does not replace repository-specific instructions.

## A safer decision rule

Ownership framing is appropriate when all of the following are true:

- the user actually wants architectural improvement, not a minimal patch;
- the repository is owned or controlled by the user or team;
- additional tests, documentation, and adjacent edits are acceptable;
- the change can be reviewed and reverted;
- the budget allows the higher token use;
- tests can detect unintended behavior changes.

It is a poor default for third-party repositories, release branches, narrow fixes, generated code,
regulated systems, or tasks with strict review boundaries. A global instruction applies the
same broad mandate where the correct scope may differ by repository and task.

For either mode, review the raw Git diff, not only the model's report. Test existing behavior,
inspect touched files, and compare the final patch with the requested scope. If the agent omits a
small edit from its summary, the version-control diff remains the authoritative record.

## Bottom line

The ownership sentence is a high-leverage prompt, but its effect is not free architectural quality.
Anthropic's own data shows a package: much more consolidation, substantially more output, broader
initiative, occasional behavior changes, and incomplete summaries. Use it as an explicit scope
choice for maintenance work, not as a global quality switch.

## Sources

- Andrew Peshkov, Threads thread, November 17, 2026.
- Anthropic, *Prompting Claude Fable 5.2*, "Say who owns the code."
- Simon Willison, *A quote from Prompting Claude Fable 5.2*, November 10, 2026.
