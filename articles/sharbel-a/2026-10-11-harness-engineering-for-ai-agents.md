---
title: "Agent Skills: Reusable Workflows Without More Agents"
author: Sharbel A.
channel: Sharbel A.
url: https://youtu.be/VxGIopUQVKo?si=oxzxOxmcmDAmugaO
date: 2026-10-11 16:00
tags: ai, development, technology
---

# Agent Skills: Reusable Workflows Without More Agents

[summary](../../summary/sharbel-a/2026-10-11-harness-engineering-for-ai-agents.md)

Sharbel A. argues that many repeatable AI tasks do not need separate agents. A general-purpose
agent can instead load modular “skills”: folders containing instructions, scripts, references, and
assets for a specific workflow. The video demonstrates a skill for researching successful YouTube
formats, explains three ways to create skills, and recommends reusing community packages.

The central design pattern is real and useful. Anthropic introduced Agent Skills in 2025 and later
published the format as an open standard. The headline, however, overstates Anthropic's position.
Anthropic said skills can replace fragmented, custom-designed agents for some use cases; it did not
announce that its engineers had stopped building AI agents.

## What an Agent Skill is

At minimum, a skill is a directory containing a `SKILL.md` file. That file begins with YAML
frontmatter containing two required fields:

- `name`: a lowercase identifier that matches the directory name;
- `description`: what the skill does and when an agent should load it.

The Markdown body contains procedures, examples, output requirements, edge cases, or other guidance.
A skill can also include optional directories:

- `scripts/` for executable code;
- `references/` for detailed documentation;
- `assets/` for templates, images, schemas, or static data.

The formal specification is available at:
https://agentskills.io/specification

The video describes a skill as “one folder with one text file.” That is a valid minimal case, but
not the whole format. Complex skills commonly contain multiple references, scripts, and assets.

## Progressive disclosure

Skills are designed to avoid placing every procedure in the model's context on every turn. The
agent initially receives compact metadata, chiefly each skill's name and description. If the task
matches, it reads the full `SKILL.md`. Referenced material can be loaded later as needed.

Anthropic describes this as three levels of progressive disclosure:

1. metadata that helps the agent choose a skill;
2. the full instructions loaded when the skill activates;
3. supporting files loaded only for relevant steps.

This saves context relative to loading every workflow in full. It does not make context usage free
or “effectively infinite” in practice. Metadata still consumes context, the selected files must fit
within active limits, and retrieval decisions can fail. Too many vague or overlapping descriptions
can cause the wrong skill to trigger or no skill to trigger.

Anthropic's engineering explanation is here:
https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

## Skills, agents, tools, and MCP are different layers

The phone analogy in the video maps a model to a processor, an agent to an operating system, and
skills to apps. It is intuitive but incomplete.

A model generates language and decisions. An agent adds a loop, state, tools, permissions, and an
execution environment. A skill supplies reusable procedural knowledge and sometimes executable
code. A connector or MCP server exposes live services and actions. These layers can work together,
but one does not automatically replace another.

Claude's documentation gives a useful boundary:

- use a conversation prompt for a one-off task;
- use a skill for a repeated procedure or reusable expertise;
- use project or personal instructions for rules that apply to every conversation;
- use an MCP connector for live data or external service access.

A skill may teach an agent how to use a connector, but the text file itself does not create network
access, credentials, or a service integration.

## What skills replace—and what they do not

A separate agent is often unnecessary when the only difference is a procedure: how to review code,
format a report, research a market, or prepare a document. Skills make those instructions modular,
versionable, inspectable, and reusable.

Separate agents can still be justified when work requires a distinct:

- identity or security boundary;
- model, context policy, or tool set;
- memory and lifecycle;
- execution environment;
- owner or accountability chain;
- concurrency and orchestration role.

The right comparison is therefore not “many agents versus one agent.” It is whether a capability
belongs in reusable instructions, a deterministic tool, an isolated worker, or an orchestrated
workflow. A skill can reduce duplicated prompts without eliminating multi-agent architectures.

## The headline overstates the Anthropic source

The video opens by saying Anthropic's engineers “stopped building a new agent for every single job.”
Its narration does not name an engineer, article, interview, or quotation supporting that sentence.

Anthropic's October 2025 engineering article says skills provide “a new way to build specialized
agents” and contrasts them with “fragmented, custom-designed agents for each use case.” It advocates
composable capabilities for general-purpose agents. That supports the video's design lesson, but
not the stronger claim that Anthropic engineers stopped building agents.

The distinction matters because the headline turns an architectural recommendation into company
news. The defensible statement is that Anthropic promoted skills as an alternative to creating a
separate custom agent for every domain-specific procedure.

## Building a skill manually

The video demonstrates a YouTube-research skill. Its description determines when it should trigger,
and its body gives a workflow: search a niche, filter recent videos, choose an “outlier score” above
two and more than 50,000 views, identify repeated topics and title structures, and rank promising
content pockets.

This is a useful illustration of procedural packaging, but the research method is a personal
content heuristic. The thresholds are not validated measures of future performance. View counts are
confounded by channel size, age, promotion, audience, language, recommendation placement, and topic.
An “outlier score” also depends on a particular vendor's definition and comparison baseline.

A stronger research skill would specify:

- the data source and retrieval date;
- the precise formula for each score;
- comparison against each channel's normal performance;
- minimum sample sizes and duplicate handling;
- separation of topics, formats, thumbnails, and titles;
- source links for every selected video;
- uncertainty and reasons to reject misleading candidates;
- a test against later performance rather than only retrospective winners.

The demonstration shows the generated result, but not a reproducible list of inputs or a validation
of the suggested titles. It establishes that Claude followed the workflow, not that the workflow
reliably predicts successful videos.

