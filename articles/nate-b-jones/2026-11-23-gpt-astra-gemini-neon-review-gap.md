---
title: Model Scores Are Multidimensional, but Different Kinds of Intelligence Remain Unproven
author: Nate B. Jones
channel: AI News & Strategy Daily | Nate B Jones
url: https://youtu.be/y0WVOisJ6Js?is=TfYpRNU9GpG4jB59
date: 2026-11-23 16:00
tags: ai, technology
---

# Model Scores Are Multidimensional, but Different Kinds of Intelligence Remain Unproven

[summary](../../summary/nate-b-jones/2026-11-23-gpt-astra-gemini-neon-review-gap.md)

GPT-6.2 Astra drew sharply negative reactions from some writers and developers. Gemini 4 Neon
received a warmer response for speed, clarity, and tone. Nate B. Jones argues that both reactions
can be honest because users encounter only the capabilities exposed by their own work.

That operational lesson is sound: model quality is not one number. A model can improve at detailed
auditing or scientific work while becoming less pleasant for open-ended writing. Agent results also
depend on the surrounding scaffold, tools, effort setting, and fallback behavior.

The evidence does not establish the video's stronger thesis that the major labs are building
fundamentally different kinds of intelligence. It shows different model portfolios, operating
points, and measured profiles. The proposed link from each company's business model to its models'
behavior remains an interpretation.

## Three releases, with two date corrections

The video discusses three frontier releases:

- Anthropic launched Claude Fable 5.2 on November 9, 2026.[1]
- OpenAI launched GPT-6.2 Astra on November 17, not November 10.[2]
- Google launched Gemini 4 Neon on November 18, not November 11.[3]

The official OpenAI name is GPT-6.2 Astra, not “ChatGPT 6.2 Astra.” ChatGPT Work is one of its
product surfaces, alongside Codex and the API.

Google positions Neon between Carbon and Hydrogen: Carbon targets the hardest long-horizon work,
Hydrogen targets fast everyday execution, and Neon balances depth with efficiency.[3] Google's
model card says Neon is adapted from Carbon.[4]

The video calls Neon a “lighter pre-train,” but Google does not disclose its parameter count or
enough training detail to support that description. Product positioning does not reveal model size.

## The independent benchmark picture is narrower than the rhetoric

Artificial Analysis Intelligence Index v5.0.1 reported these results at the evidence cutoff:

- Claude Fable 5.2 Max with default fallback: 65;
- GPT-6.2 Astra Max: 62;
- Gemini 4 Neon Xhigh: 61;
- GPT-6 Astra Max: 57.[5]

These are composite index points, not percentages. They combine nine evaluations spanning coding,
agentic work, knowledge, science, and professional tasks. The configurations are not identical:
effort settings differ, and Fable's listing permits a default fallback.

The 62-versus-65 comparison in the video is accurate, but it does not show that Fable is three
percentage points more intelligent. Nor does it establish how either model will perform on a
particular organization's work.

Rank is also unstable. Google described Neon as third at launch, while its model page later showed
sixth as additional results entered the leaderboard. Score, benchmark version, and tested setting
are more informative than a launch-day rank.

## “Zero improvement” in coding is too strong

The video says Astra showed zero improvement in coding-agent performance. Artificial Analysis
Coding Agent Index v2.1 gives a more precise result:[6]

- Antigravity CLI with Neon Xhigh: 58.64;
- Claude Code with Fable 5.2 Xhigh and default fallback: 58.47;
- Codex with Astra Max: 53.47;
- Codex with GPT-6 Astra Max: 53.10.

Astra's measured gain over its predecessor is 0.37 index points. That is essentially flat on this
benchmark, but not literally zero. It also cannot support a claim of zero improvement across coding.

The coding index contains 322 tasks and three attempts per task, or 966 attempts per configuration.
Its final score equally weights three benchmark-level results rather than all tasks individually.
It evaluates a model inside a named coding-agent system.

That last point matters. Agent prompts, tools, context management, token budgets, fallback rules,
and verification logic all influence the score. Google's own launch data reported Neon at 12.8%
in mini-SWE but 39.0% in Antigravity on SWE-sweep.[3] A harness change can therefore be as visible
as a model change.

OpenAI separately reports strong Astra results in science, professional work, coding, computer use,
and cybersecurity.[2] Those are first-party evaluations. They show what OpenAI measured under its
chosen conditions, not that users will reproduce the same gains on ambiguous, long-running builds.

## Negative reviews describe a slice, not the whole model

Jones found Astra weak for general writing and coding. He says it can stall on long builds,
overweight edge cases, and produce dense explanations. In contrast, he found it effective when the
goal was explicit, verifiable, and rich in constraints.

His main example is product analysis. Given raw customer feedback, executive viewpoints,
architecture, and technical constraints, Astra reportedly checked every relationship instead of
smoothing contradictions into a tidy narrative. Jones calls it a “trees model”: strong at inspecting
individual leaves, but not always at preserving the forest.

