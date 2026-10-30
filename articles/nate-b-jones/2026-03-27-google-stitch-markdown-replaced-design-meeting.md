---
title: "A Markdown File Just Replaced Your Most Expensive Design Meeting. (Google Stitch)"
author: Nate Jones
channel: Nate B Jones
url: https://www.youtube.com/watch?v=CDClFY-R0dI
date: 2026-03-27 00:00
tags: ai, development
---

# A Markdown File Just Replaced Your Most Expensive Design Meeting

[summary](../../summary/nate-b-jones/2026-03-27-google-stitch-markdown-replaced-design-meeting.md)

Three big creative tool releases dropped in the last week that builders
need to pay attention to. This is not about taking jobs away from
designers — it's about rethinking how we do design in the age of AI.

## 1. Google Stitch — Voice to Design

Google updated Stitch, a free tool where you describe an app in words
and it draws the screens for you. Not wireframes — finished-looking UI
with multiple pages at once. You can talk to it out loud and it designs
in real time. Voice to design is now real.

It's connected to coding tools, so you don't have to wonder whether the
design is buildable. There's no more exporting to Figma. This is why
Figma stock tanked — when your entire value proposition is built around
the idea that job families are separate, you get into trouble in the era
where roles blur and everyone moves toward the command line.

### What Stitch Actually Does

You open a canvas, talk to it via voice mode, and describe what you
want. For example: "Design a landing page for an AI writing assistant.
Hero section with headline and CTA, feature sections with benefit cards,
pricing section with two tiers." Stitch generates complete high-fidelity
screens — real typography, real color palettes, good spacing, good
component hierarchy.

The design agent holds the entire project context — all screens, all
decisions, every piece of reference material you've dropped onto the
canvas. It reasons across all of it when you ask for changes. If you
want three different navigation layouts, it sees the original and knows
how to adjust. Want the whole app in a dark palette? Just say so.

You can branch and compare design directions, pursuing five different
approaches simultaneously and evaluating them side by side. You get
instant prototyping that converts any static design into a clickable
flow. Stitch even auto-generates the logical next screen based on user
interactions, predicting what comes after a button press by reasoning
about the product structure.

It's free — 350 generations a month for nothing.

### The Design Markdown File

The most interesting feature that most coverage missed: the
design.markdown file. This export from Stitch gives you a full
agent-readable file that captures a project's design system. You not
only export the code, but get a durable record of colors, typography,
spacing rules, and component patterns. You can extract them from any
URL — point to a site you admire and pull the design markdown.

Google isn't locking this into their ecosystem. It's MCP-readable,
meaning you can grab it from Claude Code, ChatGPT, or Google's own
tools. Google even shipped official Claude Code skills — a sign of how
dominant Claude is when Google has to ship Claude Code skills with
their launch.

The pipeline: design the business objective → Stitch generates the UI →
coding agent reads the design.markdown file and starts building. No
Figma export. No handoff document. No "the developer got the design
document wrong."

### Honest Assessment

The design quality is not yet at a point where most senior designers
would sign off on it. But it's better than a prototype, and this is
the dumbest and worst it will ever be. View it as a magic junior
designer in a box — faster and better at prototyping, not perfect,
especially without clear intent.

## 2. Remotion — Video Becomes Code

Remotion is a React framework that treats video as code. In January
2026, they launched an agent skill for Claude Code. Within 48 hours,
their demo had over 6 million views. Eight weeks later, the skill sits
at 150,000+ installs on skills.sh — the number one skill not made by
Vercel, Anthropic, or Microsoft.

You install the Remotion skill into Claude Code with a single terminal
command, describe the video in plain English, and Claude writes the
React components that define every frame — text animations, motion
graphics, data visualizations, captions, transitions. Remotion renders
all of those components into an MP4. The whole loop runs locally on
your machine.

### Not AI-Generated Video

This is fundamentally different from tools like Sora and Runway that
generate pixels from prompts. Remotion generates code that renders
video. Every element is a React component you can modify, version
control, and parameterize. Change one variable, re-render 100 localized
versions — free. Update the data source and every chart in the video
updates automatically.

