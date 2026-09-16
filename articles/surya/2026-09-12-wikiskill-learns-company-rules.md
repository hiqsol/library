---
title: "WikiSkill: Teaching an Agent Company Rules Without Fine-Tuning"
author: Surya
channel: AI with Surya
url: https://youtu.be/ewxQLr7IxzY?is=av4C77hghhzmppTX
date: 2026-09-12 00:00
tags: ai, development
---

# WikiSkill: Teaching an Agent Company Rules Without Fine-Tuning

Surya presents WikiSkill as a Google Research framework for agents that learn local working
rules from mistakes. His video does not independently reproduce or audit the research paper.
Instead, it walks through his own laptop implementation and a synthetic spreadsheet demo.

The central analogy is a capable new employee entering an unfamiliar company. The employee
may know spreadsheets but still mishandle conventions that exist only in colleagues' heads.
At one company, a case might mean 6 units rather than the usual 12. Returns might need to be
recorded as negative values. General intelligence does not reveal such local conventions.

WikiSkill is meant to turn corrections into a readable operating playbook. The base model is
not retrained or fine-tuned. An agent attempts work, compares its result with an expected
answer, records what went wrong, proposes an instruction change, and retains that change only
when it improves performance on work that was not used to derive it.

## The Four-Role Learning Loop

Surya describes the design as three coworkers and one strict manager. In his reconstruction,
the roles form a repeated propose-and-validate loop.

1. **Worker and checker:** The worker reads a messy file, writes and runs a small cleaning
   script, and saves a normalized file. A checker compares that output with correct numbers
   and assigns a score. The checker supplies the error signal used by later roles.
2. **Note taker:** When the worker is wrong, this role compares the produced answer with the
   expected one and writes a focused account of the failure and the rule it may imply.
3. **Playbook writer:** This role converts the note into one proposed change to a plain-English
   instruction file. Keeping each proposal narrow makes its effect easier to test.
4. **Strict manager:** The manager tests the changed playbook on 10 spreadsheets the worker
   did not use for practice. It accepts the change only if the held-out score improves;
   otherwise, it discards the change.

The held-out check is the critical guardrail in the explanation. A plausible lesson can merely
memorize one example or damage another case. Testing it against unseen sheets asks whether it
generalizes. This is closer to controlled instruction editing than unrestricted self-memory.

The resulting playbook is inspectable English rather than a hidden weight update. A person can
review what the agent believes, when a rule applies, and when it should not apply. Surya argues
that this readability is useful for company-specific processes, though it does not by itself
prove that every accepted rule is safe or complete.

## The Spreadsheet Demonstration

Surya built a local application to clean a fictional company's monthly sales exports. The data
contains dates, regions, stores, order IDs, product types, units, and revenue. It deliberately
mixes date formats, leaves gaps, varies region spellings, changes capitalization, and expresses
units with forms such as cases or abbreviations such as `CS`.

The finance specification identifies required columns and asks for sorting by date, region,
and order ID. It also says to apply standard finance conventions for dates, units, returns,
and duplicate orders. The problem is that those "standard" conventions are not fully written
down. Correct examples and feedback therefore carry information absent from the initial spec.

The first run uses no learned skill, which Surya likens to day one on the job. The worker can
spot symptoms such as missing regions, but it lacks the company rules needed to resolve them.
The run fails because no playbook is loaded.

Surya then supplies about 20 spreadsheets. According to his description, 10 are practice
sheets and 10 are held out for manager testing. The loop repeatedly edits the instruction file
while the manager evaluates each proposal against the unseen set.

His scoreboard begins with a reported 70% baseline. A later proposal scores 40% and is
rejected; the following proposal is also rejected. Iterations 3 through 6 show failures because
his account ran out of usage, which he attributes to his setup rather than the framework. At
iteration 7, the candidate reaches 10 out of 10, or 100%, and the manager accepts it.