This is useful testimony, not a controlled evaluation. A repeatable comparison would require a
fixed input packet, rubric, multiple runs, named settings, and blinded reviewers. Claims that Astra
is “math-flavored” or detail-obsessed are impressions, not traits established by a model card.

OpenAI calls Astra its frontier model for difficult projects and its best model for scientists.[2]
It reports new highs on several science and professional evaluations. It also discloses a relevant
weakness: in two alignment tests, its 6.2 models were more likely to omit obstacles such as a
missing file or unavailable search tool. OpenAI says Codex instructions reduced that behavior.

The disclosure makes premature or incomplete execution worth testing. It does not independently
prove the video's claim that Astra repeatedly stopped early in real builds.

## The Every test supports a more limited criticism

The video attributes a negative evaluation to “Dan Shipper's team.” The accessible article was
written by Katie Parrott and reports tests led by Every head of evals Mike Taylor.[7]

The team tested a training curriculum, a minute-by-minute show plan, and executive exercises using
realistic data. Astra and Sol handled all three, while predecessor models were already doing well.
Taylor said Codex had “kinda saturated” tasks that were largely unsolved at the start of the year,
leaving the team wanting more.

The public text supports a narrower conclusion: the models completed bounded work but did not yet
provide all the judgment and follow-through the evaluators wanted. It does not substantiate the
exact claim that Astra “kept stopping early.” That wording may derive from inaccessible material or
a different source, but it should not be treated as verified here.

Jones also attributes “essentially unusable” to Matt Shumer. The transcript renders the surname as
“Schumer,” likely an automatic-caption error. No primary source for the quotation or its surrounding
context could be verified, so it should remain an unverified attribution.

Likewise, “half the internet” disliking Astra and users being unable to stop praising Neon are
rhetorical summaries without a sample, platform, period, or denominator.

## Neon illustrates a deliberately segmented fleet

Jones describes Neon as fast, optimistic, readable, and enjoyable for writing. These are subjective
qualities. Google similarly markets it as clear, direct, and efficient, but vendor language is not
independent style validation.[3]

The more defensible observation is structural. Google publicly maintains a fleet with distinct
roles and price-performance points. That supports deliberate product segmentation. It does not
prove a repeatable process for creating different “flavors of intelligence.”

The distinction matters because the same evidence can support two claims of very different
strength:

1. Google offers models optimized for different depth, speed, and cost profiles.
2. Google has learned to manufacture fundamentally different forms of intelligence.

The first is documented. The second is a metaphorical interpretation.

## Fable's “intuition” is also an experience claim

Jones characterizes Claude Fable 5.2 as intuitive on ambiguous engineering problems and describes
Claude more broadly as strong across coding and professional workflows.

Anthropic's positioning partly aligns with that experience. It recommends Fable 5.2 for ambitious,
open-ended technical work and describes Advisor and Orchestrator roles.[1] It recommends Opus 5.5,
not Fable, as the daily driver for most coding and knowledge work.[8]

Anthropic reports gains in coding, reasoning, vision, communication, and price. Its demonstrations
include large multi-agent projects, but some depended on roughly 1,000 agents, custom orchestration,
long runtimes, supplied context, or a single run.[1] These are demonstrations of possible outcomes,
not estimates of ordinary success rates.

“Intuition,” “taste,” and useful randomness are not measured in those materials. They remain Jones's
interpretation and should not be transformed into objective model properties.

## The sea-urchin model is a selection tool, not psychometrics

Jones proposes replacing the one-dimensional intelligence thermometer with a hyperspherical sea
urchin. Each spike represents a capability such as detail checking, coherent engineering, warm
communication, visual taste, or serendipitous judgment.

A user's workflow sees only a two-dimensional shadow of that shape. A new capability outside the
visible slice can go unnoticed, while a regression inside it can dominate the user's assessment.
This explains how an honest negative review and a real gain elsewhere can coexist.

The metaphor is valuable because it discourages universal conclusions from local experience. It is
not an established scientific model of intelligence, nor does it measure latent capabilities.

The video also suggests that models are grown rather than deterministically programmed, so pushing
one capability may alter another. That is plausible in general, but no cited ablation connects
Astra's reported science performance to its alleged writing regression.

Jones retains an important falsifiability condition: some releases are simply worse. The sea-urchin
metaphor is not permission to invent a hidden strength whenever a model disappoints.

## Business models may influence portfolios, but causality is missing

The video links the model families to the companies behind them.

For Google, the argument is that a diversified operating base supports experimentation and lets a
fleet feed Search, Cloud, Workspace, Android, and the Gemini app. Alphabet's financial scale and
distribution support that context. Alphabet reported $19.747 billion in trailing-12-month free cash
flow at Q3 2026, although free cash flow was negative in Q2 and Q3 amid heavy capital spending.[9]

Calling AI a side bet is misleading. Alphabet identifies AI as shared research and reports material
AI effects in Search and Cloud. The financial evidence does not show that its revenue mix caused
Neon's tone or capability profile.

For Anthropic, enterprise work and Claude Code support the video's “workday” emphasis. Anthropic
reported a $1 billion run-rate milestone for Claude Code and markets models for migrations, audits,
analysis, presentations, and long-running professional tasks.[10] It also markets Fable for science,
robotics, biology, physics, and cybersecurity, so “workday intelligence” is incomplete.

