---
title: "The Big Lie About AI Coding: What the Evidence Actually Supports"
author: Less Bitter
channel: Less Bitter
url: https://youtu.be/DzSS9R8t2Ao?is=ofGkfLhNDhnPq1H7
date: 2026-10-06 19:09
tags: ai, development
---

# The Big Lie About AI Coding: What the Evidence Actually Supports

Less Bitter argues that an online “Markdown Industrial Complex” exaggerates the value of
AI-coding skill files and custom workflows. The useful part of the critique is that GitHub stars,
bookmarks, views, prompts, tokens, commits, and pull requests are activity or attention metrics.
None alone measures useful delivery, software quality, customer value, or business outcomes.

The categorical thesis does not survive scrutiny. The video repeatedly says that “there’s no
skill in AI coding” and attributes exceptional output mainly to working 10–12 hours a day.
Controlled evidence shows a more conditional reality. Curated procedural skills, repository
instructions, interfaces, and verification scaffolds can help, do nothing, or hurt depending on
the task, model, and harness. The defensible lesson is to test each intervention, not to treat all
Markdown as expertise or all scaffolding as superstition.

The video names no research paper, controlled experiment, adoption survey, or quality audit. Its
case rests on social posts, engagement counters, self-reported output, a disputed language
benchmark, memes, and the host’s interpretation. That evidence can expose hype, but it cannot
support universal causal claims.

## The historical claims

The video says Garry Tan’s gstack appeared “maybe February” 2026 and calls Tan the godfather who
invented the trend. GitHub records the repository as created on 11 March 2026:
https://api.github.com/repos/garrytan/gstack

The date is wrong, and the priority claim is false. Anthropic introduced Agent Skills and the
`SKILL.md` format on 16 October 2025, then published the format as an open standard in December:
https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

Instruction files, custom commands, and repository guidance also predate gstack. Tan did create a
very popular implementation. The video’s contemporaneous frame shows about 135,500 stars, making
“130,000” a reasonable rounded figure. Stars show attention, not effectiveness.

The video also reduces gstack to text files that tell an agent to behave like a CEO or engineer.
Its official description does advertise 23 opinionated tools covering roles such as CEO,
designer, engineering manager, release manager, documentation engineer, and QA. The repository
also contains scripts, tests, browser tooling, templates, and resources. “A bunch of text files”
is materially incomplete.

Garry Tan’s title is accurate. Y Combinator identifies him as its president and CEO and as a
general partner: https://www.ycombinator.com/people/garry-tan

## Lauren Tan’s pull-request claim

Lauren Tan’s post says, “here’s how i shipped 2,500 PRs last month to production”:
https://x.com/poteto/status/2102050467505430555

The embedded talk is internally inconsistent with that post. Its title card says 2,000 PRs, and
Tan says “2,000 pull requests” in the recording. Neither figure is independently audited. The
video’s frame and narration show about 3.2 million views and 30,000 bookmarks, but those counters
measure attention rather than production value.

Less Bitter says the explanation is simply that Tan worked 10–12 hours each day. A review of the
full embedded talk found no such statement. Tan instead describes verification tooling, a control
CLI, feature maps, static analysis, CI, architecture constraints, PStack skills, telemetry, and
substantial setup work. These remain self-reported methods rather than independently tested
causes, but the video’s “that’s it” summary is not faithful to her account.

The claim that anyone working the same hours would match the output has no comparison group.
Repository policy, task size, automation, merge permissions, review process, team support,
quality gates, and the definition of “to production” are all uncontrolled.

The arithmetic shows why the missing denominator matters. At 2,500 PRs over 30 straight
12-hour days, the rate is 6.94 PRs per hour, or one every 8.64 minutes. Across 22 twelve-hour
workdays, it is 9.47 per hour, or one every 6.34 minutes. Across 22 ten-hour days, it is 11.36
per hour, or one every 5.28 minutes. These rates do not disprove the claim. They imply unusually
small or automated units and make PR granularity essential context.

One PR is also not one agent request. A PR may contain many prompts, retries, tests, commits,
reviews, and deployments. Automation can create many small PRs from one workflow. The video’s
conversion between the two is unsupported.

## Practitioner quotations and the Campfire benchmark

Dax wrote that models improve faster than workflow tinkerers and that someone using vanilla
Codex may be closer to the state of the art:
https://x.com/thdxr/status/2107260844400931156

The quotation is substantially accurate. It identifies a plausible maintenance problem: custom
scaffolding can preserve workarounds for weaknesses newer models no longer have. It remains a
practitioner opinion rather than a controlled comparison. Stable project conventions, acceptance
criteria, and verification procedures are different from temporary model workarounds.

