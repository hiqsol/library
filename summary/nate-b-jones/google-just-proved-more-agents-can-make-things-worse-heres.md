# Google Just Proved More Agents Can Make Things Worse — Summary

A December 2025 Google-MIT study found that adding more agents can
make systems perform worse — not diminishing returns, but actual
degradation. In tool-heavy environments (10+ tools), multi-agent
efficiency drops by a factor of 2-6 vs. single agents. Gartner
predicts 40% of agentic AI projects will be cancelled by 2027.

**Core insight:** Simplicity scales because complexity creates serial
dependencies, and serial dependencies block the conversion of
compute into capability.

**Five rules for scaling to hundreds of agents:**

1. **Two tiers, not teams.** Cursor tested flat agent teams — 20
   agents produced the output of 2-3 due to lock contention and risk
   aversion. What works: strict planner/worker/judge hierarchy.
   Workers do not know other workers exist. Yegge's Gas Town
   independently arrived at the same pattern (polecats + mayor).
   Research confirms two-level systems outperform both flat and
   deeper (3+) hierarchies.

2. **Workers stay ignorant.** Minimum viable context only. When
   Cursor gave workers project context, they experienced scope creep
   and created conflicts. Narrow scope eliminates coordination and
   enables parallelism.

3. **No shared state.** Tools are shared state — contention requires
   coordination. Tool selection accuracy degrades past 30-50 tools
   regardless of context window. Workers get 3-5 core tools; others
   via progressive disclosure. Merging handled by dedicated system
   (Gas Town's "refinery"), not workers.

4. **Plan for endings.** Context accumulation creates serial
   dependency with the agent's own past. Cursor found drift
   unavoidable — quality degraded within hours. Episodic operation:
   run, capture to external storage, terminate. Next cycle starts
   fresh. Gas Town's GUPP principle: workflow state lives outside
   any agent's context.

5. **Prompts over infrastructure.** 79% of multi-agent failures are
   spec/coordination issues, not technical bugs (infrastructure =
   only 16%). Treat prompts like API contracts. Good isolation makes
   simpler, more correct prompts.

**Where complexity belongs:** Not in agents (creates serial
dependencies at scale) but in the orchestration layer (enables
parallelism). Keep workers dumb; invest in orchestration.

**Bottom line:** Not one brilliant agent running for a week — 10,000
dumb agents well-coordinated by the system, running an hour at a
time. Teams that get this right will outproduce others by 100x.
