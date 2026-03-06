# The Ticking Time Bomb in Every Codebase Over 18 Months Old

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=NoRePxSrhpw)
- **Author:** Nate B Jones
- **Date:** 2026-01-28 15:00

---

## AI Might Be Better at Software Architecture Than Humans

Not because AI is smarter, but because humans are structurally
incapable of the kind of vigilance that good scaled technical
architecture requires.

The conventional wisdom has been that AI is bad at architecture
because architecture requires holistic thinking, creative judgment,
and wisdom accumulated over years. But when engineers describe their
architectural failures — performance degrading over months, caching
layers breaking quietly, technical debt accumulating despite best
intentions — the root cause is almost never bad architectural
judgment. It is almost always **lost context**.

The information needed to prevent the problem did exist. It was just
spread across too many files, too many people, too many moments in
time. No single human mind could hold it all at once.

## Entropy, Not Incompetence

Ding, who spent roughly 7 years at Vercel doing performance
optimization work and opened about 400 pull requests focused on
performance, crystallized the problem: performance problems are not
technical problems — they are **entropy problems**.

His framing: "You cannot hold the design of the cathedral in your
head while laying a single brick."

The argument:

- Every engineer can only hold so much in their head
- Modern codebases grow exponentially (dependencies, state machines,
  async flows, caching layers)
- Engineers shift focus between features; context fades
- As teams scale, knowledge becomes distributed and diluted
- The same mistakes keep appearing across different organizations

Entropy wins not through malice or incompetence, but through the
accumulation of locally reasonable decisions that nobody saw adding
up to systemic problems.

## Four Production Examples of Entropy

### 1. Abstraction Conceals Cost

A reusable popup hook adds a global click listener per instance.
With 100 popup instances, that is 100 callbacks firing on every
click. The fix is easy (deduplicate listeners), but nothing in the
codebase prevents the pattern from spreading. The next engineer
reusing the hook has no way to know the cost until users complain.

### 2. Fragile Abstractions

An engineer extends a cached function by adding an object parameter.
Every call creates a new object reference, so the cache never hits —
completely broken, silently. Type safety does not help. Linters will
not catch it. Nobody notices until someone profiles the app months
later.

### 3. Opaque Abstractions

A coupon check gets added to a 1,000-line checkout function. The
await blocks everything below it, creating a waterfall where
operations could have run in parallel. The engineer adding the check
cannot see the global async flow because it is spread across
hundreds of lines written by people who no longer work there.

### 4. Optimization Without Proof

An engineer applies memoization to an operation that was already
instant — like installing a caching system to remember that 2+2=4.
The overhead of the optimization is now more expensive than the
original calculation. A best practice applied without checking
whether it was needed.

These are not edge cases. They are the normal failure mode of
software at scale.

## The Human Cognitive Constraint

Working memory research is well-established: humans can hold 4 to 7
chunks of information simultaneously. This is not a training problem
or something overcome with experience — it is a structural
limitation.

Good architectural reasoning requires holding multiple concerns
simultaneously: performance, security, maintainability, existing
patterns, downstream effects on other teams. Even a moderately
complex decision might involve a dozen relevant considerations.

When a human reviews code, they can zoom in on the local change or
zoom out to architecture, but they struggle to do both with equal
fidelity. This is why code review catches bugs but misses
architectural regressions.

At organizational scale, large engineering teams are distributed
cognitive systems. Communication overhead grows quadratically with
team size. Context transfer between engineers is extremely lossy.
Institutional knowledge decays as people leave.

## Where AI Has Structural Advantages

AI has a fundamentally different cognitive architecture. Modern LLMs
can hold 200,000+ tokens in context with constant cross-referencing
across the entire input. Some models support 1 million+ usable
tokens. This is not intelligence in the human sense — it is
comprehensive pattern matching across a very large context window
with the ability to apply consistent rules without fatigue or
forgetting.

### Five Specific Advantages

1. **Consistent rules at scale** — Humans will not check 10,000
   files with the same attention they give 10. AI can apply identical
   scrutiny to every file.

2. **Simultaneous global-local reasoning** — AI can reference
   architectural documentation while examining line-by-line changes,
   maintaining both levels of abstraction simultaneously. Like seeing
   the forest and the trees at once.

3. **Pattern detection across time and space** — With access to
   version history and the full codebase, AI can identify that "this
   cache pattern has been misused three times before" or "this type
   of waterfall was introduced and later fixed."

4. **Teaching at the moment of need** — When someone writes a
   waterfall, the system does not just flag it. It explains why it is
   a problem and shows how to parallelize it. Education embedded in
   workflow rather than relying on pre-existing knowledge.

5. **Tireless vigilance** — No deadline pressure, no context
   switching fatigue, no declining sharpness on the 47th PR of the
   week.

### Vercel's Approach

The Vercel team is distilling over a decade of React and Next.js
optimization knowledge into a structured repository: 40+ rules
across 8 categories, ordered by impact from critical (eliminating
waterfalls) to incremental (advanced technical patterns). The repo
is designed specifically to be queryable by AI agents.

## Where AI Still Falls Short

These limitations are structural, not temporary:

- **Novel architectural decisions** — AI systems are trained on
  existing code and documentation. They excel at identifying
  deviations from established patterns but cannot invent new ones.
  Andrej Karpathy has noted the difficulty of using AI to code truly
  novel things.

- **Business context and trade-offs** — Architecture involves
  trade-offs between velocity, maintainability, consistency, and
  flexibility. AI can identify technical debt but cannot judge
  whether accepting it is the right call.

- **Cross-system integration** — The engineer who knows that a
  service is maintained by a different team shipping on a different
  cadence, or who remembers a failed integration during Black Friday,
  has organizational context no code analysis provides.

- **Judgment about "good enough"** — Knowing when to stop
  optimizing. A technically superior solution taking 6 months is not
  necessarily better than an adequate solution that ships now.

- **The "why" behind existing decisions** — Codebases are
  archaeological artifacts containing decisions made under
  constraints that no longer exist. AI can see what code does but
  often cannot distinguish load-bearing decisions from historical
  accidents.

## The Right Question for 2026

The industry keeps asking the wrong question: "Where can AI
autonomously drive development?" or "Should AI be kept out of
architecture?" The better question: **What aspects of technical
architecture can we assign to AI because we recognize consistent
human weaknesses in those areas?**

AI is structurally superior at maintaining context at scale. Humans
are structurally superior at judgment under uncertainty. The future
of software architecture is not human versus AI — it is AI handling
entropy that humans were always going to lose to, while humans focus
on creative and contextual work that AI cannot touch.

This applies beyond engineering. Every department in 2026 — product,
marketing, customer success — needs to ask: where do we have
cognitive blind spots? Where can AI patch those? Where do humans
still play the essential role?