Matt Pocock’s `/retro` post proposes inspecting ten prior agent sessions for navigation problems
and stale documentation. The source says that improving navigability is an underrated way to save
tokens: https://x.com/mattpocockuk/status/2105951409887949107

The video dismisses the idea as perhaps ten tokens or one tool call, but supplies no traces,
latency measurements, success rates, or maintenance costs. Better navigation could affect error
rates and onboarding as well as tokens. Generic context can be wasteful, but that does not settle
this particular workflow.

David Heinemeier Hansson said that agents implemented and optimized Campfire in Elixir, Go, and
Rust: https://x.com/dhh/status/2106810173683851564

A critic noted that the Elixir version disallowed concurrent database reads:
https://x.com/crertel/status/2106862514772320427

DHH replied that two frontier agents produced the implementation:
https://x.com/dhh/status/2106864061832991134

The exchange is real, but the implementations were not equivalent. The published discussion also
identified changes involving queues, CSRF behavior, and caching. Requests per second therefore
cannot isolate language performance or agent engineering quality. Delegating implementation does
not remove responsibility for benchmark design.

The video further claims that Claude “obviously” wrote a line in Matt Pocock’s changelog and
probably wrote everything else. The text exists, but the authorship inference has no commit or
provenance evidence. AI authorship and practical efficacy are separate questions.

## Controlled-task performance

A 2022 randomized GitHub Copilot experiment assigned 95 professional developers to one JavaScript
HTTP-server task. Among completers, the Copilot group averaged 71.17 minutes against 160.89
minutes, reported as 55.8% faster with a 95% confidence interval from 21% to 89%:
https://arxiv.org/html/2302.06590

This is causal evidence for one short, specified task with an early autocomplete model. It is not
a universal production estimate.

GitHub’s 2024 quality experiment recruited 202 experienced Python developers for one restaurant
review API task. Copilot access raised the likelihood of passing all ten tests by 53.2%, improved
blinded reviewer scores modestly, and raised approval probability by 5%. GitHub’s report is at:
https://github.blog/?s=does+github+copilot+improve+code+quality

The study was vendor-run and measured a short exercise. It did not measure long-term maintenance,
escaped defects, incidents, security, or customer outcomes.

SkillsBench tested 7,308 trajectories across 84 evaluated tasks. Curated skills raised average
pass rate by 16.2 percentage points, but software-engineering tasks gained only 4.5 points and 16
of 84 tasks became worse. Self-generated skills averaged a 1.3-point decline:
https://arxiv.org/html/2602.12670v1

That supports targeted procedural context, not indiscriminate skill packs. The benchmark is also
containerized, terminal-based, and bounded by deterministic verifiers.

A separate AGENTS.md evaluation found that generic repository context did not generally improve
success and increased inference cost by more than 20%:
https://arxiv.org/html/2602.11988v2

Developer-written files performed about seven points better than generated files, but not enough
to establish a general gain. This supports the video’s skepticism toward generated context dumps.
It does not show that all instructions are useless.

SWE-agent provides a direct fixed-model counterexample to “only the model matters.” Its custom
agent-computer interface solved 10.7 percentage points more SWE-bench-Lite instances than a
baseline using the default Linux shell:
https://arxiv.org/html/2405.15793

These studies test controlled task success. They do not establish team delivery or business value.

## Individual throughput

A field experiment randomized Copilot access for 4,867 developers at Microsoft, Accenture, and a
Fortune 100 company. The pooled instrumental-variable estimate was 26.08% more completed weekly
tasks among users, with a standard error of 10.3%:
https://economics.mit.edu/sites/default/files/inline-files/draft_copilot_experiments.pdf

Completed tasks were operationalized mainly through pull requests. Commits and builds were
secondary activity measures, while build success was a limited quality proxy. PR size and
importance can vary, and a merged PR may never benefit a user. The estimate is a local effect for
adopters under those organizations’ workflows, not a validation of cross-company PR counts.

METR obtained the opposite result in a different population. Sixteen experienced open-source
maintainers completed 246 real tasks in familiar repositories and took 19% longer with early-2025
AI tools: https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/

METR’s 2026 continuation no longer supports a reliable current estimate. Point estimates suggested
an 18% speedup for returning developers and 4% for new recruits, but confidence intervals included
no effect or slowdown. Developers increasingly avoided no-AI conditions and selected tasks, which
introduced bias: https://metr.org/blog/2026-02-24-uplift-update/

The joint lesson is heterogeneity. Effects vary with model generation, task type, repository
familiarity, user expertise, and selection into AI use. Neither “AI always makes developers
faster” nor “only longer hours matter” is supported.

## Team delivery

