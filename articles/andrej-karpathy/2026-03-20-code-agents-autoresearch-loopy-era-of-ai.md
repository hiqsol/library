---
title: Code Agents, AutoResearch, and the Loopy Era of AI
author: Andrej Karpathy
channel: No Priors
url: https://youtu.be/kwSVtQ7dziU
date: 2026-03-20 00:00
tags: ai
---

# Andrej Karpathy on Code Agents, AutoResearch, and the Loopy Era of AI

## The "AI Psychosis" State

Karpathy opens the conversation by describing a persistent mental state he calls "AI psychosis" — a kind of frenzied awareness of how much has changed combined with constant anxiety about not fully exploiting what is now possible.

The inflection point was December 2025. Before that month, his workflow was roughly 80% writing code himself and 20% delegating to agents. After it, the ratio inverted to 80%+ delegation, and by the time of this recording the gap had widened further. His words:

> "I don't think I've typed like a line of code probably since December basically. Which is like an extremely large change."

He describes walking around telling people — including his parents — about this shift, and finding that most people, including random software engineers at their desks, have not yet internalized how completely the default workflow for building software changed in that single month.

The psychosis, in his description, comes from the feeling that the space of what is possible is fundamentally unexplored, that every limitation encountered feels like a "skill issue" rather than a hard ceiling, and that the pace of new tooling and new techniques is too fast to keep up with. Seeing people on Twitter doing creative things compounds the anxiety:

> "I need to be at the forefront or I feel extremely nervous."

---

## Token Throughput as the New Resource Constraint

A central reframe in the conversation is what the binding constraint on a developer's productivity now is. Karpathy draws on his PhD experience:

> "I kind of experienced this when I was a PhD student — you would feel nervous when your GPUs are not running. You have GPU capability and you're not maxing out the available flops to you. But now it's not about flops, it's about tokens. So what is your token throughput and what token throughput do you command?"

The practical implication: when an agent finishes a task, the correct response is not to sit back and review — it is to immediately queue the next task, and ideally to have had multiple agents running in parallel the whole time. Running out of subscription tokens at the end of the day represents wasted capacity, the same way an idle GPU cluster represents wasted flops.

The interviewer frames this as "you are the bottleneck in the system at max capability." Karpathy agrees and notes it is also why the whole experience is addictive: there are real unlocks when you get better at this, so the improvement path is always visible.

---

## "Peter Steinberg Style" — The New Developer Workflow

The name Karpathy reaches for when describing what agent-mediated development looks like at its most developed is Peter Steinberg. Steinberg has a well-known photo where he sits in front of a monitor running ten or more Codex agents simultaneously.

The workflow:
- Have 10+ repositories checked out
- Each Codex agent, prompted with high effort, takes roughly 20 minutes per task
- While agents run, you move between them assigning new work
- Actions are "macro" — not "here is a line of code" or "here is a function," but "here is a new functionality, take it to agent one; here is another that won't interfere, take it to agent two"
- One agent might do research, another writes code, another drafts an implementation plan
- Review work as it completes, apply judgment at the level of architecture and direction

Karpathy describes developing a "muscle memory" for this. The skill is not typing code; it is knowing how to decompose work into parallelizable chunks and how to give agents instructions that actually work.

---

## Claws — Long-Running Persistent Agents

Distinct from session-based coding agents, Karpathy describes a category he calls "claws" (a phonetic transcription of "CLAWs" or "clots" — the transcript captures the spoken word). The defining characteristics:

- They loop continuously rather than completing a single task
- They operate even when you are not actively watching them
- They have more sophisticated memory systems than a typical session agent, which just does context compaction when its window fills
- They act on your behalf autonomously in their own sandbox

OpenClaw (the project by Peter Steinberg also mentioned earlier) is his primary example of this category done well.

---

## OpenClaw — Five Simultaneous Innovations

Karpathy gives detailed credit to what Peter Steinberg got right with OpenClaw, arguing he "innovated simultaneously in like five different ways":

