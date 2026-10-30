---
title: The App Is Disappearing From View, Not From the Stack
author: Nate B. Jones
channel: AI News & Strategy Daily | Nate B Jones
url: https://youtu.be/0j8wy4jUlsw?si=v3e3fOlSeTOD1FUp
date: 2026-10-04 16:00
tags: ai, technology
---

# The App Is Disappearing From View, Not From the Stack

[summary](../../summary/nate-b-jones/2026-10-04-post-app-ai-agent-interface.md)

Nate B. Jones calls it “the end of the app era.” The evidence supports a narrower and more useful
conclusion. Apps are not ending. Software value is separating from the requirement to use a
vendor's interface directly.

An employee may ask an agent to prepare a customer kickoff plan. The agent can read a contract,
inspect sales notes, query customer records, and draft the plan without the employee opening every
underlying application. The CRM, policy engine, records, permissions, and execution still matter.
What may disappear is the ritual of visiting each interface to obtain their value.

That distinction turns a provocative forecast into an architectural argument. It also explains why
the future is unlikely to be a blank chat box replacing everything. The emerging stack has at least
four separable layers:

1. **Interface:** where people discover, compare, supervise, and handle exceptions. 2. **Governed
workflow:** rules, approvals, validation, audit, and domain logic. 3. **Data, service, and
execution:** records, APIs, payments, inventory, and fulfillment. 4. **Agent layer:** reasoning and
orchestration across the other layers.

The contest is not simply between apps and agents. It is over which layer owns attention, context,
control, and economic rent.

## The interface is only one part of an application
The old software bundle often mixed several jobs together. It stored information, arranged it,
displayed it, and let a person act on it. A graphical interface made those capabilities feel like
one indivisible product. Agents expose the seams.

If an agent can search records and assemble a shortlist, a recruiting dashboard may matter less.
But the source data can remain essential. If an agent explains a payroll anomaly, a payroll portal
may receive fewer visits. But configured rules, approvals, tax logic, and dependable payment
execution remain essential.

This is why “no app open” does not mean “no software used.” The application may be running
headlessly behind a conversational or ambient surface. Its interface has become optional while its
workflow remains infrastructural.

Interfaces also do work that chat does poorly. Dense comparison, visual editing, monitoring, setup,
and exception handling benefit from structure. A payroll administrator may ask a question in
natural language, then open a table to inspect hundreds of exceptions before approving a run. A
salesperson may request an account brief, then use a CRM view to verify provenance and correct a
field.

The probable result is hybrid software. Agents reduce navigation and app switching. Visual surfaces
remain for oversight, high-information-density work, and confidence. Microsoft's own direction
supports convergence rather than replacement: Copilot can work with Office artifacts that remain
editable in Word, Excel, and PowerPoint.[6]

## DoorDash shows how to surrender the screen and keep the transaction
DoorDash is Jones's clearest consumer example. On September 30, 2026, the company announced U.S.
ordering by text.[2] A customer can search, build a cart, and check out in the conversation. The
experience was a beta with a waitlist, not a universal release.

DoorDash also announced an MCP-based corporate-ordering connector.[3] That program was a limited
beta with company access, employee sign-in, and consent. It was narrower than an open endpoint that
lets any assistant buy anything. A separate command-line beta reinforced the same strategic
direction.

The durable asset is not the app-opening event. It is DoorDash's merchant network, catalog, account
state, checkout, and fulfillment. If an outside agent sends a valid order, DoorDash can still earn
the transaction. The company can give up the first interface without giving up the service.

That does not prove agent ordering will generate more demand. It does not establish conversion,
retention, or broad adoption. The announcements show capability and intent, not market-scale
outcomes.

The case also reveals the hard part of delegated commerce. A person clicking “buy” approves a known
cart on a familiar surface. An agent needs bounded authority: merchant limits, spending caps, and
confirmation thresholds. It needs evidence of what the user intended and what changed before
checkout. Refunds, substitutions, chargebacks, tax, and liability still need owners.

Google's proposed Agent Payments Protocol uses signed intent and cart mandates.[16] That is an
emerging design, not a universal settlement or liability regime. DoorDash's account-bound and
consent-based beta is safer than unrestricted purchasing authority. It is also evidence that the
invisible interface still depends on visible governance.

## The incumbents are turning records into control planes
Salesforce illustrates a different defense. It did not invent SaaS. Hosted software and
application-service models predated it, and NetLedger, now NetSuite, launched in 1998.[21]
Salesforce popularized SaaS and cloud CRM after its 1999 founding.[20] That history matters because
its advantage is not only a familiar interface. It has distribution, customer records, permissions,
and knowledge of CRM workflows.

