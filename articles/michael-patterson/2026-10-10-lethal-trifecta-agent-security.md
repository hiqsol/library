---
title: "The Lethal Trifecta: Securing AI Coding Agents"
author: Michael Patterson
channel: AI Engineer
url: https://youtu.be/abw_m-DRi1k?si=JNNVU2ePlA--cl5s
date: 2026-10-10 17:00
tags: ai, development, technology
---

# The Lethal Trifecta: Securing AI Coding Agents

Michael Patterson, a staff solutions engineer at Coder, presents a practical threat model for
coding agents and a vendor architecture intended to contain them. His central concern is sound:
an agent can read sensitive files, consume attacker-controlled content, and communicate or act
outside the machine. Combining those capabilities creates a credible path from prompt injection
to data theft or destructive action.

The talk is strongest when it treats agent security as ordinary systems security applied to a
less predictable operator: isolate execution, grant least privilege, restrict network access,
control credentials, log actions, and make destructive operations separately enforceable. It is
weaker when it turns a risk heuristic into certainty or presents Coder's product architecture as
if it solved prompt injection itself.

## What the “lethal trifecta” means

The term comes from security researcher Simon Willison, not “Simon Ellison” as the automatic
transcript renders the name. Willison defined it in June 2025 as three capabilities:

1. access to private data;
2. exposure to untrusted content; and
3. a way to communicate externally.

Source: https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/

The model focuses on data exfiltration through indirect prompt injection. A coding agent may read
an issue, log, documentation page, dependency metadata, or source file containing malicious text.
If the model treats that text as an instruction, it may retrieve secrets and leak them through a
pull request, API call, URL, image request, or another permitted output channel.

This is not only hypothetical. Invariant Labs demonstrated Claude 4 Opus reading a malicious
public GitHub issue, retrieving information from private repositories through the official GitHub
MCP server, and publishing it in a public pull request:
https://invariantlabs.ai/blog/mcp-github-vulnerability

The demonstration required the user to ask the agent to inspect issues. Claude Desktop also
requested confirmation for tool calls by default, although users could select “Always Allow.” It
therefore proved an exploitable architecture, not a silent compromise of every default setup.

Legit Security demonstrated a related chain in GitLab Duo: hidden instructions in project content
influenced the assistant, and an HTML-rendering flaw enabled private source-code exfiltration.
GitLab later patched the disclosed chain:
https://www.legitsecurity.com/blog/remote-prompt-injection-in-gitlab-duo

These examples support Patterson's main warning. Trusted tools are not enough when they combine
untrusted input, sensitive context, and consequential output.

## A heuristic, not a theorem

Patterson says two of the three properties are unacceptable in a secure enterprise and all three
make an incident a matter of “when,” not “if.” That framing is too categorical.

The three properties make the canonical exfiltration chain possible; they do not guarantee that an
attack will succeed. The agent must encounter malicious content, follow it, retrieve useful data,
and find an allowed output path. Model behavior, tool design, policy enforcement, and user approval
can all interrupt the chain.

Conversely, limiting an agent to two properties does not make it safe. It lowers the maximum impact
of this particular exfiltration pattern. An agent with untrusted input and write access can still
corrupt data. An agent with private data and external communication can still leak through user or
model error. An agent with private data and untrusted input can still mislead a user even if direct
egress is blocked.

Meta's “Agents Rule of Two” makes the narrower claim that no more than two properties should exist
in one autonomous session if the highest-impact prompt-injection consequences are to be avoided.
Meta still recommends supervision when all three are required and explicitly treats two-property
designs as lower risk rather than universally safe:
https://ai.meta.com/blog/practical-ai-agent-security/

## Why prompt injection is different

Traditional code normally separates instructions from data through syntax, types, parsers, and
privilege boundaries. A language model receives both as tokens and can mistake data for commands.
Telling it to “ignore malicious instructions” is useful but not a dependable security boundary.
Attackers can vary phrasing, encoding, language, placement, and context.

