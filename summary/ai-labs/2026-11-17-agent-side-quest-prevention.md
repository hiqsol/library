---
title: Preventing AI Coding Agents from Following Stale Instructions
author: AI LABS
channel: AI LABS
url: https://youtu.be/JhZB3spnuIY?si=9NFF6iXlqhr8LiPJ
date: 2026-11-17 17:31
tags: ai, development, technology
---

# Preventing AI Coding Agents from Following Stale Instructions

[article](../../articles/ai-labs/2026-11-17-agent-side-quest-prevention.md)

AI LABS argues that stale comments, plans, instructions, and memory can send coding agents on side
quests. Google measured one narrow form: inline `TODO(bug/...)` and `FIXME(bug/...)` references in
millions of file-reading sessions.

Google found 13% of sessions exposed an agent to such a reference. Agents acted in 6% of encounters;
83% of those actions were unprompted. Of those detours, 32% concerned fixed or verified tickets,
9% obsolete or won't-fix tickets, 2% duplicate or restricted tickets, and 57% open tickets. Within
the open group, 61% only investigated and 39% edited code.

They were associated with 70% more steps, 77% more tokens, and 105% more wait time. Google's
controls make the association informative, but the study was observational and specific to bug
references. It does not establish the cost of every stale spec, memory note, or long context.

Google's cleaner checked ticket, file, and repository history before proposing removal. Reviewers
accepted over 95% of changes, and thousands of obsolete references were removed over six months.
Google did not publish a before-and-after outcome study or release a Claude Code tool.

The video's nine-out-of-ten instruction-file result comes from a separate 2026 preprint. In 320 runs
on 40 synthetic Python projects, 90.1% of baseline choices followed stale instructions. A sentence
prioritizing existing code raised code-following to 91.4%. This supports that controlled convention
conflict, not a universal rule that code overrides every requirement.

Anthropic treats `CLAUDE.md` as persistent context, not guaranteed configuration. It recommends a
concise file, under 200 lines as a guideline, and removing facts derivable from code. Chroma found
context-related degradation across 18 models, but did not test accumulated coding failures directly.
Fresh sessions help only if current decisions and changed requirements are first persisted.

AI LABS recommends ticket status metadata, no silent scope expansion, plan checks before building,
and a review-first cleanup sweep. Status should include cancelled, superseded, and blocked work with
its owner, date, and reason.

"Code is the source of truth" is unsafe as a universal rule. Code may be buggy or incomplete, while
plans may be stale. Agents should detect conflicts among code, tests, plans, tickets,
configuration, runtime behavior, and product intent; inspect their history; then ask when authority
remains unclear.

A cleanup sweep should cite exact files, tickets, revisions, conflicting evidence, confidence, and
rollback steps. Closed tickets must not authorize automatic deletion. Human review, version control,
limited permissions, and reversible changes remain necessary. Generated hooks must be inspected, and
an archive should be treated as an organizational aid rather than a security boundary.

The evidence supports a focused policy: keep instructions concise, mark document lifecycle, persist
requirement changes, constrain scope, surface conflicts, and let agents propose evidence-backed
cleanup instead of modifying or deleting material autonomously.
