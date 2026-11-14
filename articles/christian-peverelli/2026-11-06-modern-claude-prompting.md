---
title: Modern Claude Prompting Favors Clear Context and Verifiable Outcomes
author: Christian Peverelli
channel: Christian Peverelli
url: https://youtu.be/izSnNPynvps?is=Vfjl85N0MOjHEAAI
date: 2026-11-06 02:48
tags: ai, technology
---

# Modern Claude Prompting Favors Clear Context and Verifiable Outcomes

[summary](../../summary/christian-peverelli/2026-11-06-modern-claude-prompting.md)

Christian Peverelli argues that capable Claude models need less ceremonial prompting than older
models. His useful recommendation is not simply to make prompts short. It is to remove decorative
roles and brittle scaffolding while preserving the context, examples, constraints, and tests that
actually define good work.

The video's title promises a 100-fold improvement, and it repeatedly makes unmeasured claims about
quality and subscription value. Those are promotional claims, not benchmark results. The underlying
workflow is still practical when its scope and limits are made explicit.

## Replace ceremony with a direct brief

The older prompting pattern assigns an inflated persona, states a broad goal, and provides a long
procedure. Examples include "world-class copywriter with 20 years of experience" and an instruction
to create a "viral" LinkedIn post. Such language often adds no information about the desired output.

Peverelli recommends three essentials:

1. Ask for the result in plain English.
2. Add context that changes how the task should be performed.
3. Provide examples of good output when style or format matters.

His marketing example asks Claude to turn a transcript into ten LinkedIn posts for an accounting
firm, identifies the intended audience and its bookkeeping problem, and attaches three posts the
client liked. The examples provide a stronger style signal than an abstract adjective such as
"professional."

This does not mean that every short prompt is good or every long prompt is bad. Prompt length is a
poor proxy for quality. A complex contract review, data transformation, or software change may need
substantial requirements. The point is to remove tokens that do not constrain the result.

Role instructions also retain limited uses. A role can establish a domain lens, audience, or review
standard. Research on persona prompts does not show a universal quality gain, but it also does not
prove that every role degrades output. Empty prestige claims are the weaker practice.

## Let clarification expose missing requirements

The next recommendation is to say: "If anything is unclear, ask me specific questions." The model
might ask who the client is, what the client sells, what material it receives, or why customers
cancel. This turns prompting into iterative requirements discovery rather than an attempt to predict
every ambiguity in advance.

Anthropic's Claude Code guidance supports this approach for uncertain projects. It suggests having
Claude interview the user until it can write a specification, then working from a clear definition
of done. Agent guidance similarly places clarification and human judgment at meaningful checkpoints.

The instruction is not a guarantee. Models can fail to notice an ambiguity or make a confident but
wrong assumption. Users still need to state critical constraints and inspect questions for omitted
risks. Clarification is most useful when the task's target is unclear, not as mandatory ceremony for
simple requests.

## Define tests before generation

The strongest part of the video is its emphasis on objective acceptance criteria. For the LinkedIn
posts, Peverelli proposes checks such as:

- every quoted sentence must occur in the transcript;
- every number must be supported by the transcript;
- every post must remain below 150 words;
- the model must report pass or fail for every check and provide evidence.

These tests are better than "review your work" because they identify observable failure conditions.
The same principle applies to code builds, unit tests, spreadsheet reconciliation, source citations,
schemas, screenshots, and document checklists.

Anthropic recommends giving agents environmental feedback and executable pass/fail checks. Its
agent-pattern guidance also supports evaluator-optimizer loops when the criteria are clear and
iteration produces measurable improvement.

A model's self-check is not independent verification. It can overlook the same error twice, invent
supporting evidence, or choose tests its answer can easily pass. Consequential financial, legal,
medical, security, or compliance work still needs deterministic checks or qualified human review.

Peverelli also suggests placing the output in a fresh session and asking for criticism. A clean
context can reduce anchoring and expose missing assumptions. It remains the same model family, so
reviewer may reproduce the original mistake. A separate session is a critique technique, not proof.

## What Boris Cherny actually said

The video's opening refers to two October 6 posts by Boris Cherny. In the first, Cherny posted an
image labeled "Prompt." In a follow-up, he wrote that he was surprised people were surprised by how
he prompts Claude and that most tasks do not need excessive scaffolding or prescription.

A contemporaneous archived capture shows 1.4 million views on the follow-up, so that number is
supported. The video blends the original image post with the later explanation, but its central
attribution is substantially accurate.

Cherny's point is narrower than "every prompt template is dead." It concerns most tasks with current
models. Anthropic's own documentation still recommends clear instructions, ordered steps when order
matters, examples, XML structure where useful, and system roles. It simultaneously warns against
bloated, stale, and over-prescriptive instructions.

