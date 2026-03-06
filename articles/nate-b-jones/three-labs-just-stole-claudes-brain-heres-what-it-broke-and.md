# Three Labs Just Stole Claude's Brain — Here's What It Broke

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=0v9ixCWNhPo)
- **Author:** Nate B Jones
- **Date:** 2026-02-25 15:00

---

## The Extraction

Three Chinese AI labs — DeepSeek, Moonshot, and MiniMax — ran 16 million
automated conversations with Claude across 24,000 fake accounts to steal
its capabilities. They used Hydra-cluster architectures of fraudulent
accounts, proxy services to evade geographic restrictions, and in MiniMax's
case, pivoted within 24 hours of a new model release to capture the latest
capabilities before anyone could stop them.

Everyone is calling this Cold War. They are wrong. This is a Napster problem.

## Not a China Problem — A Pressure Gradient

The most valuable intelligence ever created by American companies is stored
as math — weightless, copyable, extractable through a chat window. The gap
between what frontier labs have and what everyone else can access creates a
pressure gradient. When one side has capabilities worth trillions and the
other side can extract them for thousands, the information always moves.

Distillation should be framed as piracy, not espionage. As the music
industry learned in 1999 and the film industry learned in 2003, piracy
doesn't stop. It slows down. The question is the speed of that slowdown
versus the capability gain in frontier models, which are doubling roughly
every 90 days.

## What Distillation Actually Produces

Distillation does not produce a copy. It produces a compression — and like
a lossy MP3, the characteristics matter enormously.

A frontier model like Opus 4.6 is trained on a vast, diverse corpus over
months of compute. It occupies a high-dimensional capability space — a wide
manifold. It can reason about code, navigate ambiguous instructions, use
tools in novel combinations, maintain coherence over long workflows, recover
from errors, and adapt when plans fail.

A distilled model is trained on a subset of the frontier model's outputs.
It performs well on the specific behaviors the distiller targeted but
occupies a narrower manifold. It falls off more steeply outside that
distribution. Think of it as NFL highlights vs. the full game — you see
less ads but also much less football.

## The Operations in Detail

**DeepSeek:** 150,000 exchanges targeting Claude's reasoning capability,
generating chain-of-thought training data at scale. Prompts asked Claude to
"imagine and articulate the internal reasoning behind a completed response
and write it out step by step." Also generated censorship-safe alternatives
to politically sensitive queries about dissidents, party leaders, and
authoritarianism — training data to help DeepSeek's models steer
conversations away from topics the Chinese government doesn't want discussed.
Anthropic traced accounts to specific researchers through payment methods
and request metadata.

**MiniMax:** Over 13 million exchanges focused on agentic coding and tool
orchestration — the largest of the three operations. Detected while still
active, before the model being trained was released. When Anthropic shipped
a new model mid-campaign, MiniMax pivoted within 24 hours, redirecting nearly
half their traffic. A single proxy network managed over 20,000 accounts
simultaneously, mixing distillation traffic with unrelated customer requests
to make detection harder.

**Moonshot:** 3.4 million exchanges across hundreds of fraudulent accounts
targeting agentic reasoning, tool use, computer use, agent development, and
computer vision. Later shifted to extracting and reconstructing Claude's
reasoning traces directly. Anthropic attributed the campaign through request
metadata matching public profiles of senior Moonshot staff. The result is
Kimi.

## The Performance Shadow on Agentic Work

The brittleness problem is widely misunderstood, partly because benchmark-
maxing obscures it. MiniMax trained on Claude's agentic coding outputs.
The resulting model scores well on coding benchmarks because benchmarks test
exactly what the distiller optimized for. An enterprise buyer running
standard evals might conclude the models are equivalent. They would be wrong.

The distilled model learned to produce outputs that look like Claude's on
coding tasks. It did not learn the underlying representational structure
that allows Claude to:

- Generalize across task types
- Recover from unexpected failures
- Use tools in combinations it wasn't specifically trained on
- Maintain coherent reasoning across extended autonomous workflows

The performance shadow between frontier and distilled models on short,
well-defined tasks is relatively narrow. On extended agentic work, it is
large, growing, and no benchmark captures it today because the evals for
sustained autonomous generality don't exist yet.

### Practical Testing with Kimi K2

Kimi K2 excels at PowerPoint generation — beautiful design, clean execution,
fast iteration. But on sustained agentic work requiring autonomous obstacle
navigation, multi-hour workflows, and tools used for purposes the prompts
didn't specify exactly, performance drops in ways benchmarks don't capture.

