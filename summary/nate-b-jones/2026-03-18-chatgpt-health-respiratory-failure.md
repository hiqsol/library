---
title: ChatGPT Health Identified Respiratory Failure. Then It Said Wait.
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=4HeS_C02yAE
date: 2026-03-18 00:00
tags: ai
---

# Summary: ChatGPT Health Identified Respiratory Failure. Then It Said Wait.

[article](../../articles/nate-b-jones/2026-03-18-chatgpt-health-respiratory-failure.md)

## Core Claim

Mount Sinai physicians tested ChatGPT Health using factorial design (same scenarios, 16 context
variations) and found four structural failure modes that apply to all AI agents — not just
medical ones.

## The Documented Failure

ChatGPT Health told a patient with respiratory failure to wait 24–48 hours rather than go to the
ER immediately. This is directly documented in the paper.

## Four Failure Modes

**1. Inverted U** — Models perform best on routine middle-of-distribution cases and worst on edge
cases, which is precisely where stakes are highest. An 87% accuracy score can mask silent
failures at the tails. Averages by definition hide this.

**2. Agent Knows But Does Not Act** — Reasoning traces and final answers operate as
semi-independent processes. The model correctly identified respiratory failure in its reasoning;
its output said "wait." Research shows models fail to update answers based on their own reasoning
more than 50% of the time. Chain of thought is not a reliable explanation of model decisions
(Oxford AI Governance Initiative).

**3. Social Context Hijacks Judgment** — When a family member said "the patient looks fine,"
the system was 12× more likely to recommend less urgent care. Any agent combining structured data
with unstructured human language is vulnerable to this anchoring effect. The bias is subtle and
individually defensible per decision, but systematically wrong.

**4. Guardrails That Fire on Vibes, Not Risk** — The system activated more reliably on vague
emotional distress than on concrete self-harm threats. Guardrails were matching surface language
patterns, not clinical risk taxonomy. This is the difference between the appearance of safety and
actual safety.

## Four-Layer Architecture Response

- **Layer 1: Progressive autonomy routing** — Shadow mode: agent observes human on edge cases
  until it earns autonomy on those cases through measured performance.
- **Layer 2: Deterministic validation** — Rules-based checks comparing reasoning trace to output
  (e.g., if reasoning flags EDD but output says standard risk → escalate). Do not ask the model
  to catch its own inconsistencies.
- **Layer 3: Continuous flywheel** — Bias toward false positives. Review positives. Audit passed
  runs for defects. Turn defects into new eval cases. Almost nobody does the last step.
- **Layer 4: Factorial stress testing** — Deliberately add controlled stressors (social cues,
  contradictory context, time pressure) to scenarios and measure output shift. Variation types
  are domain-general; scenarios are domain-specific. Enterprise scenarios can be
  semi-automatically generated from historical data.

## Key Insight

Most eval system work should be front-loaded. Variation-type libraries and LLM-as-judge schemas
are built once. Ongoing cost shrinks as the flywheel matures.

AI insurance for agents is coming. Insurers will require evidence of eval infrastructure. This
will not remain optional.
