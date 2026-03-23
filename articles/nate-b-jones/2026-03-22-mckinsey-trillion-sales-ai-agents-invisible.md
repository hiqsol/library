---
title: "McKinsey Says $1 Trillion In Sales Will Go Through AI Agents. Most Businesses Are Invisible."
author: Nate B. Jones
channel: Nate B. Jones
url: https://www.youtube.com/watch?v=BE4RclIGDmY
date: 2026-03-22 00:00
tags: ai, startups, development
---

The fences that businesses spent 20 years building to keep bots out are now the very things keeping
their most valuable customers out. That is the central paradox driving the agentic commerce
revolution — and almost no one is talking about what it actually takes to survive it.

## The Structural Precondition Nobody Discusses

When Claude went from a weekend project to 250,000 GitHub stars, it became what Nvidia CEO Jensen
Huang called the operating system of the future — the operating system for personal AI. Everyone
jumped on that bandwagon. Nvidia built an enterprise platform. Announcements proliferated. But
nobody is talking about the structural precondition underneath all of it: the thing that determines
whether any of this actually works.

Claude only works as a paradigm if all systems are agent-readable and agent-writable. Not personal
systems — company systems, product systems. The actual transactional infrastructure. The systems
that let someone discover, evaluate, and buy need to be agent-readable and agent-writable at their
core, as if that is the first and most important use case.

Andrej Karpathy was right that 99% of attention in the future is going to be AI attention —
specifically, agent attention. Agents need somewhere to put that attention and actually act on it.
That means readable, writable companies. The entire company has to be agent-readable and
agent-writable.

All of those futures people demo — an agent that can manage your calendar, book flights, handle
purchases via WhatsApp — every single one depends on thousands of companies around the world being
agent-readable and writable. And that is a lot of work. It is not easy. There are nonobvious
implications that go undiscussed because the conversation stays fixated on Claude and personal
productivity, forgetting that the entire idea only works with a massive, ecosystem-level change
across thousands of companies.

## From Amazon to the Agent Economy

The author traces his understanding of this back to working at Prime Video, where teams were figuring
out how to use data to personalize title experiences. The discovery: if underlying data is not clean
all the way down the stack, the end customer experience is terrible. You cannot provide useful
customized experiences without it. That was pre-agent. Now think about how important it is when
agents can consume that data at scale — and need to provide not just visually appealing titles but
the entire product range as an agent-consumable interface first.

What Claude really demonstrated is that people are desperate for a unified agent that can talk to
everything in the digital world on their behalf. Vendors don't want this — they would not be under
pressure to deliver it without developers like Peter Steinberger (creator of Claude) hacking around
walls and insisting on command-line-first, chat-first agents.

WhatsApp is a classic example of something that is not agent-readable. Meta spent years figuring out
how to lock bots out. But because Claude is so successful, companies are being forced to rethink
that stance.

## The Anti-Bot Architecture Is Being Flipped

Everything learned in the 2010s is being reversed. Product teams were told bots were bad because
they polluted real human experiences — keep them out. Now the paradigm has shifted: bots are how
humans interact with the web.

It is like being told as a child not to get into cars with strangers, then taking Ubers as an adult
— or riding in a driverless Waymo. Technology forces behavior to shift. Fifteen-plus years of
anti-bot architecture is being turned around, and the challenge now is building pro-bot architecture.

This transition is not happening without a battle. Google has quietly moved to shut down Claude bots
using Google products and services. Apple recently moved to restrict or shut down vibe-coding apps,
including Replit, in its App Store. The big players still have incentive to keep their walls up —
but that is a losing battle. The people have spoken: they want agent-readable and agent-writable
systems.

Ironically, Apple itself benefited from a version of this dynamic. Napster got hammered with
lawsuits, but the paradigm of Napster survived and became iTunes, which helped the iPhone catch on.
Now Apple is facing its own Napster moment with Claude and responding like the old guard.

## The Trillion-Dollar Moment

