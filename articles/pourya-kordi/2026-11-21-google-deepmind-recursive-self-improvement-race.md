---
title: AI Is Automating More AI Research, but the Recursive Loop Is Still Open
author: Pourya Kordi
channel: Pourya Kordi
url: https://youtu.be/0r5d9yAoeJ4?is=MuwFe5DPeN6Si0Og
date: 2026-11-21 15:58
tags: ai, technology
---

# AI Is Automating More AI Research, but the Recursive Loop Is Still Open

[summary](../../summary/pourya-kordi/2026-11-21-google-deepmind-recursive-self-improvement-race.md)

Google is releasing models faster, executives openly discuss recursive self-improvement, and AI
systems automate growing portions of coding, training-data generation, evaluation, and
scientific work. Pourya Kordi presents these developments as pieces of an approaching
intelligence explosion.

The evidence supports a narrower conclusion. AI-assisted AI development is accelerating, but
current systems still depend on human-selected objectives, architectures, training runs,
evaluators, and deployment decisions. None of the cited projects demonstrates a fully autonomous
system repeatedly building more capable successors.

The video's most important new evidence is not a model release. It is the enormous formal proof
of the Riemann Hypothesis produced by mathematician Levent Alpöge with an internal Claude model.
Independent Lean experts have validated the formal artifact. The result shows unusually
consequential AI-assisted mathematics, while substantial human direction and the absence of a
conventional readable proof make “Anthropic solved it” an imprecise attribution.

## A real acceleration, not seven months of silence

Kordi says DeepMind emerged after seven months of silence with Gemini 4 Argon, Carbon, Hydrogen,
Krypton, Oxygen, and Neon. The broad point about rapid late-2026 releases is correct, but the
list and timeline need correction.

Google publicly documented four Gemini 4 variants:

- Argon entered limited access on September 30 and broader release on October 13;
- Carbon reached trusted cyber defenders on October 28 and broader users on November 10;
- Hydrogen launched on November 12 as a faster model adapted from Carbon;
- Neon launched on November 18 between Carbon's depth and Hydrogen's speed.

Business Insider separately reported Barium as an internal checkpoint. Google has not publicly
confirmed Krypton or Oxygen, and no authoritative reporting identified them during this
fact-check.

The “seven months of silence” framing is also false as a literal release history. Google's
model-card index records Gemini 3.5 Flash in May, 3.6 Flash in July, 3.7 Flash in August, and
3.8 Flash in September. Whether those models were competitive on a particular task is a separate
question.

Google's claims about Neon include steerability and low internal fabrication rates. Descriptions
of a unique “personality” are user impressions, not independently measured capability.

## The leaked strike-team story is reporting, not a Google announcement

Reporting on a leaked April memo said Google formed a strike team to close an agentic-coding gap
with Claude Code. Sergey Brin and DeepMind CTO Koray Kavukcuoglu were reportedly involved.

The memo attributed to Brin called for Google to “urgently bridge the gap in agentic execution”
and turn models into “primary developers.” The Information's reporting was repeated by
TechRadar, but Google did not publish or authenticate the memo.

The safe description is that credible reporting described an internal push for agents that write
final code and assist AI research. It is not direct evidence that Google had automated its full
research pipeline.

## Executives really are using RSI language

In an October 14 Argon roundtable, Brin said Google was beginning to get onto an “RSI
treadmill.” He explained that researchers and models work together on the next model and that
internal checkpoints were already ahead of the public release.

The quotation verifies faster AI-assisted development. Brin's own example still includes
researchers working with models, not a system independently selecting, training, and deploying
its successor.

Sundar Pichai similarly said frontier models would become better at developing the next set of
models in an era of recursive self-improvement. This is a forecast about growing AI
participation in R&D, not evidence that human oversight has already disappeared.

Demis Hassabis drew the distinction explicitly. In a November interview, he called today's phase
one in which humans remain several times more productive while reviewing, architecting, and
writing code. He warned that a future “closed loop” without a human reviewer process could be
faster and dangerous.

The video accurately quotes the warning but then treats the prospective closed loop as nearly
present. Hassabis was identifying the next risky phase, not announcing that DeepMind had entered
it.

## Google's own evaluations remain more restrained

The model cards for Argon and Neon state that the systems had not crossed Google's thresholds
for substantially accelerating ML R&D beyond historical rates or fully automating the work of a
Google AI research team.

Internal thresholds cannot settle the broader policy debate, and company evaluations may miss
future risks. They nevertheless contradict a categorical claim that Google has already closed
the loop.

