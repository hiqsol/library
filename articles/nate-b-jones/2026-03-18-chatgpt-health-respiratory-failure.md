---
title: ChatGPT Health Identified Respiratory Failure. Then It Said Wait.
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=4HeS_C02yAE
date: 2026-03-18 00:00
tags: ai
---

# ChatGPT Health Identified Respiratory Failure. Then It Said Wait.

[summary](../../summary/nate-b-jones/2026-03-18-chatgpt-health-respiratory-failure.md)

## The Mount Sinai Study

Physicians at the Mount Sinai Health System in New York City studied ChatGPT Health — a tool
OpenAI positioned as a responsible alternative to asking medical questions directly to ChatGPT.
The researchers used a rigorous **factorial design**: the same clinical scenarios were run across
16 contextual variations to expose hidden failure modes.

Key finding: ChatGPT Health recommended waiting 24–48 hours for a patient showing signs of
**respiratory failure** rather than going to the ER immediately. That is not an edge case in the
paper — it is a documented example. The stakes here are literally life or death.

---

## Four Failure Modes of AI Agents

The paper reveals four structural failure modes that apply far beyond medicine.

### 1. The Inverted U

ChatGPT Health handled textbook emergencies (classic stroke, severe anaphylaxis) and clearly
minor conditions reasonably well. Failures concentrated at the **extreme edges** of the
distribution.

This is a characteristic LLM production pattern:
- Models are trained on distributions where the middle is densely represented and edges are sparse.
- They perform best on routine cases that any rules engine could handle.
- They perform worst where stakes are highest.

An accuracy dashboard showing 87% can mask silent failures at the tails. Examples:
- An accounts-payable agent processes routine invoices perfectly but misses a slightly modified
  duplicate.
- A claims agent handles fender-benders fine but misses a third claim from the same address in
  14 months.

**So what:** No eval suite designed to measure average accuracy will surface this pattern.
Aggregate numbers look good precisely because they average over the problem.

### 2. The Agent Knows But Does Not Act

In the Mount Sinai study, the system's own reasoning chains correctly identified dangerous
clinical findings — and then the final recommendation contradicted them. The reasoning said
"early respiratory failure." The output said "wait."

This is not a glitch. Research on chain-of-thought faithfulness confirms it is a **structural
property** of how LLMs generate outputs:
- Reasoning traces and final answers operate as semi-independent processes.
- Models sometimes produce correct answers even when incorrect reasoning chains are inserted —
  confirming the link between stated reasoning and output is weak.
- Models fail to update answers in response to logically significant changes in their reasoning
  more than 50% of the time.
- Oxford's AI Governance Initiative has argued chain of thought is fundamentally unreliable as
  an explanation of a model's decision process.

**So what:** If your compliance agent correctly identifies an enhanced-due-diligence jurisdiction
in its reasoning trace but classifies the case as standard risk in its output, you will not catch
that unless you explicitly compare reasoning to output. The fix must be architectural, not at the
model level.

### 3. Social Context Hijacks Judgment

When a family member said "the patient looks fine," triage recommendations shifted dramatically.
The system was **12× more likely** to recommend less urgent care when this framing was present.

Any agent processing inputs that combine structured data with unstructured human language is
vulnerable:
- Structured data should drive the decision.
- Unstructured language creates a framing effect that often anchors the response.
- The bias is subtle: the agent makes a slightly shifted call that is individually defensible but
  systematically wrong.

Examples that generalize:
- A vendor selection agent sees a note from a senior VP saying "I'm confident in this choice."
  Its analysis should be identical with or without that note — but it often isn't.
- A lending agent reads an employer letter describing an applicant as a "valued longtime
  employee." The positive framing shifts the risk assessment, even though the letter contains no
  material financial data.

**So what:** Without a study design that holds the scenario constant and varies only the
unstructured context input, this bias is invisible in standard evaluations.

### 4. Guardrails That Fire on Vibes, Not on Risk

ChatGPT Health's crisis-intervention guardrails fired much more reliably on vague emotional
distress than on concrete threats of self-harm. Mount Sinai's chief AI officer: "The alerts were
inverted relative to clinical risk."

The guardrails were matching surface-level language patterns and emotional tone — not the actual
risk taxonomy. This is the distinction between **testing for the appearance of safety** versus
**testing for safety**.

Example that generalizes:
- A security agent flags an email labeled "Confidential Financial Data" even if it's a public
  quarterly press release sent to a safe list.
- The same agent passes on an employee exporting 50,000 customer records to a personal Dropbox
  because the employee described it as "a backup of project files."

**So what:** The system will report that it is doing well, and will have grounds for that
assessment. You have to know enough to say "actually, this recommendation is wrong, and here
is why."

---

## A Four-Layer Evaluation Architecture

### Layer 1: Progressive Autonomy Routing

Route agents toward progressive autonomy, not complete autonomy from day one:
- High-confidence, low-stakes decisions → trust the agent.
- Extreme edge cases → put a human in the loop.
- Use **shadow mode**: run the agent alongside the human. The human resolves the edge case. The
  agent observes. Over time, measure what percentage of edge cases the agent resolves correctly
  before granting full autonomy on those cases.

### Layer 2: Deterministic Validation

Use rules-based checks to verify obvious structural consistencies — not the LLM. Example:

> "If the reasoning trace contains any enhanced-due-diligence flag AND the classification is
> standard risk → escalate."

Do not ask the model to catch its own inconsistencies. Get an external perspective that
mechanically compares stated reasoning to output.

### Layer 3: Continuous Flywheel

Bias your eval system toward **false positives** (you would rather flag too much than miss
real failures in high-stakes decisions). Then:
1. Review flagged positives to determine whether they are true or false.
2. Update the eval rulebook based on what you learn.
3. Also audit a sample of runs that the LLM-as-judge passed as good. When you find a defect in
   a "passed" run, turn it into a new eval case.

Almost nobody does step 3. It is characteristic of high-performance systems.

### Layer 4: Factorial Stress Testing

The gold standard — what Mount Sinai actually did. Take a set of scenarios and deliberately add
controlled stressors to each:
- A social cue minimizing severity.
- A contradictory piece of context.
- A time pressure element.
- A hedging qualifier.

Measure whether the output shifts when the unstructured context changes. This isolates which
factors are actually driving agent behavior.

**Scaling this:**
- Variation *types* (social pressure, tool call failure, extreme risk, human out of the loop)
  are domain-general and stable — build them once.
- Specific *scenarios* are domain-specific — one scenario per domain for each variation type.
- Enterprise scenarios can be semi-automatically generated from historical data: processed
  claims, approved procurements, compliance screenings, customer chat logs.

---

## The Cost Reality

Most of the effort to build a good eval system should be **front-loaded**, not ongoing:
- The scenario-type library is built once.
- The LLM-as-judge schema is a one-time investment.
- Specific scenario creation requires domain expert time once.
- Continuous operation is designed to minimize human involvement over time as the flywheel
  matures.

The question is not whether your agents have blind spots. They do. The question is whether you
have built infrastructure to find those blind spots before your customers do.

Nate Jones also notes: AI insurance for agents is coming. Insurers will require evidence of
eval infrastructure before issuing policies. This will not be optional.