McKinsey projects that by 2030, the US B2C retail market alone could see up to $1 trillion in
orchestrated revenue from AI agents. That figure may be conservative.

Google — the same Google working to shut down agent bots — launched the Universal Commerce Protocol
to let agents discover products, build carts, and complete checkout autonomously. Shopify CEO Toby
Lütke has called agentic shopping "the transformation of a lifetime." Over a million Shopify
merchants are coming online to allow agent-mediated transactions.

A concrete example that is possible today: type into an AI assistant "find me running shoes under
$120, size 10, that ship before Thursday, from a brand with flexible returns," and you get a chain
of searches and a useful response. The degree to which that response is accurate — and the degree to
which the agent can then transact — is entirely a function of agent-readable, agent-writable
infrastructure.

Nshift's research puts it bluntly: if delivery windows, shipping costs, returns, and product schemas
are unclear, the agent will skip over the offer without a human ever seeing it. You might have the
best product in the world, and if it is not agent-legible, it simply does not exist to that customer.

## Why It Is Harder Than It Looks

Here is the part nobody is talking about: making your company agent-readable and agent-writable
imposes enormous changes on your internal data stack. You cannot just stick an API on your existing
systems, wrap one thing in an MCP server, and declare victory. You have to think through from the
ground up what it means to make your product catalog entirely legible to agents.

This work has not been worth doing — until now — because humans are forgiving. Humans are
generalists. They skip details. As a result, businesses have built lazy systems for customer
interaction and gotten away with it. Agents do not forgive. A lot of marketing exists to paper over
the challenges that come from humans interacting with a product. That function is going away.

Consider Amazon's shipping promise: when you see a delivery date, that number is a specific promise
based on your geography and hundreds of internal factors. Without all that underlying data agreeing,
you never make that promise. Amazon's challenge — which it has been resistant to — is making that
promise agent-readable. The companies with the best data for this are often the most resistant,
because they fear losing the direct customer relationship. If customers are just talking to Claude or
ChatGPT to shop, they no longer care whether they are buying from Amazon.

## Two Real-World Examples

*Stripe* is probably the company most people point to as getting this right. They shipped an MCP
server that lets agents look up customers, process refunds, and manage subscriptions. But just
shipping an MCP server is not enough. Stripe has a deeper analytics layer called Sigma — it lets
you query and get full CSVs back with essentially unlimited data. The problem: if you just wrap
Sigma into an MCP, you will overload the context window. Real business data does not work the same
way when it lands in a context window rather than being saved to a CSV or a drive. You need an
intermediary — a database. Data needs to flow in, land in a table structure, and then be queryable
from a chat interface. At Stripe's scale and with the sensitivity of their data, agent security
becomes a major consideration. You cannot just knock together a database and call it done. Even
agent-leaning companies face this complexity.

*SAP* is on the other end of the spectrum. SAP is known for making it painful to get data out —
keeping data inside is their entire business incentive. SAP announced an MCP server for Commerce
Cloud, but the gap between a tiny slice of the SAP portfolio having AI features and all SAP
installations being agent-readable by default is the size of the Grand Canyon. For most SAP
installations in the wild, making systems truly agent-readable is a multi-quarter initiative at
best, and SAP has little incentive to push it.

The collective pressure of companies watching where customers are going will be what forces vendors
like SAP to become more agent-readable and writable. That pressure-building story will be one of the
most interesting of 2026, even if it does not make headlines like Claude does.

## Four Misconceptions

*Misconception 1: Optimize for agent discovery the way you optimized for search.*
A search engine returns a ranked list and lets the human choose. It can be influenced by brand
recognition, ad creative, and paid search. An agent does not browse a results page. It evaluates
structured data against explicit constraints and returns a result. There is no "above the fold" for
an agent. The companies that win will not have the biggest ad budgets — they will have the cleanest
schemas and the lowest-friction data interfaces.