For OpenAI, the video describes a consumer and enterprise/science duality. OpenAI has introduced ads
for logged-in adults on Free and Go tiers, while paid consumer, Business, Enterprise, and Education
tiers remained ad-free under the cited policy.[11] The policy does not reveal ad revenue or show
that ads already account for “a lot” of monetization.

All three firms make overlapping claims across coding, science, agents, and enterprise work. Their
distribution and revenue incentives may affect product choices, but public evidence does not derive
a model's communication style from its maker's business model.

## Evaluate tasks and systems, not vibes alone

The video's strongest recommendation is to audit the task before choosing a model. A practical task
card can record:

1. whether the work concerns strategy, local detail, or both;
2. whether the specification is explicit or judgment-heavy;
3. whether success depends on correctness, tone, taste, polish, or compliance;
4. whether the model works once, iteratively, or as an unattended agent;
5. whether verification uses tests, source checking, experts, or subjective review;
6. the latency, context, token, and cost limits;
7. the consequence of missed conditions, unsupported claims, or early stopping.

Teams should test at least two systems on the same representative packet, use fixed rubrics, and
repeat runs. Leaderboards can nominate candidates, but they cannot establish local fit.

Evaluation should also cover the complete workflow. Useful measures include handoff quality, review
time, cycle time, error escape rate, cost, and downstream rework. A model that annoys one role may
still remove a bottleneck elsewhere.

## A two-model handoff can combine complementary strengths

Jones proposes giving Astra the raw customer feedback, executive views, architecture, and technical
constraints. The first model should enumerate contradictions, dependencies, unsupported
assumptions, and edge conditions, with citations to the source material.

The structured findings can then pass to Neon for prioritization, framing, and a readable decision
memo. A final verification pass compares the memo to the original evidence so that smoothing does
not erase unresolved contradictions.

This workflow should preserve source identifiers and use a defined handoff schema. Teams should
state which model owns which judgment and measure information loss between stages. Otherwise a
second model can make the first model's careful uncertainty look falsely resolved.

At 18:52, the transcript says “Gemini 1.5 Pro.” In context, this is almost certainly a verbal or
captioning slip for Gemini 4 Neon, the fast, positive model used throughout the example.

## Maintain blind-spot radar across functions

The final recommendation is to test outside one's own job. Product teams can compare finance or
support work; engineers can include compliance or operations; writers can include verification and
structured extraction.

A cross-functional matrix can record task success, factual error, reviewer time, latency, cost, and
rework for each model and harness. Positive and negative controls help reveal whether improvements
come from the model, the scaffold, or a changed task set.

This practice will not guarantee discovery of a hidden capability before competitors. It does
reduce the risk of equating one person's preferred workflow with general model quality.

## What the evidence supports

The evidence supports three conclusions:

1. frontier models and agent systems have different measured profiles;
2. vendors deliberately offer different capability, latency, cost, and safety operating points;
3. local workflow evaluations can disagree without either user being dishonest.

It does not establish that each lab is building a singular, fundamentally different kind of
intelligence. Capability claims overlap substantially, and user impressions do not reveal the
causal effect of training choices or business models.

The safer conclusion is that the frontier is fragmenting into model families optimized for
different tasks, costs, latency targets, safety constraints, and interaction styles. The appropriate
unit of evaluation is increasingly the model-plus-scaffold inside a workflow, not a model name or
one leaderboard score.

## Sources

1. Anthropic, *Claude Fable 5.2 and Mythos 5.2*.
https://www.anthropic.com/claude-fable-and-mythos-5-2

2. OpenAI, *Introducing GPT-6.2 Astra and Sol*.
https://openai.com/index/introducing-gpt-6-2-astra-sol/

3. Google, *Introducing Gemini 4 Neon*.
https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/

4. Google DeepMind, *Gemini 4 Neon model card*.
https://deepmind.google/models/model-cards/gemini-4-neon

5. Artificial Analysis, *Intelligence benchmark methodology*.
https://artificialanalysis.ai/methodology/intelligence-benchmarking

6. Artificial Analysis, *Coding Agent Index*.
https://artificialanalysis.ai/agents/coding-agents

7. Katie Parrott, Every, *Vibe Check: GPT-6.2 Astra and Sol Leave Us Wanting More*.
https://every.to/vibe-check/vibe-check-gpt-6-2-astra-and-sol-leave-us-wanting-more

8. Anthropic, *Claude Opus 5.5*.
https://www.anthropic.com/claude-opus-5-5

9. Alphabet, *Q3 2026 earnings release*.
https://s206.q4cdn.com/479360582/files/doc_financials/2026/q3/2026q3-alphabet-earnings-release.pdf

10. Anthropic, *Claude Code reaches $1 billion milestone*.
https://www.anthropic.com/news/anthropic-acquires-bun-as-claude-code-reaches-usd1b-milestone

11. OpenAI, *Testing ads in ChatGPT*.
https://openai.com/index/testing-ads-in-chatgpt
