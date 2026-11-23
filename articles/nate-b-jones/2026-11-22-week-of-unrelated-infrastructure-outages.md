---
title: A Week of Outages Exposed Fragile Infrastructure, Not One AI Attack
author: Nate B. Jones
channel: AI News & Strategy Daily | Nate B Jones
url: https://youtu.be/fFeyE4nINqs?is=a7TkRS1Qx4gPD6y-
date: 2026-11-22 18:00
tags: ai, technology
---

# A Week of Outages Exposed Fragile Infrastructure, Not One AI Attack

[summary](../../summary/nate-b-jones/2026-11-22-week-of-unrelated-infrastructure-outages.md)

Microsoft 365, the FAA, Chase, United Airlines, Apple, and an NSA internal network all suffered
significant disruptions within six days. A separate compromise injected malicious code into
websites using Optimizely. The timing looked ominous, but the evidence does not support one
coordinated AI attack.

The documented causes differed: a Microsoft software-and-capacity cascade, overloaded FAA
network equipment during modernization, a Chase software defect, an unspecified United
technology failure, an Apple update, NSA security maintenance, and an Optimizely account-signup
flaw.

Nate B. Jones uses the week to make a broader argument that remains valuable after separating
the incidents. Digital infrastructure is deeply interdependent, attackers need only one usable
weakness, and restoration can require far more coordination than initial containment. Agentic
tools such as ARTEX can compress intrusion timelines, but they did not cause this cluster of
outages on the available evidence.

## The incidents were real but mostly unrelated

Temporal proximity is not a causal link. A useful analysis must establish each incident's scope,
timeline, and official or reported cause before connecting it to a larger cyber campaign.

Three narrow connections are supported:

- failures across Microsoft products belonged to one Microsoft incident;
- Chase's processing defect delayed some transactions involving other banks and Zelle;
- 178 organizations loaded malicious code through compromised Optimizely projects.

No reviewed incident report links Microsoft, the FAA, Chase, United, Apple, the NSA, and
Optimizely to one attacker. None attributes the outage sequence to ARTEX.

## Microsoft 365: a recovery cascade, not an attack

A global Microsoft 365 incident began on November 12. Exchange Online-dependent features failed,
affecting Outlook email and scheduling as well as connected features in Teams and Copilot. All
remaining customers and regions were restored by November 14, more than 24 hours later.

Microsoft's preliminary explanation identified three interacting conditions:

1. a latent software defect introduced in July;
2. failure of one of two networking gateways used for Teams traffic;
3. more than 14% of server capacity unavailable for a separate reason.

The increased load exposed the latent defect and made servers unresponsive. During recovery,
queued traffic overwhelmed servers as they returned, causing them to become unresponsive again.
Automated rollback and recovery mechanisms could not quickly escape the unusually broad failure
state.

The video says recovery traffic took healthy servers down. That captures the feedback mechanism
but is less precise than Microsoft's account: queued demand overwhelmed returning capacity.

Full restoration took more than a day, not “nearly a day.” The bug was introduced in July, so
“months-old” is safer than an exact three-month age.

Microsoft said it found no evidence of malicious activity and explicitly said the incident was
not related to cyber activity or AI agents.

## FAA: departures stopped during a network upgrade

On November 13, the FAA halted departures nationwide for a little over four hours. Aircraft
already in the air continued and landed safely, so this was not a closure of all US airspace.

The preliminary explanation was a communications failure during routine modernization.
Contractor L3Harris was replacing old copper connections with fiber at a remote site when
excessive data reportedly overloaded aging routers or switches. Investigators had not yet
settled whether faulty equipment or installation error supplied the immediate trigger.

FAA leadership said it had no evidence of a cyberattack, nefarious action, or an AI-related
cause. The fact that the stop occurred the day after the Microsoft incident does not connect
them.

## Chase: one defect created downstream payment delays

A Chase problem on November 16 delayed some online, branch, and Zelle transactions. The bank
said transactions were posting normally by approximately 6:30 p.m. Eastern and that customers
retained access to their accounts and funds.

