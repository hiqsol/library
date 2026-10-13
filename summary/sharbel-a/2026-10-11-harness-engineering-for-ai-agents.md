---
title: "Agent Skills: Reusable Workflows Without More Agents"
author: Sharbel A.
channel: Sharbel A.
url: https://youtu.be/VxGIopUQVKo?si=oxzxOxmcmDAmugaO
date: 2026-10-11 16:00
tags: ai, development, technology
---

# Agent Skills: Reusable Workflows Without More Agents

Sharbel A. explains Agent Skills: reusable folders that teach a general-purpose agent how to
perform a specific workflow. A minimal skill contains `SKILL.md` with a required name, description,
and Markdown instructions. More capable packages may add scripts, references, assets, and examples.

The description helps the agent decide when to activate the skill. It initially sees compact
metadata, then loads the full instructions and supporting files only when needed. This progressive
disclosure saves context, although vague or overlapping descriptions can still trigger incorrectly.

Anthropic introduced the format in 2025 and released it as an open standard. The video's headline
is overstated: Anthropic recommended skills instead of fragmented custom agents for some procedures;
it did not announce that its engineers had stopped building agents.

Skills, agents, and connectors solve different problems. Skills package procedures and expertise;
agents provide execution loops, tools, state, and permissions; MCP connectors provide live service
access. Separate agents still make sense for different identities, models, security boundaries,
memories, environments, or orchestration roles.

The demonstration builds a YouTube-research skill that filters recent videos by views and a vendor
“outlier score,” then extracts recurring topics and title formats. This shows procedural reuse, not
predictive validity. The thresholds are personal heuristics, and the demo does not disclose a
reproducible input set or test whether its suggested titles later perform well.

Claude can interview a user and draft a skill, but the result is only a first version. Authors must
check activation rules, review all files, test positive and negative cases, compare against the base
agent, record failures, and version changes. Clear instructions cannot rescue an invalid workflow.

Claude Cowork can also propose a skill from a screen recording on supported Mac plans. It does not
perfectly “learn every step.” Hidden state, credentials, timing, UI changes, and human judgment may
be missing, so users must inspect and test the proposal. Sensitive files, conversations, and secrets
should not be visible during recording.

The common standard improves portability across clients such as Claude, Codex, Cursor, and Hermes,
but does not guarantee identical execution. Tool names, permissions, packages, operating systems,
placeholders, connectors, and experimental fields differ. Each target environment requires testing.

Third-party skills are executable supply-chain artifacts. Reading `SKILL.md` or asking another agent
to scan it is insufficient. Review every bundled file and dependency, pin a version, test without
secrets, deny unnecessary network access, grant minimum permissions, and examine every update.

Skills are durable files, not permanent knowledge. APIs, interfaces, models, dependencies, and
policies change. Useful skills need owners, compatibility declarations, examples, evaluations,
version history, rollback paths, and periodic retirement or revision.

The durable lesson is to package repeated expertise as inspectable and versioned capability instead
of duplicating prompts or agent definitions. Skills can make a general agent more consistent, but
they still require maintenance, evaluation, compatibility testing, and supply-chain security.
