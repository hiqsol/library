# Summary: Anthropic Gave Your AI Agent the One Thing OpenClaw Has — Without the Risk

**Source:** Nate B. Jones · YouTube · 2026-03-20
**Video:** https://www.youtube.com/watch?v=vqnAOV8NMZ4

---

- Anthropic shipped `/loop` — a Claude Code command that runs an agent on a schedule without
  the user being present; most people missed it.
- OpenBrain (SQL database + MCP server) gave agents memory; `/loop` gives them proactivity —
  the final missing primitive.
- A real agent requires exactly 3 primitives: **memory** (persistent read/write), **proactivity**
  (acts on a schedule without being prompted), **tools** (hands to reach external systems).
- Without memory, every session starts from zero — the agent is a new hire on day one.
- Without proactivity, the user is the metronome; every reminder costs time the agent could
  use doing work.
- Without tools, the agent can think but can't act — a brain in a jar.
- Memory transforms a loop from a parrot (recites) into a detective (accumulates evidence,
  builds a case, identifies patterns across weeks).
- Health example: agent notices 9 of 12 mornings show low energy, finds all 3 good mornings
  followed eating before 8 p.m., dismisses caffeine as the variable — memory, not prompt.
- Business example: customer success agent sees usage down 15% one week, 28% the next,
  matches trajectory to a churned account from 6 months ago, flags for executive outreach.
- Tools let the agent act: query calendar, pull Slack threads, call Remotion via MCP to
  generate a personalized briefing video before a networking event.
- Agent cycle: wake via `/loop` → read memory → call tools → take action → write results back
  → sleep. Set once, runs indefinitely.
- Andre Karpathy's AutoResearch: agent runs ~100 ML experiments overnight, logs what it tried,
  converges on better patterns — compounding across cycles, not single-shot intelligence.
- Shopify CEO Tobi Lütke used AutoResearch to produce an agent-optimized model that
  outperformed a larger hand-tuned model — because 100 informed cycles beat one careful pass.
- OpenClaw hit 200,000 GitHub stars; Jensen Huang called it the most consequential software
  launch in history; but security researchers flagged it as a nightmare (network exposure,
  data access, vulnerable extensions).
- The OpenBrain + `/loop` + MCP tools stack replicates most OpenClaw capabilities without
  OpenClaw's security layer; scheduling is native to Anthropic, memory is user-owned.
- Honest gaps: no built-in done signal (need eval or completion check in memory); session-
  scoped (laptop closes = schedule stops); skill ceiling still requires terminal comfort.
- Peter Steinberger (OpenClaw creator) advises against it for non-technical users; went to
  OpenAI to build a safer successor — that doesn't exist yet; the primitives do.
- Terminal = time travel: these capabilities will reach friendlier UIs eventually, but
  developers and terminal users get them months ahead of everyone else.
- Core message: think in Lego bricks — when a release drops, ask whether it advances memory,
  proactivity, or tools; that frame cuts through noise quickly.