This is programmable video, which is in some ways more powerful than
generative video because it's easier to edit and adjust. One creator,
Sabrina.dev, documented generating a promotional video from one prompt,
having Claude browse the web to take real screenshots of GitHub repos,
then adding her headshot and background music from follow-up prompts.
No Premiere, no After Effects, no timeline editor.

### Sweet Spot

Clean motion graphics: text animations, data visualizations, product
demos, terminal recordings. Complex overlapping elements and fancy
transitions may not render perfectly yet.

## 3. Blender MCP — 3D Gets a Chat Window

Blender is a professional-grade creative tool for 3D modeling,
animation, rendering, and simulation. Its interface has roughly 1,500
operators and a learning curve measured in years.

Blender MCP simplifies all that. Type a natural language description
like "create a beach scene with palm trees and sunset lighting" and
watch the 3D environment assemble itself in real time. Claude
manipulates Blender's tool sets through a socket-based bridge to
Blender's Python API.

The repo has 17,000+ GitHub stars and 1,500+ forks. It integrates
with Polyhaven for free high-quality assets and with SketchFab for a
wider library. You can connect it to Hyper 3D for text-to-3D model
generation — describe a character, have it generated, and drop it into
your scene without leaving the conversation.

## The Bigger Picture: MCP Is the USB Plug for AI

The commonality across all three tools: they all depend on MCP, the
universal standard for AI connectors. MCP is becoming the USB plug
for AI — take a tool, make it an MCP server, and it becomes available
at the command line. That's how Remotion went from a website to a
fast-growing GitHub community. Making your product an MCP is the
growth hack of 2026.

## The 2010s Product Triangle Is Blurring

The 2010s-era triangle of product, engineering, and design is blurring
together. In the past, teams were gated by the ability to sequentially
get pixels on the page and then later find out if it was buildable.
The best teamwork happened when everyone was collocated around one
screen.

Now at the command line, you invoke something that is by definition
buildable — if it's not buildable, Claude Code can't touch it. You can
bring in multiple design iterations very quickly. Designers at
Anthropic and OpenAI are in the code, working from the command line,
working from component libraries, putting things together rapidly so
they don't slow the team down.

## Scheduling Creative Pipelines

Claude's cloud-based scheduling tasks (announced March 20th) change
the game further. You can:

- Schedule a weekly job that pulls all shipping from the past week and
  generates a Remotion video summarizing key points with motion graphics
- Schedule a daily job that checks analytics and generates a data
  visualization video for the team Slack
- Schedule a job that monitors your changelog and regenerates updated
  UI screenshots via Stitch for the marketing site

The entire pipeline from idea to artifact is now describable in
English, executed by agents, and scheduled to repeat autonomously.

## The Floor Dropped, the Ceiling Didn't

The pattern across 20 years of creative tool disruption (Photoshop →
Canva, After Effects → simpler tools, Sketch → Figma, Figma → AI):
a new tool lowers the floor of who can produce good-enough work.
Incumbents panic, then reality sets in. The floor dropped, but the
ceiling didn't move. Excellence still matters.

The difference now is how deep the floor dropped — when it's basically
free to generate designs, the floor dropped into the basement. The
skill shifts from "can you execute the thing" to "can you polish the
thing, identify what's not good enough, make the specific edit, do it
quickly and consistently."

The people who win are not those who individually master these tools.
It's the people who can articulate precisely how they want something
expressed visually so it conveys the experience that actually matters
to the customer. Clarity of intent is the differentiator in the age
of AI.

High-quality designers are still needed — to offer judgment, to take
these new paintbrushes and create incredible designs. What's been freed
is the time spent in creative tools that wasn't creative: moving layers,
adjusting keyframes, exporting formats, rebuilding the same layout for
the third time because a stakeholder changed one word. The density of
actual creative decisions can now go up.

Design is following development. Developers knew the command line was
the right interface for execution at scale. Creative work has arrived
at the same insight. As long as you can describe it, you can create it.