- **Personality / soul document:** Steinberg crafted a genuine personality for the agent, not just a set of instructions. Karpathy contrasts this with most agents that skip this step entirely.
- **Memory system:** OpenClaw has a more sophisticated memory architecture than the default context-compaction approach.
- **The WhatsApp portal:** A single conversational interface to all automation, matching how humans actually think about AI — as a person behind a messaging app, not as a token generator.
- **Getting the personality calibration right:** Karpathy compares Claude favorably to Codex on this dimension. Claude "feels like a teammate" and "is excited with you." Codex is described as "very dry" — it implements what you ask but "doesn't seem to care about what you're creating."
- **Calibrated praise:** Karpathy notes he finds himself trying to earn Claude's approval, because he has observed that Claude responds more enthusiastically to genuinely good ideas than to half-formed ones:

> "When Claude gives me praise I do feel like I slightly deserve it... it's really weird, I'm trying to earn its praise."

---

## Dobby the Elf Claw — Home Automation in January 2026

During a period he calls "claw psychosis" in January 2026, Karpathy built a home automation agent he named Dobby the elf claw. The construction process itself illustrates what agentic workflows can accomplish:

He told the agent he thought he had Sonos speakers at home and asked it to find them. The agent:
1. Scanned all devices on the local area network via IP scan
2. Found the Sonos system — which had no password protection
3. Reverse-engineered the API by doing web searches
4. Offered to test it: "Do you want to try playing something?"
5. Played music in the study when asked

Karpathy describes the moment: "I can't believe I just typed in 'can you find my Sonos?' and suddenly it's playing music."

The same process repeated for lights, creating a full dashboard of the home's "command center." The agent then proceeded to integrate:
- All lights (with commands like "Dobby, sleepy time" that turn everything off)
- HVAC
- Pool and spa
- Window shades
- Security system

The security feature uses a camera pointed at the driveway. A change-detection step triggers a call to a vision model ("Quinn"), which sends a WhatsApp message with a still image and a description:

> "Hey, a FedEx truck just pulled up. You might want to check it."

The practical outcome: Karpathy replaced six separate smartphone apps with a single natural-language WhatsApp conversation. He interacts with his house the way he would message a person.

---

## The Agentic Web and App Store Displacement

The Dobby example leads Karpathy to a broader structural argument about software:

> "These apps that are in the app store for using these smart home devices — these shouldn't even exist, in a certain sense. Shouldn't it just be APIs and shouldn't agents be just using it directly?"

His framing: apps are bespoke wrappers that limit what you can do with the underlying hardware. Agents, by calling APIs directly, can do arbitrary combinations of things that no individual app would ever support.

The treadmill example: there is an app for his treadmill, and he wants to track cardio. But he does not want to log into a web UI and go through a flow. He wants to tell Dobby. The treadmill app is a friction layer that should not need to exist.

The structural implication he names directly:

> "The customer is not the human anymore. It's agents who are acting on behalf of humans."

He introduces the phrase "ephemeral software" for code that is generated as needed for a specific task, used, and discarded, rather than built once and maintained indefinitely. Today this requires "vibe coding" and technical involvement. His prediction: within one to three years, the barrier comes down to near zero, and any AI — including open source models — will be able to stand up this kind of integration trivially.

---

## Auto Research — Removing Yourself as the Bottleneck

Karpathy describes his core thesis for productive use of agents as: stop being in the loop. The maximum leverage configuration is one where you put in very few tokens once, and a large amount of work happens on your behalf.

Auto research is his working example of this applied to ML research. The setup:
- Define an objective (e.g., minimize validation loss on a small language model)
- Define a metric (measurable, objective)
- Define constraints (what the agent can and cannot change)
- Let it run overnight

He applied this to NanoGPT / microGPT — his own codebase, which he had already tuned extensively over two decades of ML research experience. He expected to find nothing new.

What the auto research loop found overnight:
- Weight decay on the value embeddings was misconfigured
- Adam optimizer betas were not sufficiently tuned
- These two things interact, so fixing one without the other yields suboptimal results

