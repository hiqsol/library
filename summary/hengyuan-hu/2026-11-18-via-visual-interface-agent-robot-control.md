---
title: Coding Agents Can Control Robots, but VIA Is Slow and Heavily Scaffolded
author: Hengyuan Hu
channel: AI News & Strategy Daily | Nate B Jones
url: https://youtu.be/VkvoUCgHP6Q?is=z83qrjwyMstlrfJx
date: 2026-11-18 16:00
tags: ai, technology
---

# Coding Agents Can Control Robots, but VIA Is Slow and Heavily Scaffolded

[article](../../articles/hengyuan-hu/2026-11-18-via-visual-interface-agent-robot-control.md)

Stanford's VIA system lets an off-the-shelf coding agent control a robot through a visual
workspace. The agent previews and refines target gripper poses, then a conventional controller
executes each waypoint. It observes the result and replans in a closed loop.

Codex with Astra 6 completed 24 of 25 physical trials on a Stretch 4 robot: 4/5 lamp trials
and 5/5 each for shelf, towel-folding, table-wiping, and basket-opening tasks. Five
repetitions per task show feasibility, not a general 96% reliability rate.

“No extra training” means the foundation model received no robot-specific fine-tuning. VIA
still used a custom interface, MCP tools, robot descriptions, calibrated cameras, stereo
depth, task prompts, success conditions, and low-level controllers. Zero-shot does not mean no
robotics engineering.

The wiping example is accurately reported. When its gripper blocked the view, the agent moved
away to inspect the table. In one run it changed from holding the wipe to pushing it with a
closed gripper. That is inference-time adaptation, not learning retained in model weights.

In simulation, VIA success rose with model tier: Claude Code scored 43.3%, 65.0%, and 85.0%;
Codex scored 38.3%, 73.3%, and 100%. Astra's no-interface baseline already scored 93%, so the
interface's incremental effect was smaller for the strongest model.

Successful Astra simulation episodes averaged 51 tool calls and an estimated $3.20 in API
cost. Failed runs were excluded from cost averages. The paper does not give equivalent costs
and durations for all physical trials and explicitly limits VIA to slow, quasi-static tasks.

A separate October Astra study supports the video's latency warning. Two successful Unitree G1
manipulation runs lasted about 74 and 88 minutes. API request time represented 88.8–91.7% of
elapsed time, though this measures request latency rather than a pure category of model
“thinking.”

The transcript's “just RUA” most likely means the November *uni-robot-agent* paper. With the
same Qwen model, RoboDojo score ranged from 1.90 with RoboProbe to 31.39 with uni-robot-agent.
Harness design can dominate comparisons, but these systems differ in several ways rather than
one controlled change.

VIA is consistent with the Bitter Lesson: general visual reasoning and tool-use improvements
can transfer to robots. It does not prove that specialized robot models will disappear.
Specialized systems may retain advantages in speed, safety, cost, energy use, and predictable
high-rate control.

OpenAI reportedly moved robotics staff into research and applied teams while continuing the
work. Jones's Bitter Lesson framing is interpretation, not an experimental finding.

VIA shows varied quasi-static manipulation through a carefully designed interface. It does not
yet demonstrate real-time control, unattended safety, household robustness, economic viability,
or automatic transfer from every software-agent upgrade.
