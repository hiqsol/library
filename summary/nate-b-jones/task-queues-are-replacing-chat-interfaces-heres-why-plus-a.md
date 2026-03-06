# Task Queues Are Replacing Chat Interfaces — Summary

Anthropic built Claude Co-work in 10 days after observing developers
using Claude Code (a coding tool) for expense receipts, photo
categorization, and file management. Internal data: 67% increase in
merged PRs per engineer per day with Claude Code.

Co-work = Claude Code's agent architecture in a non-technical UI. Queue
multiple tasks, Claude works them in parallel. Feels like leaving
messages for a coworker, not having a conversation.

File system first vs browser first: browser agents face adversarial
web (CAPTCHAs, login flows, bot detection). File system agents operate
in cooperative territory — your files don't fight back. Anthropic's
bet: most valuable knowledge work lives in your files. Co-work also
integrates with Chrome for web tasks.

Prediction: 2026 is the year of desktop-native general agent wars.

Five anti-slop design bets: (1) Artifacts not text blobs — output is
the deliverable (Excel with VLOOKUP, not CSV to clean); (2) Architecture
borrowed from production code context where slop is fatal; (3) Steering
loop not editing loop — cognitive work at the top (articulating intent)
not downstream (cleaning output); (4) File system sandbox forces
specificity — must point at real folders, reducing hallucination;
(5) Task queue model encourages deeper thought about what you need
done vs shallow prompt-evaluate cycles. BetterUp study: ~2 hours lost
per piece of work slop received.

Jana Dogan (Google principal engineer, 5.5M views): gave Claude Code
a problem description, it generated what her team spent a year building
— in one hour. Prototype, not production, but independently derived
the correct solution.

Strategic implications: chatbot was transitional form — task queues
replace chat interfaces, positioning AI as worker not respondent.
Verification becomes scarce skill. Junior roles face continued
pressure. File system + browser convergence inevitable but integration
is the hard part.

Demo: creating PowerPoint, analyzing calendar, finding duplicate files
— all running in parallel across separate Co-work threads with mid-task
feedback via queue button.