A useful vocabulary separates three stages:

1. AI tools assist human researchers and engineers;
2. agents automate bounded experiments under human-set goals and evaluators;
3. a system autonomously chooses research, builds and verifies a successor, deploys it, and repeats.

Public evidence strongly supports the first stage and increasingly supports the second. It does
not yet establish the third.

## What Dream-RSI actually improves

Dream-RSI is a real project by researchers affiliated with Google, Google DeepMind, the
University of Maryland, and the University of Virginia. Its name is *Recursive Self-Improvement
through Evolving Worlds*.

A fixed coding or discovery agent explores a task and stores branches and outcomes in a
discovery tree. A separate policy-development agent rewrites executable code controlling
exploration: which branches to continue, how much work to run in parallel, and when to stop.

Recorded outcomes become a replay environment. Candidate exploration policies can be evaluated
on those stored branches without repeating every expensive model call. The best policy is then
deployed to collect another tree and extend the replay pool.

This is recursive optimization of a search-orchestration policy. The base model, evaluator, and
execution interfaces remain fixed. Dream-RSI does not rewrite its foundation model, invent a new
architecture, obtain compute, retrain itself, or deploy a successor without human governance.

## The benchmark gains are task-specific

On one Lasso discovery setup, Dream-RSI used 317 rather than 550 calls with Gemini 3.1 Pro,
about 42% fewer. With Gemini 3.7 Flash, it used 1,879 rather than 3,200 calls, about 41% fewer.

On one ConvDiv GPU-kernel task, its discovered kernel scored 2.09 times higher than fixed
exploration at a comparable budget. Other tasks produced different improvements. The result does
not mean GPU programs generally became twice as fast.

The video also says Dream-RSI improved a coding agent from about 72% to 81%. That number was not
found in the paper or project page and should not be attributed to Dream-RSI without another
source.

Replay is exact only for branches already in the discovery tree. It cannot reveal what would
have happened on unexplored branches, and a policy selected on replay histories can overfit
them.

The study demonstrates useful automated search under fixed evaluators. It is not evidence of
open-ended improvement in general intelligence.

## The nuclear analogy has limits

Nuclear fission is a positive-feedback process because neutrons released by one event can
trigger more fissions. That makes it a vivid analogy for compounding AI development.

The claim that a nuclear chain reaction becomes uncontrollable once started is false in general.
Power reactors use control rods and other systems to sustain, reduce, or rapidly stop a chain
reaction. A critical reactor is stable rather than runaway. A weapon deliberately creates a
rapidly supercritical configuration, and even that reaction ends as the material expands and
disassembles.

AI development has no measured equivalent of the neutron multiplication factor. Chip supply,
energy, experiment duration, model training, verification, deployment gates, human intervention,
and diminishing returns can interrupt the feedback loop.

The analogy identifies a possible positive feedback. It does not establish its speed, stability,
or inevitability.

## AlphaGo is an informative but unusually favorable case

The original AlphaGo learned first from expert human games and then improved through self-play.
It combined policy and value networks with Monte Carlo tree search and defeated Lee Sedol 4–1 in
March 2016. The famous Move 37 occurred in game two.

AlphaGo Zero was a different system published in 2017. It began from random play using only Go's
rules, learned through self-play, and defeated the earlier Lee-beating system 100–0 after three
days of training.

The video blends these systems when moving from Lee Sedol to Zero. More importantly, AlphaGo
Zero improved playing strength under a fixed human-designed architecture, optimizer, learning
rule, game, and objective. It did not redesign the process that built it.

Go offers exact rules, cheap self-play, a clear terminal result, and a stationary objective.
Frontier AI research involves ambiguous goals, expensive experiments, delayed effects, hidden
regressions, security risks, and disputed measures of progress.

Policy-guided search is central to AlphaGo and many planning systems. It does not “underlie all
AI,” and ordinary language-model inference need not use explicit tree search.

AlphaGo shows that a fixed learning system can improve quickly in a highly verifiable
environment. It does not prove that scientific research has the same structure.

## DeepSeek automates task creation but also changed its model

DeepSeek-V4.1-Flash uses agents to generate, solve, inspect, and repair coding tasks and
environments. Its infrastructure supports very large numbers of synthesized environments. This
is material automation of post-training data and evaluation work.

The report says DeepSeek did not introduce a novel post-training algorithm, retaining the broad
supervised fine-tuning, reinforcement-learning, and on-policy-distillation recipe.