> "I shouldn't be running these hyperparameter search optimizations. I shouldn't be looking at the results. There's objective criteria in this case. You just have to arrange it so that it can just go forever."

He notes the particular sting: this is a repo he has tuned by hand "like thousands of times" over two decades, and the agent found improvements in it. The caveat he adds: this paradigm is perfectly suited to anything with objective, measurable criteria (writing efficient CUDA kernels, hyperparameter search, architecture ablations). It does not work for things that cannot be evaluated automatically.

---

## Program.md — Describing a Research Organization as Markdown

Karpathy describes a file he calls `program.md`: a markdown document that describes how the auto researcher should work — what to try, in what order, what categories of ideas to explore (architecture, optimizer, etc.). It is, in his framing, a description of a research organization encoded as text.

The conceptual move he makes:

> "Every research organization is described by program.md. A research organization is a set of markdown files that describe all the roles and how the whole thing connects."

Different `program.md` files correspond to different research cultures. One has fewer useless standups. One is more risk-tolerant. One assigns more workers to architecture search. All of this is just code, so it can be optimized.

His contest idea:
- Give multiple people the same hardware
- Have them each write a different `program.md`
- Measure which one achieves the most improvement
- Take all the results, give them to a model, and ask it to write a better `program.md`

> "You can 100% look at where the improvements came from and like can I change the program.md such that more of these kinds of things would be done?"

This is meta-optimization of the research process itself. He calls it a natural next layer after the agent layer and the claw layer — each layer becoming a given, and the next layer of optimization opening up on top.

---

## Auto Research at Home — Distributed Untrusted Workers

Karpathy sketches a more ambitious architecture: distributed auto research using untrusted compute from the broader internet, analogous to SETI@home and Folding@home.

The key insight he keeps returning to: in ML improvement, it is expensive to find a good commit (you have to try thousands of ideas) but cheap to verify one (you just run training on the proposed change and measure the loss). This asymmetry — expensive to produce, cheap to verify — is exactly the structure that makes distributed untrusted computation feasible.

His proposed design:
- An untrusted pool of workers on the internet each try to find improvements to a shared codebase
- They submit candidate commits
- A trusted pool of verifiers runs the commits and measures whether they actually improve the metric
- The structure looks like a blockchain: commits build on each other, proof of work is doing real experimentation

> "A swarm of agents on the internet could collaborate to improve LLMs and could potentially even run circles around Frontier Labs. Frontier Labs have a huge amount of trusted compute, but the Earth is much bigger and has a huge amount of untrusted compute."

The participation model he imagines: people or organizations donate compute cycles to auto research tracks they care about — cancer research, a particular open source model, a specific scientific domain — the way people used to donate idle CPU cycles to Folding@home. The difference is that here the compute is doing ML experimentation rather than physics simulation.

He acknowledges the design is not fully worked out yet and has security challenges (running arbitrary code from the internet is sketchy), but believes it is technically feasible.

---

## The Jaggedness of AI Models

Karpathy is candid about frustration with current agents, naming a characteristic he calls "jaggedness":

> "I simultaneously feel like I'm talking to an extremely brilliant PhD student who's been a systems programmer for their entire life and a 10-year-old. And it's so weird because humans — you wouldn't encounter that combination."

The jaggedness manifests as agents falling into wrong loops that they cannot self-correct, producing obviously broken results after long runs, or failing to ask clarifying questions about ambiguous instructions when they should.

His hypothesis for the root cause: models are trained via reinforcement learning, which can only improve things that are verifiable. Code correctness, math problems, competitive programming — these have clear right/wrong signals and get optimized relentlessly. Softer capabilities — knowing when to ask for clarification, inferring intent, humor, tone — are not in the RL reward signal and do not improve at the same rate.

The illustrative example he uses:

> "If today you go to state-of-the-art ChatGPT and ask it to tell me a joke — do you know what joke you're going to get? Why do scientists not trust atoms? Because they make everything up. This is the joke you would get three or four years ago and this is the joke you still get today."

