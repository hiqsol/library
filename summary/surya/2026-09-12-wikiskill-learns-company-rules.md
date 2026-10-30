---
title: "WikiSkill: Teaching an Agent Company Rules Without Fine-Tuning"
author: Surya
channel: AI with Surya
url: https://youtu.be/ewxQLr7IxzY?is=av4C77hghhzmppTX
date: 2026-09-12 00:00
tags: ai, development
---

# WikiSkill in Brief

[article](../../articles/surya/2026-09-12-wikiskill-learns-company-rules.md)

Surya presents a local reconstruction of Google's WikiSkill research framework.
It aims to learn unwritten company rules without changing the base model's weights.
## Core Idea
- Treat the agent like a new employee who learns from corrected work.
- Convert each useful lesson into a readable, external instruction playbook.
- Keep a lesson only when it improves results on unseen validation tasks.
- This is Surya's demo and interpretation, not an independent paper verification.
## Four-Role Loop
1. Worker/checker: do the task, compare with ground truth, and assign a score.
2. Note taker: identify what failed and infer a possible company-specific rule.
3. Playbook writer: make one focused change to the instruction file.
4. Strict manager: test the change and reject it unless the held-out score rises.

## Spreadsheet Demo
- The fictional sales data mixes dates, regions, capitalization, units, and returns.
- A local case means 6 units rather than the more usual 12.
- Returns use company-specific handling, including negative values in examples.
- The spec names columns and sorting but leaves key finance conventions unwritten.
- Without a loaded playbook, the day-one run fails despite spotting data problems.
- Surya supplies about 20 sheets: 10 for practice and 10 held out for testing.
- He reports a 70% baseline; one later proposal falls to 40% and is rejected.
- Iterations 3-6 fail after his account runs out of usage, not from a scored rule.
- On iteration 7, the candidate scores 10/10, or 100%, and is accepted.
- The same file and model then pass when the learned playbook is loaded.

## Compared With Other Methods
- RAG retrieves written knowledge; WikiSkill targets rules not yet documented.
- Fine-tuning changes weights; this loop edits an inspectable instruction file.
- Memory stores experience; WikiSkill adds scoring, validation, and rejection.
- These methods can coexist; the distinctive part is validated playbook editing.

## Deployment and Limits
- Best fit: repetitive work with stable, company-specific conventions.
- Examples include month-end cleanup and invoice-to-cost-center coding.
- Surya used ADK Web, Google's Agent Development Kit, prompts, and the paper.
- A captioned tool name sounds like "Anti-gravity" and may be mistranscribed.
- Real use needs trusted ground truth, held-out data, versioning, and rollback.
- It also needs human review, privacy controls, monitoring, and cost management.
- Ten validation sheets cannot prove robustness to rare cases or distribution shift.
- Surya's near-guarantee of fewer issues is an aspiration, not established fact.

## Source Caveat
Source: AI with Surya, 12:53, published 2026-09-12; captions are auto-generated.
Video: https://youtu.be/ewxQLr7IxzY?is=av4C77hghhzmppTX
Tags: `ai`, `development`