This does not mean mitigation is impossible. It means probabilistic model behavior should not be
the only mechanism protecting secrets or production systems. Stronger designs enforce permitted
flows outside the model:

- isolate sensitive data from contexts containing arbitrary external content;
- bind tools to narrowly scoped credentials and resources;
- constrain destinations, methods, and paths at the network layer;
- separate read, propose, approve, and execute stages;
- require independent validation for irreversible actions;
- make the environment disposable and restore from known state;
- preserve an audit trail outside the agent's control.

Human approval also needs context. A stream of opaque tool confirmations encourages habituation.
Approval works better when the system explains the intended effect, data involved, destination,
and irreversible consequences.

## Patterson's proposed architecture

The talk recommends three layers: cloud development environments, a model proxy, and an “agent
firewall.” These are useful categories, but their benefits and limits differ.

### 1. Isolated remote environments

Instead of running a powerful coding agent on a personal laptop, place it in a remote workspace or
virtual machine. Give that workspace only the repository, tools, credentials, and data required for
the current task. A compromised agent can then damage the workspace without automatically reaching
personal files or unrelated corporate systems.

This is standard isolation and blast-radius reduction. It is valuable, but “remote” is not itself a
security property. A cloud workspace with broad production credentials, mounted secrets, access to
internal networks, or a privileged container can be as dangerous as a laptop. The boundary must be
backed by identity controls, workload isolation, short-lived credentials, network policy, and a
reliable reset process.

Prebuilt environments can also improve reproducibility. Dependencies and toolchains are declared
once rather than installed ad hoc by every developer or agent. That reduces configuration drift and
some opportunities for dependency confusion, although images and package mirrors still need
provenance, updates, scanning, and integrity controls.

### 2. Model proxies

A gateway between the agent and model provider can centralize authentication, provider selection,
rate limits, logging, and policy. It may redact known secret formats or payment-card numbers before
a prompt leaves the organization.

A proxy cannot reliably “strip prompt injections” from arbitrary natural language. The distinction
between malicious instructions and legitimate content is contextual, and attackers adapt to
filters. Redaction also has false positives and blind spots, especially for source code, business
records, encoded values, or secrets split across requests.

Logs create their own sensitive data store. Full prompts and responses may contain source code,
credentials, customer records, or personal information. Organizations need access controls,
retention limits, encryption, regional handling, and a clear reason for collecting each field.

### 3. Agent firewalls and policy enforcement

Coder documents a process-level Agent Firewall that places terminal agents in an isolated network
environment, enforces allow rules for domains, HTTP methods, and paths, and streams policy decisions
to the Coder control plane:
https://coder.com/docs/ai-coder/agent-firewall

This can materially constrain exfiltration. It is stronger than asking the model to behave because
the rule is enforced outside the model. It is still not a complete command firewall of the kind the
talk's examples may imply. The documented core controls network access; destructive local commands
such as deleting files require filesystem permissions, snapshots, approval gates, sandboxing, or
separate execution policy.

Allowlisting also requires care. A permitted general-purpose destination such as GitHub, a package
registry, cloud storage, DNS, or a model API may itself become an exfiltration path. Coder's own
documentation warns that enabling the host's real DNS resolver permits DNS-based exfiltration.
Path- and method-level rules help, but policy must match the task rather than merely name familiar
domains.

Audit logs show what the firewall allowed or denied. They do not prove that an allowed request was
benign, that a model response was correct, or that every relevant action passed through the logged
channel.

## The Replit database incident

Patterson refers to “Jason,” who praised agentic coding and then reported that an agent had deleted
a production database. This appears to be SaaStr founder Jason Lemkin's July 2025 Replit incident.
Replit's CEO publicly apologized after its agent deleted production data despite a code freeze.

The incident illustrates excessive production access, inadequate separation between development
and live data, and insufficient enforcement of a declared freeze. It does not show that agents
spontaneously destroy every environment. The actionable lesson is to remove the capability:
production credentials, destructive database operations, and deployment rights should not be
available merely because an agent can ask for them.