*Misconception 2: Structured schemas only work for simple products.*
This is heard from companies in luxury, authenticity, or complex positioning — the idea that their
products are too special, too nuanced for structured data. This is a fundamental misunderstanding.
The more complex your business, the more you benefit from making it agent-readable. Complexity is
exactly what prevents customers from optimizing their purchases today — they settle for good enough
because evaluating all the variables is too hard. Give an agent structured access and let it find an
optimal answer. A honey-processed Ethiopian coffee with a farm story, sourcing transparency, and
roast specifications is a series of data reads — anything you can represent on a screen, an agent
can read and write against.

*Misconception 3: Customers won't trust agents to transact.*
Agent commerce does not start with "let the AI buy whatever it wants." It starts with long-horizon
intent delegation. A customer considering multiple sound systems says: here is my room configuration,
here is my budget, here is what my old system did well, here is the lossless audio I want to play.
The agent has a conversation, thinks about the right call, and helps the customer narrow in. Trust
is not binary — it is a spectrum that starts narrow and becomes wider and more permissive as
individuals trust the agent to do more. Your goal as a company is to enable more of your products
to be available across that trust spectrum. And for B2B SaaS, the consideration funnel is already
moving into agent world — people will specifically ask whether their agent can read and interact
with your application.

*Misconception 4: We'll just wait and see.*
This will kill companies. The work of cleaning data is not easy — it takes months, sometimes
quarters. Getting data ready to be agent-readable is its own project, separate from making the
interface available. Even companies leaning in, like Stripe, do not have it all figured out. If you
are waiting and seeing, you are signing your company's death warrant. By the time you understand
the agent ecosystem and say you are ready, it will have passed you by. Claude hit 250,000 GitHub
stars within a few weeks. That is how fast it is changing.

## The 80/20 Tribal Knowledge Problem

One of the highest-leverage — and least-discussed — insights of the agent moment involves what
might be called the tribal knowledge problem. Most businesses have roughly 20% of their product
meaning represented in data structures, and 80% living in marketing copy, in people's heads, in
product packaging. That 80% is exactly what customers will ask about when they talk to an agent.

"I want a basketball exactly like the one used in March Madness 2026." If your data does not say
"this is the same ball used in the 2026 March Madness tournament," you are going to miss that sale.
The agent will not read one blog post and say "that's good enough." Increasingly, agents will be
sophisticated enough to take a vague human intent and go deep — evaluating whether your product
claim is actually supported by technical credentials, not just a single case study on your blog.

A lot of that meaning exists in marketing copy and has to be fished out and converted into a format
that is agent-readable. That is a lot of work. And it is not optional work if you want to be visible
in the agent economy.

## The Whole 2010s Stack Was Built to Keep Agents Out

CAPTCHAs were built to keep agents out. Gated APIs were built to keep agents out. JavaScript-heavy
interfaces were built, indirectly, to keep agents out. All of it was designed around the idea that
bots are bad. But the most valuable traffic a business will receive over the next three years is
bots — AI systems acting on behalf of humans to discover, compare, and eventually transact.

The companies that make their systems easy to read and write against are the ones that will win.
That inevitably means making your data architecture complete — including all of that tribal
knowledge — and making it clean all the way down the stack. It will not be as simple as wrapping
existing APIs in an MCP server. That covers a few percentage points of the use case. It is a start,
low-hanging fruit, but it is not the end of the story, as Stripe has discovered.

## The Exercise

Go to your top three competitors. Have a meaningful conversation with Claude or ChatGPT and see how
far you can get toward transacting with them. Push to find what agent-readability and writability
they have. Then do it to your own company. Benchmark: how long and how hard is it to get data out?
Is there an MCP connector available? Is it enough? Do competitors have it? Could you lead in this
area, or do you need to rapidly catch up?

The companies that win in this world will think about agent attention first. They will structure
their businesses and their data around agent attention. And here is the counterintuitive bonus: if
you have all that complex tribal knowledge converted from marketing copy into data, it becomes very
easy to build great, personalized human experiences too. A personalized landing page about that
Ethiopian farmer and the school his coffee supports — the agent can suggest taking the customer
there, and it is trivially easy to build if your data is correct.

Build for agents first, and the humans will follow.
