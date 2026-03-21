---
title: Code Agents, AutoResearch, and the Loopy Era of AI
author: Andrej Karpathy
channel: No Priors
url: https://youtu.be/kwSVtQ7dziU
date: 2026-03-20 00:00
tags: ai
---

# Andrej Karpathy on Code Agents, AutoResearch, and the Loopy Era of AI

## The Inflection Point

- December 2025 flipped Karpathy's workflow from 80% writing code himself to 80%+ delegating to agents — and the ratio has continued widening since
- He describes a state of "AI psychosis": constant awareness that the space of what is possible is unexplored, every failure feels like a skill issue not a hard ceiling, and the pace of new tooling is too fast to track
- Token throughput has replaced GPU utilization as the resource constraint to maximize; going idle while you have subscription capacity is the new equivalent of leaving GPUs unused

## The New Developer Workflow

- "Peter Steinberg style": running 10+ Codex agents in parallel, each taking ~20 minutes on high effort, while you move between them assigning work and reviewing outputs in macro actions ("here is a new functionality" rather than "here is a line of code")
- "Claws" are a distinct category above session agents: long-running persistent loops with sophisticated memory that operate on your behalf even when you are not watching, exemplified by OpenClaw
- OpenClaw succeeded because Peter Steinberg innovated simultaneously on personality (soul doc), memory architecture, and the single WhatsApp portal; Claude feels like a teammate while Codex is "very dry and doesn't seem to care what you're building"

## Dobby the Elf Claw

- In January 2026, Karpathy built a home automation agent named Dobby that, in a few prompts, scanned the local network, found Sonos speakers with no password protection, reverse-engineered the API, and played music
- The same agent controls lights, HVAC, pool, spa, shades, and security; a camera + vision model (Quinn) sends WhatsApp alerts ("FedEx truck just pulled up") with images
- Replaced six separate smartphone apps with a single natural-language WhatsApp conversation; apps shouldn't exist — "just APIs and agents as the intelligence glue"

## Auto Research

- The core principle: remove yourself as the bottleneck; define an objective, a metric, and boundaries, then let it run overnight without human involvement
- Applied to his own NanoGPT/microGPT repo (already tuned over two decades), the auto research loop found that weight decay on value embeddings and Adam betas were jointly suboptimal — things he had missed because they interact
- `program.md` is a markdown file describing how a research organization should work; different programs yield different results; his contest idea: same hardware, different program.md files, measure which gets most improvement, then feed that data back to generate an even better program.md (meta-optimization)
- Distributed extension: untrusted pool of internet workers submit candidate commits that are cheap to verify (just run training) but expensive to produce; blockchain-like structure; could let a swarm of agents outcompete Frontier Labs by harnessing Earth's untrusted compute — analogous to SETI@home / Folding@home

## Model Limitations and Ecosystem Structure

- Current models are "jagged": simultaneously like a brilliant systems programmer PhD and a 10-year-old; they still fall into nonsensical loops; RL can only improve verifiable domains, leaving softer capabilities stuck (ChatGPT still tells the same "why don't scientists trust atoms" joke it told four years ago)
- Labs currently operate in monoculture mode; Karpathy expects more speciation (like the animal kingdom), with smaller specialized models for specific domains like formal math in Lean; touching weights is harder science than context windows, which is why it hasn't happened yet
- Open source is ~6-8 months behind frontier, down from 18 months; Karpathy calls this a good equilibrium by accident — frontier for Nobel-prize-level work, open source eating basic use cases; wants more labs, not fewer

## Jobs, Robotics, and the Physical/Digital Divide

- Digital professions will be disrupted first: bits are copied at speed of light, atoms are ~1 million times harder; there is a huge overhang of digital information that has never been adequately processed ("unhobling")
- Robotics and physical automation will follow the digital transformation by years; the interesting near-term layer is the interface between physical and digital — sensors (lab equipment, biology sensors, cameras) and actuators feeding agent-driven systems; information markets where agents bid for real-world data
- Bureau of Labor Statistics data: Karpathy is cautiously optimistic on software engineering jobs via Jevons paradox — cheaper software unlocks more demand, as ATMs led to more bank branches and more tellers

## MicroGPT and Education

- MicroGPT is 200 lines of Python total: ~50 lines for the neural net architecture, ~100 lines for the autograd engine, ~10 lines for Adam, rest is training loop — Karpathy's "end of obsession" distilling LLM training to bare essence
- He stopped making explainer videos because "I'm not explaining to people anymore, I'm explaining to agents"; agents are the router to humans, providing explanations tailored to each person's level and style
- New educational artifacts: markdown docs for agents instead of HTML docs for humans; "skills" as curriculum hints that tell an agent how to teach a codebase rather than explaining it directly
- The irreducible human contribution: "the few bits" of judgment about what is essential — the agent cannot generate MicroGPT from scratch but fully understands it once shown; "the things agents can't do is your job now"