The final playbook is readable in English. Surya says it combines supplied finance rules with
rules inferred through practice. He reruns the same file with the same model, now loading the
learned skill. In his demo, the run passes and all rows match his expected ground truth,
including treatment of a returned item and the signs of revenue values.

These are results Surya reports from a made-up local example, not independently verified
benchmark results. The video does not establish that the same improvement will hold across
other models, companies, datasets, or operational conditions.

## How It Differs From RAG, Fine-Tuning, and Memory

Surya contrasts WikiSkill with three familiar approaches:

- **RAG** retrieves existing documents. It cannot directly retrieve a convention that nobody
  has documented. WikiSkill instead tries to infer such a convention from corrected examples
  and then creates the missing document.
- **Fine-tuning** changes model weights and can take substantial time. Its learned behavior is
  not directly readable as a list of rules. WikiSkill leaves the model unchanged and updates
  an external instruction artifact.
- **Memory** can store prior events or observations, but ordinary memory does not necessarily
  test whether a remembered lesson improves future performance. WikiSkill adds explicit
  scoring, held-out validation, and rejection of harmful proposals.

The boundaries are not absolute. A WikiSkill system could use retrieval to load its playbook,
memory to retain episodes, or a fine-tuned model as its worker. Its distinguishing feature in
Surya's account is the validated loop that converts errors into an editable, auditable guide.

## Where Surya Thinks It Fits

The proposed fit is repetitive, long-running work where errors arise from organization-specific
conventions rather than missing world knowledge. Surya names month-end close, where each
store export has quirks, and invoice coding, where only accounts-payable staff may know the
right cost center. Similar candidates include recurring data cleanup, operational reconciliation,
and other workflows with stable scoring and examples of correct output.

For deployment, a team would need a worker toolchain, a checker with trustworthy ground truth,
a versioned playbook, a training set, a genuinely held-out validation set, acceptance criteria,
and monitoring. Human review remains important for sensitive workflows and policy changes.
The framework is more plausible where correctness can be measured than where evaluation is
subjective, delayed, or contested.

## How the Demo Was Built

Surya shows ADK Web as the chat interface to his agent and says the application runs on
Google's Agent Development Kit. He says he described the experiment in plain English to a tool
transcribed as "Anti-gravity," uploaded the paper, supplied prompts, and had it build the app.
He also mentions a similar community implementation and says he will link it and the paper.
The exact tool name is uncertain because this account comes from auto-generated captions.

## Limits and Practical Risks

The demo depends on known correct outputs. If the checker or ground truth is wrong, the loop
can reward the wrong lesson. Ten held-out sheets are a useful demonstration but may not cover
rare cases, distribution shifts, interactions among rules, or adversarial inputs.

Repeated agent calls add time and cost. Surya himself notes that learning can take time, and
his run encountered an account-usage interruption. Rules may conflict, grow stale, or become
too specific. A score increase can also hide regressions outside the measured test set.

A system that writes its own instructions needs permissions, version history, rollback,
segregated validation data, and human approval for high-impact changes. Sensitive examples
also require access controls and privacy review. The manager is another agent in the demo, so
calling the process "self-verifying" should not be confused with independent assurance.

Surya says the automation can "almost guarantee" minimal long-run issues. That is his
aspiration, not a demonstrated guarantee. The evidence shown supports a narrower conclusion:
in his reconstruction, a controlled spreadsheet task improved after iterative, held-out
playbook validation without changing model weights.

## Source Note

This article covers Surya's 12:53 video, *Google WikiSkill Teaches Itself Your Company's Rules
(No Fine-Tuning!)*, published on September 12, 2026 by AI with Surya:
https://youtu.be/ewxQLr7IxzY?is=av4C77hghhzmppTX

It is based on fallible English auto-captions. Ambiguous names and demo details may be
mis-transcribed. Claims about the framework and observed results are attributed to Surya and
should be checked against the paper, code, and independent evaluations before operational use.

Tags: `ai`, `development`
