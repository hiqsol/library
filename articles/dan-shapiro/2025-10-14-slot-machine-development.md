---
title: Slot Machine Development
author: Dan Shapiro
channel: Dan Shapiro's Blog
url: https://www.danshapiro.com/blog/2025/10/slot-machine-development/
date: 2025-10-14 10:13
tags: ai, development
---

# Slot Machine Development

[summary](../../summary/dan-shapiro/2025-10-14-slot-machine-development.md)

Something new is possible.

Four weeks ago, I braved the gaggle of Waymos nosing around the Presidio to check out Connected
Stack. I plopped next to my buddy James Cham, notorious partner at Bloomberg Beta. We started
swapping stories while earnest founders pitched their wares on stage. James started telling me
strange things about his portfolio companies' latest discoveries. I was skeptical.

"You've got to meet Justin. He's doing incredible things."

A few hours later at Piccino, I found Justin McCarthy, CTO of StrongDM, scooping up gnocchi at a
table made from a large subsection of a redwood tree.

He started telling me about his efforts to scale the use of AI in development. I furrowed my brow.
"If there's one thing I've learned about AI development", I said as I grabbed the burrata, "it's
this: you have to review *every* checkin. If you don't, things things go farkakte, fast".

Justin stared at me.

I faltered.

I mean... it's always been that way... maybe less, lately?

Then Justin explained something to me very obvious. *If* your AI can accurately judge its own work,
to at least a first approximation. *If* your AI can follow directions. And *if* you are willing to
pay.

**You can delegate all your work in parallel and pick the winner.**

That's it. That's the trick. Pull the wheels until the software springs forth.

Dispatch a half-dozen requests to write the code. Have each instance test itself. That might be a
unit test suite, that might be having an LLM inspect the output, that might be navigating the page
with Playwright or - more likely - it might be all of the above. Everyone turns in their homework,
and an LLM picks the winner.

What if it's a total bust? No problem: keep the message thread going. Tell the losers why they lost,
and get another round of iterations.

Slot-machine development is just N versions in parallel, a judge, and a budget.

And... it doesn't seem right.

First, it's remarkably expensive. But only if you're thinking in terms of a $20/month ChatGPT
subscription. If you're thinking of it in terms of cost per developer-hour? I've tried it, and
frankly it's hard to spend as much on tokens in a day, as you pay an engineer in an hour.

Second, it seems daunting to build tests that good. But of course, the AI helps with that part too.
I've gone from "AI writes unit tests" to "AI writes Cypress tests" to "AI has Playwright and just
faffs around for a bit". It's astonishing, but the latter requires little more than a good prompt
("You're a power user of localhost:8000 and you're bent on breaking it; try everything") and time to
go get coffee.

Finally, and I think the real reason. It just feels... wasteful. I remember being hunched over the
chatgpt terminal, waiting for each token to arrive. When something went off the rails - panic!
Abort, reprompt, nudge, pray. Spending ten times the tokens on five parallel attempts feels like
lighting money on fire.

But that's just the fear talking.

Everything old is new again. As the value of tokens climbs faster than the cost, we can justify
using more of them as we do more important work. First we learned to scale training compute. Then we
learned to scale reasoning tokens in series. Now - inference tokens in parallel.

Things just keep getting more interesting.

*Notes:*

- *Ryan Kannomakes the outstanding point that delegating to**different**models in parallel is way
  better than many instances of the same model*.

- *Arjun may have been the original source of "slot machine development". He's building a beautiful,
  simple tool to do it for you athttps://www.superconductor.dev/.*

- *Before that, Anthropiccalled their own products a slot machine, although they only dared to pull
  it once at a time.*

- *And it looks like Anthropic got it fromRoger Goldfinger, way back in the early days of... July?*
