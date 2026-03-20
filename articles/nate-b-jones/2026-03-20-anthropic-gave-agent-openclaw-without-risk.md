# Anthropic Gave Your AI Agent the One Thing OpenClaw Has — Without the Risk

**Source:** [YouTube](https://www.youtube.com/watch?v=vqnAOV8NMZ4) · Nate B. Jones · 2026-03-20

---

## The Gap That Just Closed

A few weeks ago, Nate Jones introduced OpenBrain — a SQL database connected to your AI via
an MCP server, giving it persistent memory. Thousands of people built it. But one piece was
still missing: a heartbeat. A way for the agent to wake up, act, and go back to sleep on its
own without you poking it every time.

Anthropic just shipped that piece. It's called `/loop` — a native Claude Code command that
lets an agent run a job on a schedule without you being at the computer. Most people didn't
notice. They should have.

---

## The Three Lego Bricks of a Real Agent

A chatbot responds when you push it. An agent acts on its own. The difference comes down to
three primitives:

**1. Memory** — the ability to read and write to something persistent. Without memory, every
interaction starts from zero. The agent is perpetually a new hire on day one.

**2. Proactivity** — the ability to act without being prompted. Without it, you are the
metronome. Every minute you spend reminding the agent is a minute the agent could spend doing
work.

**3. Tools** — the ability to reach out and touch systems: pull data, call APIs, write to
databases, trigger workflows. Without tools, the agent can think but has no hands or feet.
It's a brain in a jar.

Remove any one of the three and you don't have a real agent anymore.

---

## What `/loop` Actually Does

`/loop` is the proactivity primitive. It fires a Claude Code agent on a schedule, without
manual intervention. Combined with OpenBrain (or any SQL memory store behind an MCP server)
and a set of tools, you get most of what OpenClaw delivers — without downloading OpenClaw.

The scheduling comes natively from Anthropic. The memory lives in a database you control,
accessed through a standard protocol without the prompt injection vulnerabilities in
OpenClaw's orchestration layer. The tools are whatever MCP servers you've connected.

---

## Why Memory Transforms a Loop

Consider a simple case: a morning energy check-in. Without memory, the agent asks how you
slept and gives generic advice. With memory, it notices you've reported low energy 9 of the
last 12 mornings, looks for the common factor in the 3 good days, and finds that all three
followed evenings where you ate before 8 p.m. The caffeine experiment you ran two weeks ago?
The agent dismisses it — the pattern doesn't support it. The real variable is meal timing.

That's the difference between a parrot that recites phrases and a detective that builds a
case from accumulated evidence.

The same principle scales directly to business. A customer success agent running weekly
health checks — without memory — flags usage down 15%. With memory, it sees that's down from
15% the prior week to 28% total, matches the trajectory against a similar account that
churned 6 months ago, and flags it for executive outreach with a deadline.

---

## Tools Make the Agent Act

Memory makes the agent smart. Tools make it act. Consider a networking example: every Friday
afternoon, `/loop` fires. The agent queries OpenBrain for every person you've interacted with
in the past two weeks, pulls meeting notes, emails, and Slack threads, passes that context to
Remotion via MCP, and generates a personalized briefing video with faces, talking points, and
follow-ups you still owe — delivered before you walk in the door.

Or simpler: the agent queries your calendar, cross-references it with memory, and sends you a
Slack message: "You're seeing Sarah tonight. Last time she mentioned evaluating a new data
platform. You said you'd send her the write-up. Here's the link."

The agent cycle is always the same:
1. Wake up via `/loop`
2. Read memory
3. Call tools
4. Take action
5. Write results back to memory
6. Sleep

Set the rhythm once. Don't touch it again.

---

## The Compounding Value of Loops

The real power isn't in any single cycle — it's accumulation across cycles.

Andre Karpathy open-sourced AutoResearch: give an AI agent a training setup, a single GPU,
and a success metric, then let it run experiments overnight. The agent modifies code, trains
for 5 minutes, checks if the metric improved, keeps or discards the result, and loops — about
100 experiments overnight with zero human intervention. Shopify CEO Tobi Lütke used this repo
to build an agent-optimized smaller model that outperformed a larger hand-tuned model. Not
because the agent was smarter in any single cycle — because it ran 100 cycles and remembered
them all.

The same principle applies without ML training. Track a competitor. Monitor regulatory
changes. Follow a market. Without memory, each morning cycle gives you a snapshot. With
memory, each cycle builds on the last. The search becomes intelligent.

Before `/loop`, getting this behavior required scaffolding: external tools to manage the
loop, markdown files to carry context between iterations, eval conditions "bolted on with duct
tape." `/loop` solves the scheduling problem natively. A proper memory system solves the
context problem. Together, that turns a hack into architecture.

---

## What `/loop` Is Not (Honest Gaps)

- **No built-in done signal.** The loop runs until it expires or you stop it. For
  goal-directed work, you need to tell the agent to check memory for a completion state or
  wire up evals manually.
- **Session-scoped.** Close your laptop and the schedule stops. Anthropic offers desktop-level
  scheduling, but always-on operation across restarts is not a native capability.
- **Skill ceiling is real.** `/loop` lives in Claude Code, which is still terminal-based and
  daunting for non-developers. These capabilities will eventually surface in friendlier UIs,
  but right now developers get them first.

The terminal is time travel. Being willing to open a different window puts you months ahead
of everyone waiting for the polished product.

---

## The OpenClaw Comparison

OpenClaw hit 200,000+ GitHub stars — the fastest-growing software repo in history. Jensen
Huang called it the most consequential software launch in history. People are hungry for
agents. But security researchers have called OpenClaw a nightmare: users opening their
networks to the internet, giving OpenClaw access to data it shouldn't have, installing
extensions with severe vulnerabilities.

You can get most of the same capabilities without it. Stack OpenBrain (or any SQL memory
store) + MCP tools + `/loop` and you get:
- Proactive scheduling from Anthropic natively
- Memory in a database you own and control
- Tools accessed through standard protocols without injection vulnerabilities

Peter Steinberger, who built OpenClaw, has been clear: don't use it if you aren't very
technically sophisticated. He went to OpenAI partly to eventually build something OpenClaw-
like but accessible and secure. While he builds that, you don't have to wait.

---

## The Takeaway

Small releases matter. `/loop` looks minor. It's not. It's the final Lego brick that completes
the stack:
- **Memory:** OpenBrain or any SQL store via MCP
- **Proactivity:** `/loop`
- **Tools:** Whatever MCP servers you've connected

If you've already built OpenBrain and connected tools, you're one command away from a
proactive agent. Add `/loop` and the heartbeat starts.

The community is building this. Nate is opening a shared space for OpenBrain recipes and
agent use cases so builders can learn from each other. The components are all on the table.