The evidence therefore supports selective structure: use only the structure that helps the model
understand or verify the task.

## Karpathy, models, and disputed attributions

The video attributes the phrase "my prompts are getting shorter and dumber" to Andrej Karpathy and
says excessive requirements can constrain a model. Karpathy joined Anthropic in May 2026 to build a
pretraining research team, so his Anthropic affiliation is real. No primary source for the exact
quoted wording was located, and it should be treated as an unverified attribution.

Karpathy's documented teaching is more nuanced. His earlier material recommends reusable prompts,
structured sections, and few-shot examples when they improve results. That is compatible with
removing empty ceremony but not with a universal rule that shorter is always better.

The named Claude models are real. Anthropic's catalog lists Opus 5.5, Fable 5.2, and Sonnet 5.5.
The transcript's abbreviated "Fable" and "Sonnet" omit versions but are not
invented names.

The claim that Anthropic deleted more than 80% of Claude's own instructions in July 2026 without a
measurable coding loss could not be verified in a public Anthropic source. Anthropic does advise
keeping `CLAUDE.md` concise, removing facts inferable from the repository, and deleting stale habits
such as repeated all-caps warnings. That qualitative guidance does not establish the video's 80%
number, date, scope, or evaluation result.

## Keep persistent instructions small but sufficient

`CLAUDE.md` is a Claude Code instruction file, not a universal feature of ordinary Claude chats.
Peverelli recommends removing redundant rules, repeated `IMPORTANT`, `NEVER`, and `ALWAYS` warnings,
and procedures the model no longer needs.

This is sound when simplification removes conflicts and stale instructions. It becomes harmful if it
removes repository commands, architectural constraints, security boundaries, testing requirements,
or facts that cannot be inferred reliably. A concise instruction file should still contain the
information required to work safely in that specific project.

Memory features are also product- and account-dependent. They should not be assumed to replace
project documentation, explicit task requirements, or durable source material.

## Match effort to risk and autonomy

The video presents five effort levels:

- low for ideas the user will inspect immediately;
- medium for ordinary work with a known target;
- high for tasks requiring verification or handling edge cases;
- extra high for long work that should proceed with less supervision;
- max for difficult analysis intended to run with minimal user involvement.

Examples range from generating email subject lines to reconciling twelve months of invoices and
checking contractual risks against past disputes. The useful principle is to spend more computation
and review where errors are costly or the user will be less involved.

Effort controls, prices, and behavior are interface- and version-specific. Higher effort does not
remove the need for review. It may affect latency, usage, assumptions, and quality. The video's
promise of three times more work from a subscription has no supplied measurement.

## Context management is potentially lossy

The final section promotes third-party "mods" for choosing effort, monitoring context, handing work
to a new chat, and warning when a conversation becomes cold. A fresh session can improve focus when
irrelevant history dominates and reduce repeated context processing.

The exact claims need caution. The video recommends handoff around 80–85% context usage, says chats
remain active for 60 minutes, and implies a handoff preserves all context. No product documentation
was supplied for those thresholds or savings. A summary-based handoff can omit details.

Subscription credits and API token billing are different systems. A credit-saving technique for one
Claude interface may not apply to API users or another plan. The promoted tools lead to the
presenter's free community and paid program, which matters when evaluating performance claims.

## A calibrated workflow

A defensible version of the video's method is:

1. State the requested outcome directly.
2. Supply only relevant context, data, constraints, and strong examples.
3. Ask targeted clarification questions when requirements are genuinely incomplete.
4. Establish objective acceptance tests before execution.
5. Match effort and autonomy to complexity and consequences.
6. Run deterministic checks and obtain human review for high-stakes work.
7. Use a fresh critic when useful, without treating it as independent proof.
8. Keep persistent instructions current, concise, and sufficient for safe operation.
9. Start a clean context when old conversation history becomes distracting.
10. Treat context handoffs as lossy unless the required facts are checked explicitly.

Modern models can often infer more from less scaffolding. They cannot infer information never
provided, ensure that assumptions match the user's intent, or validate themselves reliably in every
domain. Better prompting is high-signal communication paired with evidence that work is complete.

## Sources

- Boris Cherny, archived October 6 posts and October 13 view-count capture.
- Anthropic, *Prompting best practices*.
- Anthropic, *Claude Code best practices*.
- Anthropic, *Effective context engineering for AI agents*.
- Anthropic, *Building effective agents*.
- Anthropic, Claude models overview.
- Zheng et al., *Personas in System Prompts Do Not Improve Performances*.
- Karpathy, *How I use LLMs*.