## Letting Claude draft a skill

The second method asks Claude to interview the user about a workflow and generate the skill. This is
faster than authoring the file from scratch and can surface edge cases the user forgot to mention.
Anthropic provides a `skill-creator` skill for this purpose.

Generation should be treated as a first draft. The author remains responsible for:

1. checking that the description triggers only on appropriate tasks;
2. reviewing every instruction and bundled file;
3. testing representative positive and negative cases;
4. comparing results against a baseline without the skill;
5. recording failures and updating the procedure;
6. versioning changes and retaining rollback paths.

An agent can write syntactically valid instructions that encode a weak process. A polished
`SKILL.md` does not prove that the underlying workflow is correct.

## Recording a workflow

The third method uses Claude Cowork's “Record a skill” feature. On supported Claude for Mac plans,
a user records the screen, clicks, typing, and optionally narration. Claude analyzes the recording
and proposes a new or updated skill for review.

The video's description that Claude “learns every single step” and can then recreate the process is
too certain. The official workflow produces a proposal; the user must inspect and save it. Visual
actions may depend on hidden state, timing, credentials, UI changes, or judgment that a recording
does not capture. Narration helps explain intent but does not remove the need for testing.

The feature also has privacy implications. Anthropic advises closing sensitive files and
conversations and avoiding passwords or secrets during recording. As of the documentation checked,
it is available in Cowork on Claude for Mac for Pro, Max, and Team plans, not in ordinary chat,
Windows, Free, or Enterprise.

Official documentation:
https://support.claude.com/en/articles/12512198-how-to-create-custom-skills

## Portability is conditional

Anthropic published Agent Skills as an open standard in December 2025. The common directory and
frontmatter format makes skills easier to move among products that implement the specification.
Cursor, Claude products, Codex, Hermes, and other tools may support the pattern.

The video's statement that one folder works across “Claude, Codex, Cursor, Hermes, you name it” is
broader than the standard guarantees. Portability depends on each client's implementation and the
skill's assumptions:

- tool names and permission models differ;
- available packages and operating systems differ;
- `${CLAUDE_SKILL_DIR}` and other placeholders may be product-specific;
- MCP servers, browser access, and credentials may not exist in another client;
- experimental fields such as `allowed-tools` have uneven support;
- scripts may require unavailable binaries or network access.

Portable skills should declare compatibility requirements, avoid undocumented client behavior, use
relative paths, and test every target environment. Format compatibility is not execution
compatibility.

## Skills are executable supply-chain artifacts

The video correctly warns that third-party skills may contain malicious instructions or scripts.
Anthropic gives the same warning: install from trusted sources and audit less-trusted packages,
including code, dependencies, bundled resources, and external network access.

The video's suggestion to “have your agent scan” a downloaded skill is not enough. A malicious
package can hide behavior in scripts, dependencies, encoded files, remote installers, dynamic
content, or instructions that activate only under certain conditions. The reviewing model may share
the same weaknesses as the executing model.

A safer installation process includes:

1. pinning a specific commit or version rather than a mutable branch;
2. reading the complete `SKILL.md` and every referenced file;
3. inspecting scripts and dependency manifests manually and with security tools;
4. checking licenses, maintainer identity, provenance, and release history;
5. testing in a disposable environment without secrets;
6. denying network access unless the workflow requires named destinations;
7. granting only the tools and filesystem paths needed for the task;
8. reviewing updates as new code, not automatically trusting the package forever.

Copying a GitHub URL into a powerful agent and asking it to “install this” delegates both package
selection and execution to the system being protected. The agent may help inspect the package, but
policy enforcement and human review should remain outside the skill.

## Reuse does not mean permanence

The video says users can teach a job once and have the skill “forever.” Skills are durable files,
but procedures decay. APIs change, user interfaces move, models interpret descriptions differently,
dependencies disappear, and business policies evolve.

Treat a skill like maintained software or operational documentation:

- assign an owner;
- state its supported environment;
- include examples and expected outputs;
- test activation as well as task completion;
- track versions and changes;
- reevaluate after model or tool upgrades;
- remove stale skills that conflict with newer ones.

The best skill is not merely reusable. It produces measurably better results than the base agent and
continues to do so after changes in its environment.

## A practical design process

A disciplined skill-development loop is:

1. Identify a repeated task and define success with representative examples.
2. Run the base agent and record recurring failures or corrections.
3. Decide which parts need instructions, references, deterministic scripts, or live connectors.
4. Write a narrow description containing both capability and trigger conditions.
5. Keep the main instructions short and move optional details into focused reference files.
6. Add scripts only where deterministic computation is better than language generation.
7. Test tasks that should trigger the skill and nearby tasks that should not.
8. Compare accuracy, consistency, cost, latency, and user intervention against the baseline.
9. Review permissions, external communication, dependencies, and secret handling.
10. Version the skill and update it from observed failures rather than assumptions.

This process captures the valuable idea behind the video without assuming that auto-generated
instructions are automatically reliable.

## Verdict

The video is a useful introduction to Agent Skills and accurately explains the basic `SKILL.md`
structure, progressive disclosure, reusable procedures, Claude-assisted creation, screen-recorded
skill proposals, and the need to inspect third-party packages.

Its headline is sensational. Anthropic advocated composable skills instead of a separate custom
agent for every procedure; it did not say its engineers stopped building agents. The claim of
universal cross-client portability also ignores differences in tools, permissions, environments,
and extensions.

The durable lesson is narrower and stronger: repeated expertise should be captured as inspectable,
versioned capability rather than copied across prompts or agent definitions. Skills are a practical
packaging mechanism, but they remain software-adjacent artifacts that require evaluation,
maintenance, compatibility testing, and supply-chain security.