The video's conclusion that DeepSeek therefore did not touch its “main algorithm” is inaccurate.
The model includes substantial architectural and systems changes, including sparse attention,
memory, residual-mixing, caching, and speculative-decoding changes.

DeepSeek reports DeepSWE v1.1 rising from 54.4 to 74.2 and Terminal-Bench 2.1 from 82.7 to 90.6.
Those numbers are vendor results. Architecture, pretraining, data scale, infrastructure, and
post-training all changed, so generated tasks alone cannot receive causal credit for the gains.

This is an automated training factory under a human-designed program, not a deployed model
deciding to redesign and retrain itself.

## Kimi K3 builds elaborate simulated work environments

Kimi K3 is an open-weight, natively multimodal mixture-of-experts model. “Open source” is less
precise because the released weights use the Kimi K3 License rather than a conventional
open-source software license.

Its report describes persistent agent environments resembling Gmail, Notion, Slack, and Canvas,
with professional workflows across multiple applications and long trajectories. Some training
attempts use thousands of tool calls and millions of context tokens.

Kimi also builds a self-evolving knowledge graph through recursive, agent-driven web
exploration. The word “recursive” here describes expansion from broad subjects to fine-grained
concepts. It does not mean that Kimi rewrites its weights or training algorithm.

On one showcased camera-repair-management replication task, Kimi reports a 1.000 completion
curve, compared with 0.918 for Claude Opus 4.8, 0.893 for GPT-5.5, and 0.560 for Kimi K2.6.

The video's rounded percentages are accurate. This was one verifier-assessed task, not a
multi-task claim that Kimi always reconstructs software perfectly.

The DeepSeek and Kimi reports show extensive automation of curriculum creation and agent
training. They do not demonstrate autonomous model development from objective selection through
deployment.

## The Riemann result is real and needs careful attribution

The video's aside that Anthropic “apparently” solved the Riemann Hypothesis refers to a
development announced one day before publication.

Anthropic mathematician Levent Alpöge, working extensively with an internal Claude model,
released a huge Lean proof of the Riemann Hypothesis and a Dirichlet-L-function version of the
Generalized Riemann Hypothesis on November 20.

Independent Lean and Mathlib experts reported full confidence that the artifact states the
intended Riemann Hypothesis and formally proves it. MIT verification compiled all 175,187
modules, checked the export with independent kernels, compared the headline statements, and
reproduced the roughly 61.57-billion-byte raw export.

That is unusually strong verification of formal validity. It should not be conflated with
Anthropic's earlier result improving a lower bound from 41.6% to 67.2% for zeros known to lie on
the critical line. Anthropic explicitly said the earlier work did not prove the hypothesis.

“Anthropic solved it” obscures the collaboration. Alpöge supplied substantial human guidance and
conceptual steering; Claude generated and formalized a vast amount of work. The proof has not
yet been distilled into a conventional human-readable mathematical argument.

The careful conclusion is that an AI-assisted human mathematician produced a formally verified
proof, while mathematical digestion, conventional exposition, and institutional recognition will
take more time.

## Research taste is not one thing

Kordi calls “research taste” or long-horizon intuition the final missing trigger for an
intelligence explosion. Psychology supports a more qualified account.

Daniel Kahneman and Gary Klein argued that trustworthy intuition is most likely when an
environment has sufficiently valid, learnable regularities and people have adequate
opportunities to learn them. Repeated practice and reliable feedback help, but their paper does
not give the video's four items as independent necessary-and-sufficient conditions.

Research includes tasks with very different feedback quality. Compiler speed, model loss, memory
use, and benchmark performance can be measured quickly. Choosing an important scientific
question, identifying a misleading proxy, or anticipating a technology's social value may take
years and remain confounded.

A system can automate the measurable components without possessing general scientific judgment.

## Expert-forecasting evidence does not erase expertise

Philip Tetlock studied 284 professionals and collected 82,361 political and economic forecasts.
The average performance was unimpressive: subject specialization did not consistently help,
simple baselines were often competitive, and prominent forecasters could be overconfident.

Saying that every expert was no better than random is too strong. The study used multiple
probabilistic comparisons, and later forecasting work found persistent differences between
people and gains from training, updating, aggregation, and team design.

A separate study followed 6,591 patients treated by 170 psychotherapists. Average patient
improvement did not rise with therapist experience and declined slightly, while therapists
varied and early termination became less common.

