# The Ticking Time Bomb in Every Codebase Over 18 Months Old
# — Summary

AI may be structurally superior to humans at certain aspects of
software architecture — not because it is smarter, but because humans
cannot maintain the vigilance that scaled architecture requires.

**Core thesis (from Ding at Vercel, ~400 performance PRs over 7
years):** Performance problems are entropy problems, not technical
ones. "You cannot hold the design of the cathedral in your head
while laying a single brick." Entropy wins through locally reasonable
decisions that accumulate into systemic failure.

**Four production examples of entropy:**
1. Popup hook adding 100 global listeners nobody notices
2. Cache silently broken by new object references — no linter catches
3. Coupon check creating a waterfall in 1,000-line checkout function
4. Memoization applied to already-instant operations (more overhead
   than the original)

**Human constraint:** Working memory holds 4-7 chunks. Code review
catches bugs but misses architectural regressions. Teams are lossy
distributed cognitive systems — knowledge decays as people leave.

**AI structural advantages:**
- Consistent rules at scale (10,000 files with equal attention)
- Simultaneous global-local reasoning (forest and trees at once)
- Pattern detection across time/space (version history awareness)
- Teaching at the moment of need (explain why + show the fix)
- Tireless vigilance (no fatigue on PR #47)

**Vercel's approach:** Distilling 10+ years of React/Next.js
optimization into 40+ structured rules across 8 categories, designed
to be queryable by AI agents.

**Where AI still falls short (structural, not temporary):**
- Novel architectural decisions (cannot invent new patterns)
- Business context and trade-offs (cannot judge "right call")
- Cross-system integration (organizational context)
- "Good enough" judgment (when to stop optimizing)
- The "why" behind existing decisions (archaeological artifacts)

**Key reframe:** Stop asking "where can AI autonomously drive
development?" Ask: "What architectural tasks can we assign to AI
because humans have consistent cognitive weaknesses there?" AI
handles entropy; humans handle judgment under uncertainty. This
complementarity question applies to every department, not just
engineering.
