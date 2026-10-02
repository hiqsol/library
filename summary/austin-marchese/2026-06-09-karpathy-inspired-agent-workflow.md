---
title: "A Better Way to Work With AI Agents—Without Inventing a “Karpathy Method”"
author: Austin Marchese
channel: Austin Marchese
url: https://youtu.be/7zZy1QTvokM?is=VWe3HfSD_NFgsRxg
date: 2026-06-09 16:00
tags: ai, development
---

# A Better Way to Work With AI Agents—Without Inventing a “Karpathy Method”

Austin Marchese’s video presents a useful three-part workflow for AI agents:
specification, verification, and a persistent working environment.
The attribution is the problem.
Karpathy did not say “stop prompting Claude,” name a “Karpathy method,” define those
three layers, or claim they make people build 10× faster.
The framework is Marchese’s synthesis, inspired by Karpathy’s Sequoia AI Ascent talk.
What Karpathy did argue is still valuable: professionals remain responsible for a
detailed spec, human oversight, security, judgment, and whether the system makes sense.
His [talk summary](https://karpathy.bearblog.dev/sequoia-ascent-2026) also describes
agent capability as uneven and stresses investing in one’s setup.
His [verifiability thesis](https://karpathy.bearblog.dev/verifiability) helps explain why
code, math, and games often benefit from cheap feedback while ordinary context stays jagged.
His [animals-versus-ghosts essay](https://karpathy.bearblog.dev/animals-vs-ghosts) warns
against treating a model like a motivated human colleague.
Marchese turns those ideas into practical advice: interview the user to uncover the real
goal, work in reviewable increments, and require explicit approval of key decisions.
Define acceptance criteria before execution, but test substance rather than format alone.
Use another model to find defects, not to certify truth through agreement.
Check external systems after consequential actions and retain human review where needed.
For the environment, keep concise project instructions in `CLAUDE.md`, reusable procedures
in skills, and sourced knowledge in maintained files.
Anthropic says [`CLAUDE.md`](https://code.claude.com/docs/en/memory) provides context;
it is not an enforced security boundary or necessarily reinjected on every prompt.
Use [hooks](https://code.claude.com/docs/en/hooks), OS permissions, sandboxing, and narrow
credentials for constraints that must not depend on model compliance.

Karpathy’s [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
is persistent derived knowledge, not model training merely because files sit on disk.
Skills also do not improve automatically; failures must be captured, edited, and retested.

Do not equate faster output with delivered value.
Measure correctness, rework, incidents, user impact, and full workflow cost.
The video’s 10× claim is unsupported, while Boris Cherny’s “2–3× quality” statement is
practitioner advice without a disclosed benchmark or universal metric.

The supplied transcript uses automatic captions and may contain recognition errors,
omissions, lost capitalization, and incomplete text for prompts shown only on screen.

## Sources
- [Karpathy’s AI Ascent summary](https://karpathy.bearblog.dev/sequoia-ascent-2026)
- [Karpathy on verifiability](https://karpathy.bearblog.dev/verifiability)
- [Karpathy on animals and ghosts](https://karpathy.bearblog.dev/animals-vs-ghosts)
- [Anthropic: memory and hooks](https://code.claude.com/docs/en/memory)
- [Austin Marchese’s video](https://www.youtube.com/watch?v=7zZy1QTvokM)