These findings caution against assuming that tenure produces better judgment. They do not show
that research taste is imaginary or that a slightly-better-than-random selector is sufficient
for frontier science.

## Historical text can test forecasting, with leakage risks

A 2019 Nature study trained word embeddings on about 3.3 million materials-science abstracts. In
a historical test, three of its top five thermoelectric candidates were later proposed or
studied.

The model identified predictive signals in literature. It did not synthesize or experimentally
validate the materials, and later research attention is not a clean measure of scientific merit.

TypewriterLM is also real. It is a 7.24-billion-parameter model trained on a heavily filtered
corpus from 1700 through 1913. The project aims to create a useful platform for temporal
experiments.

The cutoff is imperfect. The authors found post-1913 leakage, and modern models contributed to
some instruction generation and judging. TypewriterLM demonstrated qualified language
capability, not scientific forecasting or research-taste training.

Training temporally bounded models to predict later discoveries is a plausible proposal.
Historical outcomes could provide far more practice than a human career permits. But the
proposal faces serious problems:

- later metadata, citations, terminology, tools, or OCR can leak the answer;
- history records what was funded and published, not every promising failed path;
- later success is not a clean label for ex-ante scientific quality;
- scientific institutions and causal relationships change over time;
- optimization can learn period-specific shortcuts;
- modern tools can silently contain post-cutoff knowledge;
- performance on retrospective predictions may not transfer to new research.

No cited experiment shows that historical back-training creates general research taste.

## What a closed improvement loop would require

Current projects provide some candidate ingredients: capable coding agents, generated
environments, automated experiments, tool use, verifiable evaluations, and models that help
build later models.

A fast closed loop would also need:

1. systems able to perform most frontier R&D, including interpretation and integration;
2. evaluations that detect contamination, reward hacking, regressions, and shifted capabilities;
3. improvements that make the next research cycle more effective;
4. gains that exceed errors and experimentation costs;
5. training, evaluation, hardware, and approval cycles short enough to compound;
6. available compute, energy, chips, data, simulators, and experimental access;
7. room for repeated gains despite diminishing returns and local optima;
8. improvements that transfer beyond the evaluator used to select them;
9. operational permission to run and deploy successive systems;
10. stability against accidents, deception, cyber compromise, and objective drift.

These conditions are neither proven jointly sufficient nor all known to be necessary.
Long-horizon research taste is not demonstrably the single final bottleneck.

## The sponsor segment is marketing, not evidence

The video includes a paid segment for Cardboard, a YC-backed AI video editor. The demonstration
shows advertised editing, effects, music, recipes, and agent integrations.

The segment is identified as sponsored. Its product claims and selected examples are marketing
and do not provide independent evidence for the broader RSI argument.

## Bottom line

The video's core observation is correct: AI systems now help design successors, generate
training environments, run experiments, optimize search policies, and contribute to major formal
mathematics. Google leaders publicly expect the cycle to accelerate and explicitly worry about
closing it.

The stronger thesis is not established. Dream-RSI modifies an orchestration policy around a
fixed model. DeepSeek and Kimi automate training components inside human-designed pipelines.
Gemini's model cards say the systems have not crossed Google's automated-R&D thresholds.
Historical back-training is a proposal, and AlphaGo's clean game loop does not map directly onto
open-ended science.

AI-assisted AI R&D is a consequential feedback loop worthy of safety controls, independent
evaluation, and governance before human review becomes nominal. It is not yet a demonstrated
autonomous intelligence explosion.

## Sources

- Google, Gemini 4 Argon, Carbon, Hydrogen, and Neon announcements and model cards.
- Google DeepMind, Argon roundtable with Sergey Brin, October 14, 2026.
- Masters of Scale, Demis Hassabis interview, November 5, 2026.
- *Dream-RSI: Recursive Self-Improvement through Evolving Worlds*.
- DeepSeek, DeepSeek-V4.1-Flash technical report.
- Moonshot AI, Kimi K3 technical report.
- Lean community and MIT independent checks of the Alpöge–Claude RH proof.
- DeepMind, AlphaGo and AlphaGo Zero papers and historical pages.
- Kahneman and Klein, *Conditions for Intuitive Expertise*.
- Tetlock, expert political and economic forecasting study.
- Goldberg et al., longitudinal psychotherapist-outcomes study.
- Tshitoyan et al., materials-science word embeddings, *Nature* 2019.
- *A Language Model from 1913: Pretraining on Historical Text*, arXiv:2606.02991.