Chase attributed the event to a software bug in an on-premises hardware system and said it was
not cyber-related or systemic.

Some customers at other institutions could see delays when a transfer involved Chase. Zelle said
its own platform remained operational. This is an example of a real dependency ripple, not
evidence that every named bank suffered its own outage.

It also does not connect the banking event to Microsoft, the FAA, United, Apple, the NSA, or
Optimizely.

## United Airlines: a separate 90-minute failure

United experienced a company-wide web-based technology outage on November 16. It delayed some
mainline departures for approximately 90 minutes and affected pilot applications, crew
communications, and final aircraft-weight calculations.

Flights already in progress and United Express flights were not affected. United said it had no
indication of a cybersecurity issue but did not publicly identify the underlying technical
fault.

The United incident happened three days after the FAA stop and was separate from it.

## Apple: an internal update

On November 17, Apple reported disruption to iCloud account access, the App Store, Apple Music,
iCloud Mail, and several education and purchasing services.

Apple attributed the outage to an internal update, not a cyberattack. Its status page showed the
listed incidents resolved by 6 p.m. Eastern that day.

Proximity to other outages is not evidence of a common cause when Apple supplied a distinct
internal explanation.

## NSA: maintenance and urgent patching

A classified NSA internal communications network was disrupted from November 17 to November 20,
more than three days rather than merely two. Employees lost access to an internal
classified-email-like service, while the NSA said mission-critical intelligence capabilities
remained operational.

The agency's public statement described temporary degradation during scheduled routine
maintenance. Later reporting linked the maintenance to patching critical PHP vulnerabilities and
said some systems did not return as expected after updates.

AI tools had helped researchers find the PHP flaws. That is an indirect role for AI in
vulnerability discovery, not evidence that AI attacked or disabled the NSA.

Officials briefed on the incident said it was not a cyberattack. The official statement and
later reported technical detail should remain distinct because the NSA itself gave only the
broader maintenance explanation.

## Optimizely: one real supply-chain-style compromise

The week's confirmed malicious-code event was separate from the infrastructure outages. On
November 16, an attacker exploited a flaw in Optimizely Web Experimentation's account-signup
flow, impersonated users on targeted customer accounts, and inserted malicious JavaScript into
customer projects.

Optimizely said fewer than 5% of its customers were affected, the incident was limited to Web
Experimentation, and it closed the vulnerability and blocked the malicious delivery within three
hours of detection. It described this as unauthorized exploitation rather than a credential
breach.

Report URI identified 188 infected snippets associated with 178 organizations, including BBC and
CNN. The video's “BBC, CNN, and hundreds of others” overcounts that sample; 176 other
organizations were identified.

The injected code implemented capabilities to replace cryptocurrency addresses, capture card
details from site-controlled fields, steal some cookies or screenshots, and deliver iOS
exploits. The number of visitors affected and the amount of stolen payment data remain unknown.

Cards entered inside cross-origin hosted payment fields such as Stripe or Adyen iframes were
outside the script's reach. This illustrates the value of origin isolation, not a guarantee that
all hosted payment flows or all browser users were safe.

Finding compromised third-party JavaScript does not establish that every publisher's own servers
were breached or that every visitor executed a harmful payload.

Neither Optimizely nor Report URI attributed this compromise to ARTEX or AI.

## ARTEX is a real acceleration in offensive tooling

ARTEX is an open-source, Go-based multi-agent penetration-testing framework with six specialized
sub-agents. It can connect to external language models and automate parts of reconnaissance,
credential attacks, exploitation, cloud operations, and reporting.

The creator, known as Autumn-27, released it on GitHub in July 2026 and made the original
repository unavailable on October 8 after reports of abuse. Forks, mirrors, archives, localized
variants, and an ARTEX Pro version remained.

The FBI issued a FLASH about ARTEX on November 13. The publication collected tactics,
techniques, and indicators drawing partly on Microsoft, Google, and security-vendor reporting.

An FBI warning published on the same day as the FAA stop is a temporal coincidence. The FBI did
not attribute the FAA event or the wider outage cluster to ARTEX.

