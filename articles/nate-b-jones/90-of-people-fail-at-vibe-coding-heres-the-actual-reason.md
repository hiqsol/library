# 90% of People Fail at Vibe Coding: You're Skipping the Hard Part

- **Source:** [YouTube — Nate B Jones / AI News & Strategy Daily](https://www.youtube.com/watch?v=sLz4mAyykeE)
- **Author:** Nate B Jones
- **Date:** 2026-02-07 16:01

---

## From Work to Play

Something clicked in the last couple of weeks. Vibe coding — using AI to
build software with natural language — has been possible since early 2025.
For most of the year, it was still work: fighting tools, babysitting the
AI, debugging weird failures, learning about databases and backends. The
friction was high enough that you had to be serious about what you were
building.

What shifted is not just that the tools got better. Models hold context
longer. Agentic patterns have matured. Builder platforms are more reliable.
The friction has dropped enough that building software stopped feeling
like work and started feeling like play. And play produces very different
things.

### The Fable Example

A service called Fable started making the rounds. You upload a photo of
your pet and it generates a Renaissance portrait — your dog as a baroque
duke, your cat as a Flemish noblewoman. It ships as a physical print.
This is not an "identify a market need and execute" story. It is a
"wouldn't it be funny if" story. Someone was playing. They built the joke.
The internet turned out to have demand for it.

Software has now become cheap enough to make for fun, and people are
making different things — weirder, more creative, things that come from
play rather than strategy.

## Software's Instagram Moment

For most of software's history, the gap between "I wish this existed" and
"I made it exist" was too wide to cross casually. Most ideas died in that
gap — not because they were bad, but because the activation energy was
too high.

The gate is open now. This is software's Instagram moment. Taking good
photos used to require serious expertise — exposure, developing, dark
rooms. Then cameras got easier, the smartphone made everyone a
photographer, and Instagram came along. Professional photography still
exists, but alongside a vast amateur ecosystem.

The same is happening with software. Professionals are not going anywhere.
Complex systems still require deep expertise. But alongside professional
development, there is now space for casual creation: building for
yourself, for fun, for friends, because you had an idea and now you can
make it real.

### Examples of Hobby Software

- A designer builds a personal dashboard showing moon phases, Spotify
  stats, and days until vacation
- A retiree automates greenhouse irrigation
- Someone makes a browser extension that logs every article mentioning
  cat grooming
- A friend gets a custom Telegram bot for concert ticket alerts
- A custom CRM for a small business

None of these are necessarily businesses. They are projects built for the
satisfaction of building.

## Parkour Vision for Software

Most people, told they can now build any app they want, say "cool" and
never think of anything to build. Not because they are uncreative, but
because most people's problems are not software-shaped and most do not
notice when they are.

There is a concept from parkour called "parkour vision" — the trained
ability to see walls as runnable surfaces, gaps as jumpable spaces,
railings as pathways. Software vision is like that. Programmers are
trained to see repetitive tasks as automation opportunities. Everyone
else just keeps doing them manually.

Signs you might have software vision:

- You have built a complicated spreadsheet to solve a problem
- You have duct-taped together automations with Zapier, N8N, or macros
- You have bent a tool to do something it was not designed for
- You have written bash scripts to fix broken drivers

You do not need to know how to code. You need to notice when a problem
could be solved by software and be curious enough to try.

## Two Failure Modes

### 1. Moving So Fast You Never Stop to Think

When building is instant, the bottleneck shifts to knowing what you
actually want. It is easy to prompt before figuring that out, generating
piles of features that do not fit together. The build-test-iterate loop
is so fast it can feel intoxicating for its own sake.

**The discipline:** Pause. Describe what you want plainly before
prompting. Know why you are building it. Know what success looks like.
The tools will happily turn vague intentions into their idea of working
code — but that may not be your idea.

### 2. Confusing "Works on My Laptop" with "Ready for Users"

AI compresses the cost of creating software toward zero but does not
compress the cost of owning software in production. Someone still has to
answer when the vibe-coded project breaks at 2 AM. Who carries the
liability? Who integrates it with everything else?

For personal projects, it does not matter. Your greenhouse automation can
crash and the worst thing is you go water the tomatoes. For something
users depend on, the gap between prototype and production remains real.

Security researchers have found roughly 10% of apps built on popular vibe
coding platforms have vulnerabilities (likely a low estimate) — databases
exposed to the public internet, API keys visible to anyone who looked.
AI handles the happy path and often misses edge cases.

Platforms like Lovable are betting on the Shopify playbook: start with
"you can vibe code anything" and help you grow up — adding
authentication, security, and scaling infrastructure.

## The Two Paths

### Builder Platforms (Lovable, Bolt, Replit)

You describe what you want in chat. The platform generates the application
— front end, backend, database, deployment, even domain. You never see a
terminal. Makes sense if you have zero technical background and need
something fast. Trade-off: control. These platforms optimize for speed to
first demo, not long-term maintainability.

### Command-Line Tools (Claude Code, Cursor, Windsurf)

You work in a code editor or terminal. The AI writes the code. You see
it, run it locally, commit to your own repo. Gives flexibility to change
tools without starting over. Trade-off: setup friction and a learning
ramp. But the code is truly yours.

### Key Principle for Both

AI coding tools degrade over long conversations. The model contradicts
itself and forgets what it built. Solution: break work into small tasks,
each in a fresh context window. Clear tasking for a particular job,
defined precisely.

## The Skill That Matters: Specification

The valuable skill is not coding. It is specification. Experienced
developers know how to break problems into pieces, know what questions to
ask (what happens when a user is not logged in? what if the database is
slow?). Beginners tend to prompt vaguely and accept whatever the AI
generates.

You do not need to be a professional developer. You need enough intuition
to specify clearly and evaluate with critical thinking. That gap is much
smaller than learning to code from scratch.

## Getting Started

1. **Start with something you actually want.** Motivation matters.
2. **Describe before you build.** Write down what you want and why.
3. **Accept rough early attempts.** It is part of building intuition.
4. **Stay in the shallow end** until comfortable.
5. **Know when to ask for help.** Experienced engineers who also vibe
   code hang out on X, Discord, and community forums.

## Three Converging Truths

1. Building software is inherently satisfying — the feeling of making
   something that works. Always true, but previously gated behind years
   of specialized learning.
2. The internet has nearly infinite demand for interesting things. Always
   true, but discovering what the internet wanted was historically
   expensive.
3. The cost of building hobby-scale software is approaching zero. This is
   new. Making it fun is even newer — just a few weeks old.

> When the cost of experimentation collapses, you can be playful. Try the
> idea. If it does not work, you did not lose much. If it does, maybe the
> internet loves your dog pictures.