The video gives no lead time, deployment frequency, change-failure rate, failed-deployment
recovery time, review queue, rework, or incident data. Lauren Tan’s PR count and DHH’s throughput
table therefore do not demonstrate team delivery performance.

DORA 2024 reported associations between higher AI adoption and better documentation quality,
self-reported code quality, and review speed. It also reported 1.5% lower delivery throughput and
7.2% lower stability:
https://cloud.google.com/blog/products/devops-sre/announcing-the-2024-dora-report

DORA 2025 surveyed nearly 5,000 technology professionals. It reported 90% AI use, more than 80%
perceived productivity improvement, a positive relationship with delivery throughput, and
continued higher delivery instability:
https://services.google.com/fh/files/misc/2025_state_of_ai_assisted_software_development.pdf

The year-to-year direction change cautions against treating cross-sectional relationships as fixed
causal effects. DORA itself says the 2025 regressions are safest read as comparisons. Self-report,
organization maturity, task mix, platform quality, and reverse causation remain plausible
confounders.

## Software quality and security

Quality is multidimensional. Passing tests, build success, reviewer preference, readability,
latency, maintainability, reliability, escaped defects, incident severity, and security are not
interchangeable.

The GitHub exercise supports improved test success and modest review gains on one Python task. A
peer-reviewed 47-person security study found that AI-assisted participants produced less secure
solutions in four of five tasks and were more likely to believe that their code was secure:
https://arxiv.org/html/2211.03622

That study used older models and short educational tasks, limiting transfer to 2026 agents. It
still refutes any blanket inference that more AI-generated code is necessarily safe or high
quality.

Tan’s talk advocates executable verification, CI, lint rules, architecture constraints, telemetry,
and human responsibility. These are sensible controls, not proof that the reported PRs were high
quality. DHH’s non-equivalent implementations likewise cannot validate agent engineering quality.

## Business and customer outcomes

No source in the video reports revenue, profit, retention, conversion, customer satisfaction,
cost to serve, support burden, incident cost, or goal attainment. The video therefore supplies no
evidence that the cited workflows created business value. It also supplies no evidence that they
failed to do so.

DORA includes self-reported product and organizational constructs, but its analysis is
observational and avoids strong causal interpretation. Teams need evaluations that connect an AI
intervention to representative work and downstream user or business outcomes.

## Bias and measurement problems

The video selects viral successes and provocative posts. Failed skill packs, unremarkable agents,
and people whose long hours produced little are absent. That is selection and survivorship bias.

Hours, model quality, tools, instructions, architecture, tests, expertise, team support, and task
type vary together. Attributing output to hours alone does not isolate a cause.

Stars, views, bookmarks, PRs, commits, tokens, and requests per second measure different things.
Optimizing any proxy can distort behavior. PR targets encourage tiny changes; benchmark targets
encourage verifier overfitting; raw speed can trade off against stability or security.

Vendor-run studies and creator self-reports are useful but need independent replication and
objective telemetry. Benchmarks also have limited external validity. Bounded terminal tasks do not
capture long-term maintenance, cross-team coordination, operational risk, or whether a feature
should have been built.

“Markdown” is too broad a category. Repository overviews, nonfunctional requirements, procedural
checklists, executable tools, examples, and verification scripts are different interventions.
SkillsBench and the AGENTS.md study can reach different results without contradiction because they
test different things.

## Verdict

The title is sensational. A narrower thesis is well supported: viral AI-coding content often
markets activity metrics and generic instruction packs without causal evidence of delivery,
quality, or business value. Teams should evaluate context and skills on representative tasks and
measure human time, task success, inference cost, review burden, escaped defects, delivery
stability, and user outcomes.

The video replaces one absolutism with another. “All skill packs improve productivity” is
unsupported. So is “there’s no skill in AI coding.” The available evidence favors measured,
task-specific scaffolding plus strong engineering controls, with no presumption that more files,
agent runs, hours, or pull requests create value.

## Editorial corrections

- Retitle the piece around the weakness of viral output metrics rather than “the big lie.”
- Change gstack’s origin from February to 11 March 2026 and remove the priority claim.
- State that Tan’s post says 2,500 PRs while her talk says 2,000; label both self-reported.
- Remove the unsupported attribution of 10–12-hour days to Tan.
- Describe her verification, architecture, CI, telemetry, and skills before assessing causality.
- Present Dax’s post as practitioner opinion and contrast positive and negative benchmarks.
- Explain why the Campfire implementations do not isolate language or agent performance.
- Remove authorship guesses about Claude unless commit-level provenance is available.
- Separate controlled-task results, individual throughput, team delivery, software quality,
  security, and business outcomes on screen.
- Replace output volume with versioned evaluations on representative work and downstream outcomes.