## Hundreds targeted does not mean hundreds compromised

Microsoft says the China-state-aligned actor it calls Storm-0940 used ARTEX from at least
September to target hundreds of organizations globally. The majority of targeting was
unsuccessful.

Several attacks did obtain privileged cloud access. Microsoft observed multiple instances in
which the time from initial targeting to privileged access was less than three hours.

Google separately describes an overlapping campaign as UNC7228. It reported movement from a
first compromised account to deep system access in approximately four hours and, in one case, 15
minutes. The clock began after an account was already compromised, not when the attacker first
selected the target.

These are different measurements from separate observers. The results demonstrate compressed
attack timelines, but they should not be merged into one universal 15-minute compromise rate.

## Hundreds or thousands of attacking agents remain a forecast

ARTEX's documented architecture uses six specialized sub-agents. The reviewed sources show
concurrent multi-target operations, rapid action, and significant scaling potential.

They do not document hundreds or thousands of ARTEX agents in one operation. They also do not
measure a one- or two-person team replacing hundreds of nation-state operators.

It is plausible that agent frameworks let smaller teams run more operations in parallel. The
degree of head-count compression remains unmeasured. Presenting that scenario as an observed
fact overstates the evidence.

## ConnectWise shows why containment is easier than restoration

Microsoft attributes the ConnectWise Cloud Backup supply-chain compromise to Storm-0940 using
ARTEX. That does not make ARTEX an autonomous attacker; it was a framework used by a
human-directed threat actor.

ConnectWise disabled seven vendor application identities and revoked associated credentials on
October 17. These identities supported Cloud Backup and other Microsoft integrations across
customer tenants. Disabling them centrally blocked new authentication quickly.

Restoration was more involved:

- account resets and replacement application credentials began on October 20;
- the affected-environment reset was reported complete on October 21;
- phased service restoration began on October 28;
- each Microsoft 365 tenant required separate authorization for a hardened application;
- all four restoration phases were complete on November 19;
- protection still could not resume for a tenant until its administrator reauthorized it.

The video's October 19 reset date is incorrect. October 28 was not merely continued uncertainty;
it was the start of phased restoration with explicit tenant instructions.

“Putting everything back took weeks” is fair for full service restoration. Some reauthorized
tenants could resume backup earlier, so it should not imply that every tenant waited until
November 19.

The broader lesson holds: revoking a small number of shared identities can contain access
quickly, while rebuilding trust and obtaining consent across many customer tenants takes
coordination.

## Java inventory is a practical defensive bottleneck

On November 17, CISA urged immediate patching of CVE-2026-114938, a critical memory-corruption
flaw in the x86-64 HotSpot JVM's Base64 decoder. Crafted input could crash the JVM and permit
unauthenticated remote code execution.

CISA's first action was to identify affected Java installations. It explicitly warned that Java
runtimes bundled inside third-party applications, container images, and appliances might not
appear as separate software-inventory entries.

The video's suggestion that a supplier may need to confirm an embedded version is a reasonable
operational inference, not CISA's wording.

“Java is everywhere” is rhetoric. The supported point is that Java is widely embedded and that
an incomplete inventory can delay patching even after a fix exists.

## Bank of America's remediation effort is reported, not audited

CNBC reported that Bank of America hired 1,000 contractors to remediate software flaws
identified by Anthropic's Mythos. Bank of America did not supply a primary public disclosure
reviewed here, so the number remains attributed reporting rather than an independently audited
company metric.

The example suggests that faster automated vulnerability discovery can create a large defensive
work queue. It does not establish that every finding was exploitable, equally urgent, or newly
created by AI.

## The Binance recruiting attack used a fictitious-company persona

Binance says an employee was contacted through a legitimate job platform in September by someone
posing as a project director. The campaign included purported HR and CEO interviews for a
fictitious company. During the second interview, the employee was told to download an assignment
containing a malicious repository onto a work computer.