Salesforce and NVIDIA announced **Koa**, built on NVIDIA **Nemotron**.[5] Salesforce said Koa was
post-trained on synthetic CRM data, not customer data. At the evidence cutoff, it was moving into
selected customer pilots. General availability was expected later in winter 2026. Its error claims
came from Salesforce's own benchmark, not an independent evaluation.

Koa is therefore evidence of a strategic position, not proof of deployed impact. Salesforce can
expose trusted records to outside agents, offer governance over those agents, and provide its own
domain-tuned reasoning where that is useful. The value proposition spans data, workflow, gateway,
and agent.

The Salesforce–Anthropic partnership, branded **Claudeforce**, makes the strategy clearer.[7] It
included Salesforce in Claude, prebuilt sales skills, central authentication and permissions, and
MCP, API, and command-line access. But it was still in pilot or open-beta territory at the cutoff.
A partnership announcement does not prove broad production interoperability.

Optionality is real only if customers can move more than a model call. They need to export prompts,
skills, memory, policies, logs, and evaluations. They need equivalent permission semantics and
reliable behavior after migration. A menu of model names inside one control plane may still
preserve platform dependence.

Microsoft is building a similar stack from a different base. It described **Autopilot** as a
persistent, proactive, cloud-hosted agent.[6] The product had its own tenant identity, memory,
computer, and workspace. At the end of September 2026, it was expanding to private preview. That
status matters: persistence in a preview is not evidence of mature deployment.

Microsoft can combine Azure infrastructure, identity, developer tools, Office data and artifacts,
familiar applications, and the agent surface. It can also make usage-based agent capacity part of
the commercial bundle.[6] Its installed base may become an advantage even when users click fewer
Microsoft icons.

Meta approaches the same opportunity from consumer distribution. It launched consumer **Muse** on
September 8, 2026, then **Muse for Small Business** three weeks later on September 29.[4] The
business version listed connectors including QuickBooks, Shopify, Stripe, Slack, and Asana, with
approval required for sensitive publishing, sending, and spending.

Jones sees a consumer assistant becoming a small-business headquarters. That is a plausible 2027
path, not an established adoption pattern. Calling Meta a SaaS company is also an analytical
stretch; its core business remains advertising and consumer platforms. The important move is from
attention and identity into business orchestration.

## Data can outlive the product wrapped around it
Crustdata offers the cleanest example of software unbundling. Its vendor case study describes The
Firm, a two-person recruiting agency, building a custom Claude skill over Crustdata APIs.[8] The
recruiters supplied selection criteria and judgment. Crustdata supplied structured people and
work-history data. Claude supplied a new interaction and orchestration layer.

The customer could avoid another packaged recruiting interface while continuing to pay for data it
could not easily reproduce. Crustdata says the system increased capacity and accelerated closes.
Those are customer and vendor claims without an independent control group. The case demonstrates
possibility, not prevalence or measured causality.

Workday marks the opposite end of the risk spectrum. Its Payroll Agent is described as detecting
data or configuration issues, suggesting fixes for review, and preserving human oversight.[9] The
description sits on top of configured payroll data, rules, permissions, and governance.

Explaining a paycheck is not the same as reliably paying employees. Few firms should hand-code
payroll merely because an agent can generate software. Compliance rails, approvals, audit history,
and accountable execution remain valuable. An agent can increase that value by making a complex
system easier to use. Vendor language about flawless payroll is marketing, not an audited
guarantee.

Together, Crustdata and Workday define a build-versus-buy boundary. A thin interface over
replaceable information is vulnerable. Scarce structured data may remain defensible. A regulated
workflow that buyers do not want to rebuild may become more defensible. The relevant question is
not whether AI can generate a workflow. It is who will govern, test, maintain, insure, and answer
for it.

## MCP and A2A solve different parts of interoperability
Agent access is often compressed into “add MCP.” That is too simple. MCP standardizes how an AI
client connects to tools, resources, and context.[14] It can lower bespoke integration work and
make a service callable. It does not make two services semantically equivalent or safely
substitutable.

Authorization is optional at the MCP protocol level.[14] For HTTP implementations that support it,
the specification uses OAuth-based discovery, audience-bound tokens, and explicit resource
indicators. Those mechanisms reduce token misuse and confused-deputy risk. They do not ensure that
a model chooses the right action.

A2A addresses another layer. It defines how agents discover, communicate, and coordinate with other
agents, while MCP connects agents to tools and data.[15] A2A 1.0 had support from more than 150
organizations by April 2026, according to the Linux Foundation. That is momentum, not universal
compatibility.