A frontier model encounters an unexpected error mid-task and knows how to
reroute — tries a different library, restructures its approach, asks for
clarification. A narrower model encounters the same error and either fails,
loops, or produces a technically valid but strategically incorrect
workaround. It doesn't have the representational depth to understand why
the original approach was chosen.

## The Economics of Extraction

MiniMax ran 13 million exchanges. At Opus 4.6's published API pricing ($15
per million input tokens, $75 per million output): roughly $2 million in
API costs — likely less given proxy discounts and fraudulent account abuse.
That extracts capabilities that cost $2 billion to develop.

A 1,000-to-1 return on theft. No rational economic actor leaves that on
the table.

## The Time Edge

If distillation is inevitable, the point of prevention is time. When
capabilities double every 90 days, a three-month lead is non-trivial:

- Deploying a capability first vs. second
- Establishing market position before competitors ship a distilled version
- Having a 3-6 month head start on developing what comes next

Anthropic's countermeasures (behavioral fingerprinting, detection
classifiers, access controls) won't stop distillation. They will slow it.
In a landscape of exponential capability curves, slowing acquisition by
weeks or months creates real competitive advantage — exactly like DRM in
music, copy protection in software, and anti-piracy in film. None stopped
copying. All imposed friction. The friction was where the money lived.

## This Is Universal, Not Just Chinese

The incentive to distill applies to every lab that is not Google, Anthropic,
or OpenAI. The compute to train a frontier model from scratch is billions.
The compute to distill is orders of magnitude lower. Smaller American labs,
European startups, open-source projects, academic research groups, government
contractors — all face the same structural incentive.

Even Meta, with virtually unlimited compute, pursued capabilities
substantially through talent acquisition. Zuckerberg personally recruited
researchers from Google, OpenAI, and Anthropic with nine-figure packages.
He acquired Scale AI in a $14 billion deal at least partly about acquiring
Alexander Wang and his team's expertise. When Llama 4 underperformed, Zuck
went shopping for people who'd done the hard work elsewhere.

Talent acquisition operates on the same principle as distillation: acquiring
existing intelligence is cheaper than developing it independently.

When DeepSeek released R1 and the market gasped at Chinese-lab reasoning on
a "modest budget," the correct question was not "how did they do it cheaply?"
but "what fraction was independently developed?"

## The Task Scope Framework

Think of AI tasks on two axes:

**Horizontal (Task Scope):** Narrow and well-defined (classify email,
summarize doc) to wide and open-ended (debug system across six repos over
three days, build prototype from vague spec).

**Vertical (Model Provenance):** Frontier-trained at top (Opus 4.6,
GPT-5.3, Gemini 3.1 Pro) vs. distilled/derivative at bottom.

On narrow tasks, the vertical gap barely matters — distilled models handle
email classification at 90%+ of frontier quality for a fraction of the
cost. On wide tasks, the gap is a chasm. The distilled model looks fine
for the first hour or two but by hour 4-8, you encounter errors outside
the distilled training data.

**Match provenance to scope.** Use distilled models aggressively for narrow
tasks. Reserve frontier models for work requiring generality, sustained
coherence, and handling situations the training data didn't anticipate.

## The Off-Manifold Probe

Take a complicated task in your domain — something requiring multiple steps,
tool use, and judgment. Run it on different models. When both succeed, change
one constraint. Watch what happens:

- Does the model adapt, identifying which reasoning transfers and which
  needs revision?
- Or does it regenerate everything from scratch, or worse, force-fit the
  old solution to new constraints?

This test reveals more about representational depth than leaderboard scores.
A generalizable model successfully tackling the problem and running out of
structural memory looks very different from a distilled model losing
coherence or failing at tool use.

## Takeaways

1. **Assume frontier capabilities will leak.** The question is speed, not
   possibility. Every safeguard is a speed bump, and speed bumps matter
   because capability curves are exponential. A three-month edge is
   meaningful.

2. **Distilled models are systematically worse in ways benchmarks don't
   capture** — and those ways matter most for the highest-value agentic
   use cases. Test for generality. Use the off-manifold probe.

3. **Model routing is now a competitive advantage.** "Which AI should I
   use?" is the wrong question. "Which AI for which problem, given how
   these models were built and what that implies about their actual
   capabilities?" is the right one.

AI capabilities are becoming like water — they seep through every crack.
Export controls, detection systems, and fingerprinting are dams and levees.
They work, they buy time, but the pressure behind them increases with
every capability gain. The Napster era looks quaint by comparison.