The evidence supports a constructed recruiting operation with fake company roles. “Created an
entire fake company” is stronger because it may imply incorporation or complete corporate
infrastructure that Binance did not document.

Binance labels its report an initial and continuing investigation. Its account should be treated
as a company incident report, not a completed independent forensic judgment.

## Attackers and defenders face different work

An attacker may need only one viable weakness and can abandon failed paths cheaply. Defenders
must understand dependencies, preserve service, close multiple routes, validate repairs, restore
trust, and avoid introducing new failures.

This asymmetry is real, but “attack is easier than defense” is not universal. Well-designed
identity, segmentation, least privilege, browser isolation, reproducible infrastructure,
backups, and practiced recovery can raise attacker cost and reduce restoration time.

AI can assist both sides. Attackers can automate reconnaissance, exploit adaptation, and
concurrent operations. Defenders can use models for inventory, log analysis, detection, patch
prioritization, simulation, and recovery planning.

AI output does not remove the need to verify changes. Microsoft's outage is a reminder that
acting quickly in a complex system can prolong failure when capacity, queues, and dependencies
are poorly modeled.

## Simulation is promising, not an available guarantee

Jones imagines defenders simulating a recovery quickly enough to discover cascading failures
before a real rollout. Digital twins, staging environments, traffic replay, chaos engineering,
and automated analysis already approximate parts of this idea.

A faithful simulation of a global service is difficult. Hidden state, live demand, third-party
dependencies, partial failures, and stale configuration can make a test environment diverge from
production.

AI-assisted simulation may shorten incidents, but the video supplies no measured evidence that
such a system would have prevented Microsoft's cascade or reduced it by a specific number of
hours. That is a practical proposal and forecast.

## Practical preparation

The video recommends a password manager, a family safe word, and a preparedness kit. These are
useful measures when stated more precisely:

- use a reputable password manager and unique passwords;
- enable phishing-resistant multifactor authentication where available;
- verify unusual family requests through a separate channel or agreed phrase;
- keep essential contact, payment, travel, and medical information available offline;
- maintain tested backups rather than assuming cloud access will always work;
- for organizations, inventory dependencies, applications, identities, and embedded runtimes;
- rehearse containment and recovery, including restoring credentials and customer authorization.

A safe word can help challenge an impersonation attempt but should not be treated like a
reusable password shared broadly or stored in insecure messages.

The claim that the internet is “more vulnerable than ever” is not established by one crowded
week. Measurement changes, reporting, service concentration, software complexity, and improved
discovery all affect how many incidents become visible.

## Bottom line

The outage cluster does not reveal one AI cyberattack. Most events had distinct reported causes,
and several providers explicitly ruled out malicious activity. Treating coincidence as
coordination would obscure the operational lessons.

Those lessons are serious. Complex digital services can fail through interactions among old
defects, capacity loss, updates, queues, shared identities, embedded software, and third-party
code. Recovery can take longer than containment because trust and service must be rebuilt safely
across every dependency.

ARTEX adds a separate warning: agentic offensive tools can increase speed and concurrency in
real intrusions. Microsoft and Google document attacks reaching privileged or deep access in
hours and, once, 15 minutes after an initial account compromise.

The appropriate response is evidence-led defense: reliable inventory, least privilege,
independent monitoring, practiced recovery, isolated payment components, cautious AI assistance,
and incident reporting that keeps known causes separate from speculation.

## Sources

- Microsoft, preliminary account of the November 12–14 Microsoft 365 incident.
- FAA and L3Harris reporting on the November 13 departure stop.
- Chase, United, and Apple statements on their separate service disruptions.
- NSA statement on scheduled-maintenance network degradation.
- Optimizely incident report and Report URI technical analysis.
- Microsoft Threat Intelligence, Storm-0940 and ARTEX campaign report.
- Google Threat Intelligence Group, ARTEX and agentic-threat reports.
- FBI FLASH-20261113-001 on ARTEX tactics and indicators.
- ConnectWise, continuously updated Cloud Backup advisory.
- CISA alert for CVE-2026-114938.
- Binance, initial report on the fictitious-company recruiting compromise.
