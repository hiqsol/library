---
title: We're So Back - AI Solved Mitchell's 6-Month Ghosty Bug
author: ThePrimeagen
channel: The PrimeTime
url: https://youtu.be/5DP0az1q_8M
date: 2026-03-19 00:00
tags: ai, development
---

# "We're So Back": AI Solved Mitchell's 6-Month Ghosty Bug

[summary](../../summary/the-primeagen/2026-03-19-were-so-back-ai-solved-mitchells-6-month-ghosty-bug.md)

## The Hype Cycle

Software engineering discourse has been trapped in a loop: every new model release triggers
either "it's so over" (AI will replace all developers) or "we're so back" (AI is amazing again).
The people who've never written a line of code flex about their to-do apps. The developers laugh
from the sidelines — until AI actually does something impressive.

This video is about one of those genuinely impressive moments.

---

## Mitchell Hashimoto's Bug

Mitchell Hashimoto — best known recently as the creator of the **Ghosty terminal** — posted
about a bug that had resisted fixing for over 6 months. When splitting the screen in Ghosty,
there was a brief visible flash — a flicker from the underlying content showing through before
the new pane rendered.

He tried to solve it. His team tried. Other AI models tried. Nothing worked.

Then: **OpenAI Codex "o3 extra high"** solved it in one shot, costing $4.14, in minutes.

Mitchell's note: *"The best thing Codeex did was eventually start reading the GTK4 source code.
That's where I ended up seeing my GitHub issue, and I knew the answer was somewhere in there,
but I didn't have the time or the motivation to do it myself. The other models never went there.
The lower reasoning efforts with o3 didn't go there either. Only extra high went there."*

---

## What the AI Actually Did

The bug was a GTK rendering issue. The AI's investigation path:

1. Identified it as a GTK split update problem
2. Found the exact commits touching the relevant area
3. Combed through every patch, tracking code changes
4. Looked at per-commit history tied to the specific issue
5. Narrowed down to `split_tree_split` operation
6. Made an unexpected pivot: started reading **GTK4 C source code directly**
7. Also looked at Zig code (Ghosty is written in Zig)

The root cause: leaf nodes inside GTK surfaces were being **fully destroyed and recreated** on
each split — instead of being reused when they hadn't changed. The visible flash was those nodes
being torn down and rebuilt. The fix: reuse unchanged leaf nodes, destroying only what actually
needs to change.

The AI produced ~50-60 lines of changes that solved a problem requiring synthesis across
multiple codebases (Ghosty/Zig, GTK4/C, GitHub issue history).

---

## The Human Work That Still Happened

ThePrimeagen flags what the "AI Andy" vibe-coder misses: Mitchell didn't just take the code
and ship it. He:

- Did a thorough code review
- Asked pointed questions about specific design decisions
- Pushed back on failure mode handling
- Required further changes based on that review
- Did manual cleanups

The review and cleanup phase took meaningful time — just far less than the *research* phase
would have. The AI handled the forensic work (reading source trees, tracing commits, connecting
disparate codebases). The human handled judgment, correctness, and code quality.

---

## The Bug It Introduced

Counter to pure "it's so over" narratives: after fixing the hard 6-month bug, Codex introduced
**2 new simpler bugs**. Those were quickly caught and fixed. PrimeTime's framing: it fixed a
genuinely hard problem and created two easy ones — net strongly positive, but not magic.

---

## ThePrimeagen's Mental Model

He describes two modes he operates in:

- **Write everything by hand** — full control, slow
- **"Sam Altman take the wheel"** — AI writes it all, he just adds tests and hopes

What he doesn't do enough of — and what Mitchell's story illustrates — is the **middle path**:
*"Here's something that will take a lot of research. Go get me 80% of the way there. I'll do
the other 20%."*

This is the actually productive mode: use AI for tedious forensic research through large
codebases; use human judgment for review, cleanup, and design decisions.

---

## Hyrum's Law

ThePrimeagen closes with **Hyrum's Law** as the frame for why these deep-source bugs are so
hard:

> *With a sufficient number of users of an API, it does not matter what you promise in the
> contract. All observable behaviors of your system will be depended on by somebody.*

This is why the bug existed: some behavior of GTK that was never documented as a contract became
relied upon. The AI could find it because it read enough source code to see what was actually
happening vs. what was promised.

---

## The Honest Take

This video is not "it's so over for developers." It's:

- AI is genuinely transforming the most painful parts of development — deep forensic debugging
  across large codebases
- Human review, judgment, and cleanup remain essential and non-trivial
- The productive future is the 80/20 split, not full autonomy
- The hype cycle (over/back/over/back) misses that the actual shift is quieter and more specific
