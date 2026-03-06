# Claude Opus 4.6: The Biggest AI Jump I've Covered — Summary

Opus 4.6 shipped February 5, 2026. Sixteen agents coded autonomously for
two weeks and delivered a 100,000-line Rust C compiler for ~$20,000. A year
ago, autonomous coding topped out at 30 minutes.

Context window expanded 5x (200K to 1M tokens). The key metric is MRCV2
retrieval accuracy: Sonnet 4.5 scored 18.5%, Gemini 3 Pro 26.3%, Opus 4.6
hit 76% at 1M tokens and 93% at 256K tokens. The model can hold 50,000
lines of code and reason across all of them simultaneously.

New "agent teams" feature (internally "team swarms"): multiple Claude Code
instances coordinate through a shared task system with lead/specialist
roles and peer-to-peer messaging. This is how the C compiler was built —
16 parallel agents, each owning a subsystem.

Rakuten deployed Opus 4.6 in production across 50 engineers and 6 repos.
In one day it closed 13 issues autonomously, routed 12 to the right people,
and knew when to escalate. Non-technical Rakuten employees now contribute
to development through the Claude Code terminal.

Side demo: given basic tools and no instructions, Opus 4.6 found 500+
zero-day vulnerabilities in audited open-source code. It independently
analyzed git history to find hastily patched security changes — a method
nobody told it to use.

Two CNBC reporters built a Monday.com-style dashboard in under an hour for
$5-$15 in compute. Anthropic's Scott White calls this "vibe working" —
describing outcomes, not process.

Revenue-per-employee at AI-native companies: Cursor $5M (20 people),
Midjourney $5M (40 people), Lovable $13M+ (15 people). Traditional SaaS
elite is ~$600K. McKinsey targets agent-to-human parity by end of 2026.

Dario Amodei puts odds of a billion-dollar solo-founded company by end of
2026 at 70-80%.

Key takeaway: the relationship between headcount and output is broken.
The question for every org is now agent-to-human ratio and what each human
must excel at to make it work. Infrastructure demand from agent swarms
makes the $650B hyperscale buildout look conservative.

Actionable: touch AI systems built this month, every month. Run multi-agent
sessions on real work. Describe outcomes, not steps. Audit which
coordination hours actually require human judgment.
