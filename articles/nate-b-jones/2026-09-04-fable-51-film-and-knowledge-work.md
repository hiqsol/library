---
title: "Everyone's Testing Claude Fable 5.1 On Code. It Made Me A 37-Second Film."
author: Nate B Jones
channel: AI News & Strategy Daily | Nate B Jones
url: https://www.youtube.com/watch?v=55rDzRkUVdE
date: 2026-09-04 16:00
tags: ai, development
---

# Everyone's Testing Claude Fable 5.1 On Code. It Made Me A 37-Second Film.

 ## Knowledge work needs more than a finished file

Jones tests Claude Fable 5.1 through investment analysis, concise writing, and a generated
architectural film. He treats these as realistic work samples rather than controlled benchmarks.
His central distinction is between producing a complete artifact and making its reasoning easy
for another person to inspect.

The financial assignment concerned GoPro's proposed acquisition by Starman. Models researched
the transaction, built a post-acquisition discounted cash-flow workbook, and prepared an
executive presentation. Jones compared GPT-5.6 Soul at extra-high effort, Fable 5 at extra, and
Fable 5.1 at both low and extra effort.

## Effort changes the quality of review

Fable 5.1 on low produced seven workbook sheets and 13 slides. Jones says formulas worked,
scenario changes affected valuation, and the analysis addressed cash burn and possible
additional funding. The reported base case was $1.15 per share. However, it lacked dedicated
sources and checks sheets and embedded source notes, making assumptions harder to audit.

He stresses that missing Starman financial history prevents treating these modeled values as
established valuations. The transcript is inconsistent in rendering some other scenario prices,
so those figures are not reproduced here as precise results.

At extra effort, Fable 5.1 produced nine sheets and 15 slides. It modeled the businesses
separately, added closing probability, made funding needs explicit, used a weighted average cost
of capital and an exit-multiple check, and linked 26 sources. It distinguished present deal
value from value at closing. Jones's reason to spend more tokens is the additional
decision-relevant questions and inspection detail, not the different share-price estimate.

Soul produced 10 sheets and 10 slides, with a dedicated sources sheet and a checks sheet showing
an explicit pass result. Jones found this especially easy to hand to another analyst. He
preferred Fable's presentation design.

The practical workflow is iterative: use low effort to establish a first version, challenge the
assumptions, use another model to inspect the structure, and spend extra effort when additional
diligence or presentation quality is valuable.

## A 100-word writing test

Jones asked each model to explain Toyota's success in the United States in 100 words. Fable 5
included substantial history but spent scarce space on decorative metaphors. Fable 5.1 retained
more concrete milestones and clearer causal links, including the connection between Japanese
export restrictions and US manufacturing.

Soul used fewer dates and milestones to create a smoother general narrative. Jones would choose
between them according to audience: a general reader may benefit from Soul's flow, while an
executive audience may prefer Fable 5.1's density. He still notices repeated contrast structures
and punctuation habits in Claude's writing, but finds 5.1 easier to steer.

## A film built through software

Given a Seattle property address, a loose brief, and tool access, Fable 5.1 built a 37-second
architectural walkthrough in Blender. Jones says he did not operate Blender himself. The agent
created the house, terrain, interiors, lighting, landscaping, and camera path in code. It
rendered stills, inspected them, revised the scene, checked motion, and rendered the film.

The sequence moved from the exterior through the foyer and living room, then back above the
property. Trees and glass remained stylized. Jones sees it as useful concept communication, not
a substitute for every aspect of professional production. In his comparison, Fable 5's version
was rougher and Soul's was shorter with weaker interior detail.

## Economics and usage limits

Jones reports Fable 5.1 API pricing of $10 per million input tokens and $50 per million output
tokens, unchanged from Fable 5. Cached reads fell from $1 to $0.25 per million tokens. He cites
Anthropic estimates of about 25% lower cost for typical work and about 45% lower cost for
cache-heavy agentic workloads.

These are release-period figures and estimates. API cache economics do not directly describe
subscription allowances. Jones still finds Claude limits tighter than OpenAI's, while reporting
that Fable 5.1 completes more useful work within them, especially at low effort.
