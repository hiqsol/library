---
title: A Week of Outages Exposed Fragile Infrastructure, Not One AI Attack
author: Nate B. Jones
channel: AI News & Strategy Daily | Nate B Jones
url: https://youtu.be/fFeyE4nINqs?is=a7TkRS1Qx4gPD6y-
date: 2026-11-22 18:00
tags: ai, technology
---

# A Week of Outages Exposed Fragile Infrastructure, Not One AI Attack

[article](../../articles/nate-b-jones/2026-11-22-week-of-unrelated-infrastructure-outages.md)

Microsoft, the FAA, Chase, United, Apple, and the NSA suffered disruptions within six days. Incident
reports identify different causes and provide no evidence of one coordinated AI or ARTEX attack.

Microsoft's outage came from a months-old defect, gateway failure, and reduced capacity. Recovery
traffic repeatedly overwhelmed servers, extending restoration beyond 24 hours. Microsoft explicitly
ruled out malicious activity, cyber causes, and AI agents.

The FAA stopped departures for about 4.5 hours during a network upgrade. Chase reported a software
bug, United had a separate 90-minute technology outage, and Apple blamed an internal update. None
reported evidence of a cyberattack.

An NSA internal network was disrupted for more than three days during maintenance and reported PHP
patching. Mission-critical systems stayed operational. AI helped find the vulnerabilities; it did
not attack or disable the network.

Optimizely suffered a separate compromise. Malicious JavaScript reached 188 snippets tied
to 178 organizations. It could capture cards from site-controlled fields, while hosted cross-origin
payment iframes remained inaccessible.

ARTEX is an open-source offensive framework with six specialized sub-agents. Microsoft says a
China-aligned actor used it to target hundreds of organizations, mostly unsuccessfully. Google saw
one campaign reach deep access 15 minutes after an account was already compromised.

No reviewed source documents hundreds or thousands of ARTEX agents in one operation or proves that
one or two people can replace hundreds of operators. Those are forecasts, not observations.

ConnectWise contained its compromise by disabling seven application identities on October 17.
Restoring service required new credentials and authorization for every Microsoft 365 tenant;
phased restoration began October 28 and finished November 19.

CISA's Java alert illustrates another bottleneck: runtimes embedded in applications, containers, and
appliances may be absent from inventories. Finding every affected instance can take longer than
publishing a patch.

The core lesson survives the corrections. Attackers need one viable weakness, while defenders must
map dependencies, preserve service, verify repairs, rebuild trust, and restore each integration
without creating another failure.

AI can accelerate attacks and help defenders with logs, inventory, patching, and recovery.
Model output still requires verification, especially when rapid changes can destabilize production.

Useful preparation includes unique passwords, phishing-resistant MFA, tested backups, offline copies
of essential information, dependency inventories, and rehearsed restoration. A family safe word can
help challenge impersonation but should not become a broadly shared password.

The evidence shows fragile infrastructure and faster agent-assisted cyber operations—not one attack
behind the week's outages.