Neither protocol standardizes portable personal memory, learned preferences, full workflow state,
or evaluation history. Neither guarantees matching policy, provenance, error semantics, or task
success. Protocol support should be treated as reachability until interoperability is tested.

## Identity and security become product features
An agent that reads mail, updates CRM, orders food, and touches payroll cannot operate as an
unbounded extension of a user account. It needs its own identity, a human sponsor, narrow scopes,
expiry, and revocation. It needs separation between delegated user authority and service authority.
Every consequential action needs an auditable chain back to intent.

Microsoft Entra's agent identity model points in this direction.[19] It includes unique agent
identities, sponsors, access packages, expiration, and conditional access. This governance layer
may strengthen cloud and identity incumbents while weakening the direct interface of smaller point
products.

Prompt injection remains a more fundamental problem. Malicious instructions can hide in email,
webpages, documents, tool output, or a candidate résumé that a recruiting agent is asked to assess.
The UK National Cyber Security Centre warns that current language models do not enforce a security
boundary between instructions and data.[18]

In a 2026 red-team competition, NIST reported at least one successful hijacking against every one
of 13 frontier models across more than 250,000 attempts.[17] Authentication does not make a model's
decision trustworthy. Human review helps, but does not by itself establish fairness or legal
compliance.

Practical systems need least privilege, deterministic policy gates, and sandboxing. They need
signed tool metadata, origin and provenance, full tool-call logs, rate and spending limits, rapid
revocation, and human confirmation for irreversible acts. These are not accessories to the agent
layer. They are part of the product.

## Reliability keeps the visual escape hatch alive
Agent reliability has improved, but it is not solved. Stanford's 2026 AI Index reports 66.3%
accuracy on OSWorld in 2025.[11] That leaves roughly one failure in three on a structured
computer-use benchmark. Production workflows add stale data, API outages, permissions failures,
model variance, partial completion, and cross-system rollback.

Each connector and remote agent adds latency and another failure boundary. Long-running work can
hide waiting, but it cannot eliminate failure handling. Users need progress states, cancellation,
retries, idempotency, and compensation when only part of a transaction succeeds. They also need a
review surface that shows what happened.

“Dependable execution” is therefore a requirement, not a demonstrated property. The launches
discussed by Jones provide no comparable uptime, error-rate, latency, or end-to-end task-completion
data. Volume and speed are not business outcomes. More generated reports, processed records, or
agent calls can simply mean more review.

The useful denominator is the successful, governed outcome. Measure cost per completed task, human
review time, incident rate, rollback frequency, outcome quality, and recovery after a vendor
switch. Revenue or productivity claims also need a causal design, not a before-and-after story that
ignores staffing, demand, and process changes.

## The app market supplies an important reality check
The strongest contrary evidence is hiding in plain sight: apps are still growing. Sensor Tower
reported nearly 150 billion mobile downloads in 2025, $167 billion in spending, and 5.3 trillion
hours of use.[12] Generative-AI apps were themselves part of that growth.

An Apple-commissioned Analysis Group study estimated that the App Store ecosystem facilitated more
than $1.4 trillion in billings and sales in 2025, with 850 million average weekly users.[13] That
total includes physical goods and services and reflects Apple's interests. Sensor Tower also has
commercial interests and covers iOS and Google Play. The measures are not directly comparable.

Even with those caveats, neither source shows an app collapse already underway. The evidence
supports coexistence: rising mobile engagement alongside agent adoption. The change is in the path
to a service, not the disappearance of services or screens.

Enterprise deployment is also earlier than the rhetoric implies. Stanford reports that 88% of
surveyed organizations used AI in 2025, and 70% used generative AI in at least one function.[10]
Yet agent deployment remained in the single digits across nearly all functions. Jones's “every
role” language should be read as provocation, not measurement.

His claims about 2027 should likewise be treated as forecasts. Consumer agents may spill into
small-business operations. MCP access may become expected in some categories. AI-vendor switching
conflicts may become more visible. None of those outcomes was established by October 4, 2026.

## Lock-in moves into the employee's hidden workflow

Jones's strongest organizational insight is not about technology architecture. It is about work
that procurement cannot see.

A recruiter may combine a paid agent, data APIs, browser automation, custom skills, review habits,
and feedback from hiring outcomes. Over time, the workflow accumulates tacit criteria for different
managers. Finance sees a subscription and token bill. The recruiter sees weeks of context, tuning,
and operating knowledge.

This is a new switching cost, but it is not inevitable. Vendor-neutral harnesses, documented
instructions, exportable memory, open logs, reusable evaluations, and model routing can reduce it.
Organizations should test migration before claiming optionality. A backup model that cannot
reproduce the workflow is not a backup.

