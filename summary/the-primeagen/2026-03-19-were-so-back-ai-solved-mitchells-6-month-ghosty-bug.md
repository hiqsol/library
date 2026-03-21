# Summary: "We're So Back" — AI Solved Mitchell's 6-Month Ghosty Bug

ThePrimeagen · The PrimeTime · 2026-03-19

## The Bug

Mitchell Hashimoto (creator of Ghosty terminal) had a screen-flicker bug on split — visible
for 6+ months, unfixed by him, his team, and multiple AI models. OpenAI Codex o3 extra high
solved it in minutes for $4.14.

## What Made the Difference

Only "extra high" reasoning went to read GTK4 C source code directly — other models and lower
reasoning levels did not. The root cause: GTK leaf nodes inside surfaces were being fully
destroyed and recreated on each split instead of reused. The fix: preserve unchanged nodes.
Synthesis required: Ghosty/Zig code + GTK4/C source + GitHub issue history.

## Human Work Still Required

Mitchell did not just ship the AI's output:
- Full code review with pointed questions
- Pushed back on failure mode handling → further changes
- Manual cleanups

Review/cleanup took meaningful time — just far less than the research phase.

## The Bug It Also Introduced

Codex fixed the hard bug but introduced 2 simpler new ones. Both quickly caught. Net: strongly
positive but not infallible.

## ThePrimeagen's Mental Model

Two modes: write everything by hand, or "Sam Altman take the wheel." The underused middle path:
use AI for 80% (forensic research, source tree traversal), do the 20% yourself (review, design,
cleanup). This is the actually productive mode Mitchell demonstrated.

## Hyrum's Law

Closing frame: *"With sufficient users of an API, all observable behaviors will be depended on
by somebody."* Deep-source bugs exist because undocumented behaviors become load-bearing. AI
can find them by reading enough source — humans historically couldn't afford the time.

## The Point

Not "developers are over." The shift is specific: AI strips away the least pleasurable part of
programming — combing through vast source trees looking for one hidden root cause. Human
judgment for correctness and design remains essential.
