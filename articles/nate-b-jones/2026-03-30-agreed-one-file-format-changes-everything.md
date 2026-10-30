---
title: "Anthropic, OpenAI, and Microsoft Just Agreed on One File Format. It Changes Everything."
author: Nate Jones
channel: Nate B Jones
url: https://www.youtube.com/watch?v=0cVuMHaYEHE
date: 2026-03-30 00:00
tags: ai
---

# Anthropic, OpenAI, and Microsoft Just Agreed on One File Format

[summary](../../summary/nate-b-jones/2026-03-30-agreed-one-file-format-changes-everything.md)

Skills — markdown files that encode expertise for AI agents — have
gone from a personal productivity hack to cross-platform organizational
infrastructure in six months. Anthropic, OpenAI, and Microsoft now all
support the same format: a folder with a markdown file containing
metadata and methodology that any agent can read and act on.

## Four Shifts Since October

**1. Personal → Organizational.** In October 2025, a skill was
something you built for yourself. Now team and enterprise admins roll
out skills workplace-wide. They are version-controlled, available in
the sidebar, and callable inside Excel, PowerPoint, Claude, and
Copilot. An organization's methodology is no longer carried in
people's heads — it lives in agent-readable, human-readable files.

**2. Humans → Agents as callers.** Humans were the primary callers
of skills in October. Now the majority of skill invocations come from
agents, which can make hundreds of skill calls in a single run. Skills
need to be designed agent-first.

**3. Developer tool → Universal tool.** Skills are not limited to
code execution. They work for any domain — real estate operations,
financial analysis, client deliverables. A real estate GP known as
Texas Paintbrush on X built over 50,000 lines of skills across 50
repositories covering rent roll standardization, comps analysis, cash
flow handling, and team handoff protocols.

**4. Closed-source → Open standard.** Skills as markdown became a
cross-industry standard. Anthropic and Microsoft partner to bring
skills to Copilot. OpenAI supports them. People trade skills like
baseball cards because best practices are discoverable, not known —
the community learns together.

## Anatomy of an Effective Skill

A skill is a folder with one required file: `skill.md`. It has
metadata at the top and methodology below. That is it.

**Description** — where most skills fail. Bad: "helps with
competitive analysis." Good: names document types produced, includes
trigger phrases ("analyze our competitors"), states output format.
Technical gotcha: the description must stay on a single line — if a
formatter breaks it, Claude won't read the second line. Invest 80%
of your attention here.

**Methodology body** needs five things:

1. *Reasoning, not just steps* — frameworks, quality criteria,
   principles. Linear-only procedures break on unrecognized cases.
2. *Specified output format* — markdown, Excel, PDF, exact fields.
   "Produce a summary" is too vague.
3. *Explicit edge cases* — everything a human handles through common
   sense must be written down. Claude will not infer them.
4. *Examples* — a pattern-matching target in additional files in the
   skill folder.
5. *Keep it lean* — under 100–150 lines in the core file. Short
   skills that fire reliably outperform long ones with competing
   instructions.

## Agent-First Skill Design

When agents are the primary caller, failures are different. There may
be no human recovery loop if the agent gets it wrong. Four principles
for agent-first skills:

**Description as routing signal.** The description must contain
wording that matches the outcome the agent has been given. It is not
a label — it is a routing mechanism.

**Contracts, not suggestions.** Frame the output as a contract — an
API-style declaration of what the skill delivers and what it does
not. The agent needs to confidently choose the right skill.

**Composability.** Think end-to-end. The output of one skill must be
correct input for the next agent or sub-agent in the chain. Don't
optimize for a single output — optimize for handoffs.

**Hardwire what matters.** If behavior must be deterministic, use
scripts, not skills. Skills are plain English — agents will often
follow them but not always. Scripts guarantee execution.

## Quantitative Testing

Agent-driven skills need test suites. Run a basket of tests, quantify
results, change the skill (version it), and re-test. Wording in
skills triggers different parts of a transformer's latent space —
you may need three or four iterations to get the exact response
pattern you want, even with examples.

## Three Tiers of Team Skills

**Tier 1 — Standard skills.** Consistent across the organization:
brand voice, formatting rules, approved templates. Provisioned
widely through team and enterprise accounts.

**Tier 2 — Methodology skills.** How your team performs high-value
work: client deliverable structure, senior practitioner craft, the
things that take a new hire months to learn. These live in senior
practitioners' heads and need to get into shared repositories.

**Tier 3 — Personal workflow skills.** Under-the-desk tools for
day-to-day work. Tempting to keep on your laptop, but dangerous —
when you're on vacation or sick, nobody can use them. Think
systemically about access levels for expertise.

## Community Skills Repository

A new section of OpenBrain will serve as a practitioner skills
library organized by workflow type. Every skill will meet an agent
readability bar. Coverage includes competitive analysis, financial
model review, deal memo drafting, research synthesis, and meeting
synthesis. The goal is domain-specific skills for real problems —
not just developer starter packs.

## Skills Compound, Prompts Evaporate

Skills compound through two forces: industry investment in the
ecosystem and your own commitment to iterating. Each refinement
makes the skill better for future, smarter agents. Prompts are
excellent but ephemeral — they disappear from the conversation.
Skills persist in the repository and improve over time.

Simon Willison wrote in October that skills would be a bigger deal
than MCP. That may be right, but fluency needs to catch up. The
path from prompting to reusable, agent-readable skills is where
the compounding value lives.