Employees should document the real production system: inputs, data sources, prompts, skills, tools,
approvals, exceptions, and outputs. They should record quality checks and the business result the
workflow supports. That makes hidden dependence legible without mistaking private tricks for
durable capability.

Disclosure is not risk-free. Workers may fear that revealing automation will raise quotas or
threaten headcount. Managers can reduce that fear by separating workflow discovery from performance
punishment, and by crediting the people who make reusable practices visible.

Leaders should map actual team usage before consolidating vendors. They should include migration
time, quality loss, retraining, and incident exposure, not only license and token prices. The cost
of switching lives in employee practice as well as procurement contracts.

## Business models will follow the value

As interface ownership weakens, software revenue does not vanish. It can move toward subscriptions
for systems of record and governance, usage charges for models and agent capacity, API or data
metering, and transaction or fulfillment fees. Implementation, evaluation, security, and exception
management become sellable services. Outcome-based pricing may grow where outcomes can actually be
attributed.

A general agent can also become the new gatekeeper. It may control discovery, ranking, defaults,
identity, payment, and access. That can shift power toward Microsoft, Meta, Apple, Google,
Anthropic, OpenAI, or another distribution owner. Open protocols reduce integration friction, but
certification, telemetry, billing, and default placement can still centralize control.

Underlying providers retain leverage too. DoorDash controls available merchants, checkout, and
fulfillment. Salesforce governs CRM records and actions. Workday governs payroll configuration and
execution. Headless does not mean commoditized.

The winning product may be the one that gives up interface exclusivity while preserving
differentiated data, governed workflow, and accountable execution. Its own agent can be excellent
without excluding outside agents. Its visual application can remain available without being
mandatory.

## A practical test for the post-destination app

For any software purchase, ask four questions.

**Interface:** What is better in chat, and what still needs a visual surface?

**Workflow:** Which rules, approvals, audit trails, and exceptions are hard to rebuild?

**Service:** Who owns the authoritative data, transaction, and operational liability?

**Agent:** Can multiple agents access the system safely, and can context move between them?

Then test the connections rather than checking boxes. Verify scopes, provenance, human approvals,
rollback, and task completion. Export memory, prompts, skills, logs, and evaluations. Run a
migration exercise and measure recovery time. Track direct app opens, agent-mediated transactions,
review time, incidents, successful-task cost, retention, and switching effort over 12 to 24 months.

That is a more falsifiable story than “the app era is over.” Apps remain healthy, and agents remain
early. But the assumption that every software company must own a dedicated interaction in order to
deliver and capture value is already under pressure.

The app is not disappearing from the stack. It is becoming one possible doorway into a governed
system of value.

## Sources

[2]: https://about.doordash.com/en-us/news/text-doordash [3]:
https://about.doordash.com/en-us/news/doordash-ordering-connector [4]:
https://about.fb.com/news/2026/09/introducing-muse-small-business [5]:
https://www.salesforce.com/news/press-releases/2026/09/15/koa-reasoning-model [6]:
https://blogs.microsoft.com/ "Introducing the new Copilot with Home, Code and Autopilot" [7]:
https://investor.salesforce.com/ "Salesforce and Anthropic Announce Claudeforce" [8]:
https://crustdata.com/case-studies/the-firm [9]:
https://www.workday.com/en-us/artificial-intelligence/ai-agents/payroll.html [10]:
https://hai.stanford.edu/ai-index/2026-ai-index-report/economy [11]:
https://hai.stanford.edu/ai-index/2026-ai-index-report/technical-performance [12]:
https://sensortower.com/blog/state-of-mobile-2026 [13]: https://www.apple.com/newsroom/ "App Store
ecosystem reaches $1.4 trillion" [14]:
https://modelcontextprotocol.io/specification/2025-06-18/basic/authorization [15]:
https://www.linuxfoundation.org/press/ "A2A Protocol Surpasses 150 Organizations" [16]:
https://cloud.google.com/blog/ "Announcing Agent Payments Protocol (AP2)" [17]:
https://www.nist.gov/blogs/ "Insights into AI Agent Security" [18]:
https://www.ncsc.gov.uk/blog-post/prompt-injection-is-not-sql-injection [19]:
https://learn.microsoft.com/en-us/entra/id-governance/agent-id-governance-overview [20]:
https://www.salesforce.com/news/stories/the-history-of-salesforce [21]:
https://www.netsuite.com/portal/aboutus.shtml

*Source note: This article draws on Nate B. Jones's October 4, 2026 video and its automatic
*captions. Product names and claims were checked against the sources above; the captions remain
*fallible, and launch announcements do not establish adoption.*