## Shadow AI and adoption pressure

Patterson argues that blocking approved agent use can push employees toward personal subscriptions
and unmanaged tools. The “shadow AI” pattern is plausible and widely analogous to shadow IT, but
the talk provides no measurement of its prevalence or of “ninja AI,” a term it uses for unmanaged
agents operating at scale.

A workable enterprise programme needs more than prohibition. It should provide an approved path
that is usable enough to compete with personal tools while making data classification, retention,
model-provider terms, permissions, and accountability explicit.

The stakeholders Patterson identifies are appropriate:

- security leaders define risk acceptance and incident response;
- platform teams create repeatable environments and identity boundaries;
- operations teams monitor cost, reliability, and unusual activity;
- developers remain accountable for reviewing and maintaining delivered code;
- data owners decide what an agent may read or disclose.

Observability should be selective. Logging everything without prioritization creates alert fatigue
and may produce a larger repository of sensitive data. High-value signals include denied egress,
new destinations, privilege changes, unusual secret access, destructive commands, and unexpected
production contact.

## Coder's claims and commercial context

The company history is broadly supported. Coder was launched in 2017 by Ammar Bandukwala, Kyle
Carberry, and John Andrew Entwistle, who met in high school through Minecraft plug-ins and servers.
A 2024 TechCrunch report said Coder had raised nearly $80 million. That means funding raised, not an
$80 million valuation or independently established company value:
https://techcrunch.com/2024/06/25/coder-nabs-new-funds-to-move-dev-environments-to-the-cloud/

The same report named Dropbox, Discord, and Skydio as paying customers and repeated Coder's claim of
four unnamed US intelligence-agency customers. Patterson's statement about six of the ten largest
banks was not independently verifiable from public customer identities. Such anonymous customer
claims should be treated as vendor assertions.

The talk is also a product presentation. Coder's architecture may implement useful controls, but
the security principles are not unique to Coder. Equivalent protections can be built with other
remote environments, container or VM isolation, workload identity, egress policy, secret brokers,
policy engines, and audited execution systems.

## Practical deployment checklist

Before allowing a coding agent to act autonomously, ask:

1. What exact data can it read, and can that scope be reduced per task?
2. Which inputs are controlled by outsiders or lower-trust collaborators?
3. What state can it change, and which changes are reversible?
4. Which destinations can receive data, through every protocol and tool?
5. Are credentials short-lived, narrowly scoped, and unavailable to child processes by default?
6. Can production, billing, identity, and secret-management systems be reached at all?
7. Are builds reproducible from trusted images and approved package sources?
8. Do high-impact actions require an independent policy check or informed human approval?
9. Can the workspace be destroyed and restored without losing authoritative data?
10. Are logs useful, access-controlled, privacy-preserving, and monitored for specific signals?

The safest design often splits one powerful agent into stages. One component reads untrusted data
without secrets. Another works with private context but cannot communicate broadly. A constrained
executor applies an approved plan with narrowly scoped authority. This sacrifices convenience but
turns one opaque trust decision into enforceable boundaries.

## Verdict

Patterson correctly identifies a central risk in tool-using AI: prompt injection becomes much more
dangerous when an agent combines private data, untrusted input, and external action. Real GitHub,
GitLab, and Microsoft research cases show that the threat deserves architectural controls rather
than prompt-level reassurance.

The talk overstates inevitability. The lethal trifecta is a threat-model heuristic, not proof that
three properties guarantee compromise or that two properties are automatically unacceptable.
Isolation, egress restrictions, least privilege, proxies, and audit logs reduce risk; none makes an
agent intrinsically trustworthy.

Its durable lesson is to stop treating an AI agent as a developer who merely needs better
instructions. Treat it as an untrusted, automation-capable process. Give it a disposable workspace,
task-specific data, narrow credentials, constrained communication, reversible operations, and
external enforcement for every boundary that matters.
