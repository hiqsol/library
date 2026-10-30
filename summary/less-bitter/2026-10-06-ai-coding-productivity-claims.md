---
title: "The Big Lie About AI Coding: What the Evidence Actually Supports"
author: Less Bitter
channel: Less Bitter
url: https://youtu.be/DzSS9R8t2Ao?is=ofGkfLhNDhnPq1H7
date: 2026-10-06 19:09
tags: ai, development
---

# The Big Lie About AI Coding: What the Evidence Actually Supports

[article](../../articles/less-bitter/2026-10-06-ai-coding-productivity-claims.md)

Less Bitter argues that a “Markdown Industrial Complex” turns AI-coding instruction files into
hype. The strongest point is correct: stars, views, bookmarks, tokens, commits, and pull requests
measure attention or activity, not delivery, quality, customer value, or business outcomes.

The claim that “there’s no skill in AI coding” is sensational. Controlled evidence shows that
procedures, interfaces, repository context, and verification scaffolds can help, do nothing, or
hurt depending on the task, model, and harness. Each intervention needs testing.

The video gets gstack’s history wrong. GitHub records its creation on 11 March 2026, not February.
Anthropic introduced Agent Skills and `SKILL.md` in October 2025 and made the format an open
standard in December. gstack became popular, but it did not invent the pattern.

Lauren Tan’s post claims 2,500 production PRs in one month, while her embedded talk says 2,000.
Neither figure is audited. Her talk contains no 10–12-hours-per-day statement. She instead credits
verification tools, feature maps, static analysis, CI, architecture, telemetry, and PStack skills.

At 2,500 PRs over 30 twelve-hour days, the rate is one every 8.64 minutes; over 22 such workdays,
one every 6.34 minutes. This does not disprove the claim, but makes task size, automation, review,
merge policy, and the meaning of “to production” essential context.

Dax’s warning that new models obsolete custom workflows is practitioner opinion, not a controlled
result. Matt Pocock’s repository-review prompt is not evaluated. DHH’s Campfire ports cannot rank
Elixir, Go, or Rust because their database, queue, CSRF, and caching behavior differed.

Controlled evidence is mixed. A 95-developer Copilot experiment reported 55.8% faster completion
on one JavaScript task. A 202-person Python exercise found higher test success and small review
gains. Both were narrow tasks and do not establish production-wide effects.

SkillsBench found curated skills raised average pass rate by 16.2 points, but software engineering
gained 4.5 points and 16 of 84 tasks worsened. Generic AGENTS.md context brought no general gain
and over 20% more inference cost. A fixed-model SWE-agent interface improved results by 10.7 points.

Individual throughput is also heterogeneous. A 4,867-developer field study estimated 26.08% more
completed weekly tasks among Copilot users. METR found 16 experienced maintainers took 19% longer
with early-2025 AI tools. Effects vary by task, expertise, repository, model, and self-selection.

The video reports no delivery lead time, failure rate, recovery time, rework, incidents, revenue,
retention, customer satisfaction, or support burden. DORA’s survey associations are not causal.
A 47-person study also found less secure code in four of five AI-assisted security tasks.

The defensible conclusion is narrower than the title: viral AI-coding content often promotes
activity metrics and generic context without evidence of delivery, quality, or value. Teams should
test representative work and measure human time, success, cost, defects, stability, and outcomes.