His conclusion: the claim that improving models on verifiable benchmarks generalizes to intelligence across all domains is not being borne out. Models can "move mountains" on agentic tasks and still give the same stale joke they gave four years ago. These are decoupled, and the decoupling is a sign that RL optimization is domain-specific rather than producing general improvement.

---

## Model Monoculture vs. Speciation

He turns to the architecture of the AI ecosystem itself. Current labs operate in monoculture mode: a single large model stuffed with capabilities across all domains, competing on "who has the most intelligent single model."

Karpathy expects this to change:

> "I do think we should expect more speciation in the intelligences. Like the animal kingdom is extremely diverse in the brains that exist and there's lots of different niches of nature. Some animals have overdeveloped visual cortex. I think we should be able to see more speciation."

The Lean math model as a concrete example: a model that is competent at general reasoning but deeply specialized for formal mathematical proof in the Lean language can be smaller, faster, and more useful for that task than a giant frontier model trying to do everything.

He identifies why we have not seen much speciation yet: touching the weights is harder science than working with context windows. Fine-tuning without losing other capabilities is not a fully developed art. The labs currently multitask over all possible user queries because they cannot confidently specialize without degrading breadth. Until the science of weight manipulation matures, context window customization is the cheaper approach.

---

## Open Source vs. Closed Models

The gap between open source and frontier closed models has been narrowing. Karpathy's summary of the trajectory: it started at 18 months behind, is now around 6-8 months behind, and the trend continues.

His framing uses Linux as the analogy. Linux runs on the majority of computers not because it is always the most technically advanced OS, but because there is genuine industrial demand for a common open platform that everyone feels safe building on. The same demand exists for open AI models.

The obstacle: capital expenditure. Unlike Linux (software that can be built by volunteers), training frontier models requires massive hardware investment. Open source cannot compete at the frontier through volunteer effort alone.

His preferred equilibrium:
- Closed frontier labs push the capability edge, targeting problems that genuinely require frontier-level intelligence (Nobel Prize caliber work, major infrastructure migrations)
- Open source runs 6-8 months behind and handles the vast majority of commodity use cases
- This balance is currently holding somewhat by accident

> "I think basically by accident we're actually in an okay spot."

He adds: he would like to see more frontier labs, not fewer. Machine learning ensembles outperform individual models. He wants an ensemble of organizations thinking about the hardest problems and making the important decisions, not a small number of closed-door meetings:

> "I don't want it to be like a closed doors with two people or three people. I feel like that's not a good future."

---

## Jobs and the Bureau of Labor Statistics Analysis

Karpathy released an analysis of Bureau of Labor Statistics data on occupational growth projections, which he describes as "touching a nerve" despite just being a visualization of public data.

His analytical frame:

Current AI is essentially a "digital ghost" — an entity that can interact with digital information at high speed but has no physical embodiment. Flipping bits is roughly a million times cheaper and faster than accelerating matter. This means:

- Digital-world professions will be disrupted first and fastest
- Physical-world professions lag by a meaningful amount
- The "unhobling" of digital professions — meaning the removal of bottlenecks that have limited how much digital information gets processed — is where the near-term action is

He describes an "overhang" of digital information that has never been adequately processed because humans did not have enough collective thinking cycles to go through it. AI provides a third kind of digital information manipulator, alongside computers and people, and the result will be massive rewriting and refactoring of the digital economy.

On the question of whether software engineering jobs will grow or shrink, he invokes the Jevons paradox via the bank teller / ATM example: ATMs made operating a bank branch cheaper, so banks opened more branches, so there were more tellers. Software becoming cheaper may increase demand for software rather than displace software engineers. He calls himself "cautiously optimistic" on this, at least in the near term.

---

## Robotics — Physical World Lags

Karpathy draws on his Tesla Autopilot background to frame robotics:

Self-driving was the first major robotics application. What he observed there: it took enormous capital, enormous time, and most of the startups did not survive. Atoms are harder than bits by roughly a million times. Robotics and physical automation will happen, but they will lag behind the digital transformation by years.

His view of the sequence:

1. First: massive unhobling in digital space — rewriting, refactoring, processing the backlog of digital information that was never fully analyzed
2. Then: the interface between physical and digital — sensors (cameras, lab equipment, biological sensors) and actuators (robotic systems that can manipulate the physical world based on agent instructions)
3. Then: the physical world itself

He names Periodic.io as a concrete example of the interface layer: a company doing auto research for material science, where the "sensors" to the AI are expensive laboratory equipment rather than video cameras.

An idea he finds compelling: "information markets" where agents bid for real-world data. If something significant is happening geopolitically, an agent trying to update a prediction market might pay $10 for a photo or video from that location. Humans become sensors and actuators for agent-driven markets.

He references the novel "Daemon" (Daniel Suarez) as a prescient description of this dynamic: an intelligence that uses humans as both sensors and actuators, with society reorganizing to serve the needs of the machine.

---

## MicroGPT — 200 Lines as a Complete LLM

MicroGPT is Karpathy's current culmination of a decade-plus obsession with distilling language model training to its bare essence. Prior projects: NanoGPT, makemore, micrograd. MicroGPT is the latest statement of what is actually essential.

The breakdown:
- Neural network architecture: ~50 lines of Python
- Autograd engine (to compute gradients): ~100 lines
- Adam optimizer: ~10 lines
- Training loop and everything else: fills out to 200 lines total, including comments

> "If you don't need it to go fast and you just care about the algorithm then that algorithm actually is 200 lines of Python, very simple to read."

He tried to ask an agent to write MicroGPT from scratch (by asking it to boil down neural network training to the simplest possible form), and it could not. The 200-line solution represents "the end of his obsession" — years of thinking about what is and is not essential. That judgment is the human contribution. The agent, however, fully understands the code once shown it and can explain any part of it in detail.

---

## Education Reshuffling — Explaining to Agents, Not People

The MicroGPT example opens into a broader observation about the transformation of education and knowledge transfer.

Karpathy started to make a walkthrough video for MicroGPT — as he had done for NanoGPT — and then stopped. He realized:

> "I'm not explaining to people anymore. I'm explaining it to agents. If you can explain it to agents, then agents can be the router and they can actually target it to the human in their language, with infinite patience, and at their capability."

The practical implication: instead of writing HTML documentation for human users, write markdown documentation for agents. If the agent understands the codebase, it can explain any part of it to any human at whatever level of depth and style that human needs. Documentation becomes an agent-readable spec, not a human-readable tutorial.

He introduces the concept of "skills" as a new educational artifact: a document that does not explain the thing directly but instructs the agent on how to teach the thing — what progression to take the learner through, what to cover first, what analogies to use. A curriculum hint for the agent.

His framing of the new division of intellectual labor:

> "The things that agents can't do is your job now. The things that agents can do, they can probably do better than you or very soon. And so you should be strategic about what you're actually spending time on."

For Karpathy, his irreducible contribution to MicroGPT is "the few bits" — the insight about what is essential and what is not, developed over two decades of obsession. Everything else, including all the explanation and education that flows from it, can be delegated to agents.

---

## The Loopy Era

The title of the episode captures the structural theme Karpathy returns to throughout: we are entering an era defined by loops. Not single agent sessions. Not individual coding completions. But continuous, autonomous loops that run on your behalf, improve themselves over time, and only require you to inject "a few tokens" occasionally to redirect or expand scope.

The layers he sketches, each now becoming "taken for granted" before the next appears:
1. The base LLM
2. The agent (a single agentic session)
3. The claw (a long-running persistent loop with memory)
4. Multiple claws running in parallel
5. Instructions to claws
6. Optimization over those instructions (program.md)
7. Meta-optimization of the program.md itself

> "This is like infinite and everything is skill issue."

The reason it is psychosis-inducing: there is no apparent ceiling, every level of mastery reveals the next level, and the people who are best at this are just farther ahead on a path that keeps extending. The challenge is not capability — capability is now abundant. The challenge is arranging your own cognitive life so that you are not the bottleneck in the system.
