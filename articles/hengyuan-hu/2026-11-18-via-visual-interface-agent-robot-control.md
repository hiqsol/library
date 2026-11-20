---
title: Coding Agents Can Control Robots, but VIA Is Slow and Heavily Scaffolded
author: Hengyuan Hu
channel: AI News & Strategy Daily | Nate B Jones
url: https://youtu.be/VkvoUCgHP6Q?is=z83qrjwyMstlrfJx
date: 2026-11-18 16:00
tags: ai, technology
---

# Coding Agents Can Control Robots, but VIA Is Slow and Heavily Scaffolded

[summary](../../summary/hengyuan-hu/2026-11-18-via-visual-interface-agent-robot-control.md)

Stanford researchers connected off-the-shelf coding agents to robot controllers through a
visual interface. Their VIA system completed 24 of 25 trials across five physical tasks with a
Stretch 4 mobile manipulator. The foundation model received no robot-specific fine-tuning, but
the system was not an unmodified coding agent plugged directly into motors.

VIA supplied a custom visual workspace, robot descriptions, calibrated cameras, depth
estimation, Model Context Protocol tools, task prompts, and conventional controllers. The
agent selected and refined waypoints while lower-level software executed safe motions. This
division is the paper's main engineering contribution, not a detail that can be omitted from
the result.

The experiment provides strong feasibility evidence for robot-use agents on quasi-static
tasks. It does not establish reliability across environments, real-time control, autonomous
safety, economic viability, or the eventual displacement of specialized robotics models.

## The study behind the headline

The source is *VIA: Visual Interface Agent for Robot Control* by Hengyuan Hu, Jensen Gao,
Priya Sundaresan, Satvik Sharma, Jeannette Bohg, and Dorsa Sadigh of Stanford University. The
first arXiv version appeared in July 2026 and version two was posted on October 7.

The paper asks whether capabilities developed for coding and computer use can transfer to
robot control when the robot is presented as another interactive visual application. It
evaluates Claude Code and Codex with several model tiers in simulation, then uses Codex with
Astra 6 for physical experiments.

The video's automatic transcript renders the physical model as “Codex Astra 6.” The accurate
interpretation is the Codex agent powered by Astra 6. It also turns *uni-robot-agent* into
“just RUA” in a later comparison.

## How VIA works

VIA places a virtual target gripper over camera images or a reconstructed point cloud. The
coding agent can inspect a screenshot, click a point, translate or rotate the target, preview
the change, and adjust it before committing a physical motion.

When satisfied, the agent submits a waypoint. A conventional controller then moves the actual
gripper toward the target while respecting the robot's control interface. After the motion,
the agent receives a new observation and chooses another waypoint.

This creates two nested feedback loops:

1. a virtual loop in which the agent stages and checks a target without moving the robot;
2. a physical loop in which it executes a waypoint, observes the result, and replans.

The distinction matters. The model does not calculate every motor command at control
frequency. It selects sparse target poses, gripper states, and mobile-base movements. PI
controllers, motion limits, and robot software handle the intervening motion.

The interface is deliberately legible to a model trained for computer use. MCP tools expose
operations such as taking snapshots, probing image locations, editing the virtual gripper,
opening or closing it, and executing a waypoint. The paper compares this with posing an object
in 3D software.

## What “no extra training” means

The headline is accurate in one narrow sense: the tested Claude Code and Codex models were
used without gradient updates on robot demonstrations. The physical Astra 6 system also did
not learn a new robot policy from the five tasks.

It does not mean that the system lacked robot-specific engineering or information. VIA
includes:

- a purpose-built visual robot-control interface;
- an MCP server with documented robot tools;
- a system prompt explaining the robot, interface, and closed-loop workflow;
- RGB and depth sensing, camera calibration, and robot proprioception;
- a target-gripper representation aligned with controller degrees of freedom;
- low-level motion controllers;
- task descriptions and explicit success conditions;
- Fast-FoundationStereo depth estimation for the physical wrist camera.

The agent's model weights were unchanged, but its action space and observations were carefully
designed for robot control. “Zero-shot” here means no task-specific model training, not no
setup, no prompts, no robot software, or no prior robotics information in pretraining.

The paper says it adds no robot-specific fine-tuning or additional agent scaffolding. VIA
itself is a substantial robot interface and harness. The narrower point is that it reuses the
coding agents' existing tool loops and context management instead of training a new agent
policy.

## Simulation design

The simulation used a Franka Panda arm in robosuite on six tasks:

- rotate a stove knob;
- open the middle drawer;
- place a bowl precisely on a plate;
- put a square nut on a square peg;
- arrange seven blocks as a rainbow;
- build a stable T-shaped block structure.

Each agent-model configuration received ten randomized seeds per task. Standard episodes had a
one-hour wall-clock cap, while the Rainbow task allowed two hours. Memory across episodes,
internet search, and file access to benchmark state were disabled.

VIA was compared with a baseline that received the same images, point clouds, proprioception,
agent, and controller but could not preview targets in the visual interface. Its controller
commands executed immediately.

## Simulation results

Success increased with model tier. Overall VIA success across the six tasks was:

- 43.3% for Claude Code with Sonnet 5;
- 65.0% for Claude Code with Opus 4.8;
- 85.0% for Claude Code with Fable 5;
- 38.3% for Codex with Terra 5.6;
- 73.3% for Codex with Sol 5.6;
- 100% for Codex with Astra 6.

Astra 6 succeeded on all ten seeds for every simulated task. Yet the interface contributed
less at that tier: the no-interface Astra baseline scored 93%, compared with VIA's 100%. For
weaker models, the ability to stage and inspect a target produced larger gains.

Human-written detailed instructions gave mixed and modest improvements. Across five tasks,
Claude Code with Opus rose from 62% to 76%, while Codex with Sol rose from 68% to 74%.
Individual tasks sometimes got worse, showing that added instructions are not uniformly
helpful.

These are author-run benchmark results rather than independent replication. Task counts are
limited, model and system versions are contemporary, and several tasks use binary success
checks in simulation.

## The 24-of-25 physical result

The physical evaluation used a commercial Stretch 4 mobile manipulator. Codex with Astra 6 ran
five trials on each of five tasks:

- turn on a lamp by pulling its chain: 4/5;
- open a drawer and put a toy lion inside: 5/5;
- fold a towel diagonally: 5/5;
- pull out a wipe and clean a black mark: 5/5;
- open a basket lid: 5/5.

The aggregate was 24/25, or 96%. The initial robot location was randomized, along with
task-specific object locations, poses, or mark shapes.

The result covers only five repetitions per task in one research setup. A single additional
failure would have changed the aggregate to 92%. The study establishes that the system can
perform these specific tasks, not a 96% reliability rate for general robot work.

## The wipe behavior is real but should not be called learning

During wiping, the gripper obscured the table. The agent moved it away after several wipes to
inspect whether the mark remained. In one run, holding the wipe did not clean effectively, so
it dropped the wipe and pushed it with a closed gripper.

This is credible closed-loop adaptation within an episode: observe, act, inspect, and change
strategy. The model weights did not update, and the behavior was not retained as a newly
learned policy across trials. Calling it “sophisticated learning behavior” blurs
inference-time replanning with learning.

Other qualitative behaviors included remembering a toy and drawer that could not be viewed
together, retrying after a basket lid slipped, and searching for a lamp once its cabinet
entered view. The one physical failure occurred when the agent grasped the lamp stem rather
than its similar-colored chain.

## Cost and latency

The paper reports simulation API costs only for successful default-prompt episodes. Averaged
equally across tasks with a success, estimated costs were:

- $5.30 for Claude Code with Sonnet 5;
- $11.20 with Opus 4.8;
- $16.30 with Fable 5;
- $2.40 for Codex with Terra 5.6;
- $2.80 with Sol 5.6;
- $3.20 with Astra 6.

Successful Astra simulation episodes averaged 51 MCP tool calls. The Rainbow task averaged 136
calls and $7.60. Failed episodes were omitted from the cost table because they often ran until
timeout, so the figures are not full expected costs per attempted job.

The paper does not report equivalent per-task wall-clock durations or API costs for all 25
physical trials. Its authors explicitly identify inference as slow and expensive. VIA is
restricted to quasi-static tasks and is unsuitable for dynamic jobs such as catching a ball.

This limitation is not cosmetic. A robot must perceive and react before the world changes, and
an hour-long successful run may be impractical even if the final state is correct.

## The separate Astra study

The video's speed example comes from *Has GPT-6-Astra Achieved Embodied Intelligence?*, posted
in October 2026, not from VIA.

On a Unitree G1 humanoid, Astra completed two of three plush-toy pick-and-drop trials and all
three walking trials. The two successful manipulation runs lasted about 74 minutes 31 seconds
and 87 minutes 47 seconds.

Across 108 archived API calls, median request latency was 24.84 seconds. API request time
accounted for 88.8–91.7% of elapsed run time. This supports the video's approximate statement
that deliberation consumed around 90% of the time, though the paper measures API request wall
time rather than a clean scientific category called “thinking.”

The G1 setup used an operator emergency stop. Manipulation locked the waist, legs, and body
height; the model chose arm targets and binary hand profiles, while controllers executed them.
Two successes out of three establish feasibility, not operational reliability.

## Harness quality can dominate model comparisons

The November paper mentioned in the video is most plausibly *Democratizing Robot-Use Agents: A
Unified Harness with Open Models*, which introduced *uni-robot-agent*. The transcript's “just
RUA” is not the paper's name.

With the same Qwen3.8-Flash-Next model on RoboDojo, reported score changed sharply with the
harness:

- 1.90 with RoboProbe;
- 7.75 with RPent;
- 21.01 with the hybrid GAP harness;
- 31.39 with uni-robot-agent.

The paper attributes gains to structured robot descriptions, camera calibration, shared tools,
informative feedback, context handling, monitored motion, and overlapping model reasoning with
tool execution. That result reinforces the importance of system design.

It should not be read as a clean ablation of one software change. The harnesses differ in
multiple ways, and the 31.39 result is a paper-specific RoboDojo score, not a general robotics
capability percentage. Still, it demonstrates why benchmark claims cannot be attributed to the
foundation model alone.

A different October paper, *OpenRUA*, takes the opposite interface approach. It gives a coding
agent terminal access to ROS 2, documentation, and starter tools rather than a bespoke visual
action layer. It reports strong simulation performance, but it is separate from the November
study discussed in the video.

## The Bitter Lesson is an interpretation, not an experimental conclusion

Richard Sutton's 2019 essay argued that general methods leveraging increasing computation,
especially search and learning, have repeatedly overtaken systems built around human domain
knowledge. His examples include chess, Go, speech recognition, and computer vision.

VIA is consistent with one possible extension of that lesson: improvements in general visual
reasoning, tool use, and context management can transfer into robot tasks without retraining
the model. The simulation scaling trend and physical feasibility results support that
possibility.

But VIA is also full of human-designed structure. Researchers selected waypoint control,
designed the virtual gripper, exposed calibrated views, wrote tool semantics, chose
controllers, and specified task success. General model capabilities and robotics engineering
are complements in this system.

The study does not compare long-run scaling laws for general agents against equivalently
funded specialized robot policies. It cannot establish that one paradigm will overtake the
other.

Specialized models can also exploit more data and computation. They may retain advantages in
control frequency, latency, energy, safety, predictable behavior, and on-device operation. The
video's more careful acknowledgment of this point is warranted.

## OpenAI's reorganization

Reporting in Fortune, summarized by The Decoder, says OpenAI reorganized rather than abandoned
its robotics effort in November 2026. Robotics researchers moved into the main research
organization under Mark Chen, while applied robotics and hardware moved into Greg Brockman's
Applied organization.

OpenAI clarified that robotics work continued. Reporting connected the decision to the
increasing robotics usefulness of general-purpose models and also discussed business pressure.
That supports the video's organizational description.

It does not prove the company's sole technical thesis or validate VIA. Internal restructuring
can reflect staffing, product, financial, and research considerations simultaneously. Claims
that OpenAI is “organizing around the Bitter Lesson” are the narrator's interpretation rather
than a quoted experimental finding.

## What transfers, and what remains unproven

The evidence supports transfer of several useful capabilities:

- visual target selection;
- multi-step task decomposition;
- tool use through documented interfaces;
- retaining state within a long episode;
- inspecting outcomes and attempting recovery;
- using general model improvements without robot fine-tuning.

It does not yet establish:

- fast continuous control in changing scenes;
- safe operation near people;
- recovery from irreversible failures;
- robustness across unfamiliar hardware and environments;
- unattended operation over long periods;
- lower total cost than specialized policies;
- household-scale reliability;
- automatic transfer from every software-agent improvement.

The tasks were mostly quasi-static, and controllers absorbed substantial motor-control
complexity. No experiment tested rapidly sliding objects, human interaction, cluttered
industrial throughput, or safety-critical edge cases.

## Practical implications for builders

The strongest near-term lesson is architectural. A foundation model need not output actuator
commands to contribute to robot control. It can select goals, use a visual workspace, inspect
execution, and leave high-frequency motion to deterministic or learned controllers.

Interfaces should expose enough state for diagnosis without overwhelming the model.
Previewable actions can prevent expensive physical mistakes. Structured tool results,
calibrated geometry, controller feedback, and explicit success checks may matter as much as
model choice.

Evaluation should report more than final success. Useful measures include:

- elapsed time and model latency;
- interventions and emergency stops;
- expected cost over both successes and failures;
- collisions and near misses;
- recovery after changed conditions;
- performance on unseen tasks and hardware;
- throughput relative to specialized baselines;
- reliability across many more than five trials.

A robot that eventually completes a task while requiring continuous supervision may consume
more human attention than it saves.

## Forecasts should remain forecasts

The video predicts that 2027 will be a major year for this approach and advises developers to
look for robotics consequences whenever a new frontier model appears. That is a plausible
strategy, not an experimental result.

The claim that household robots have not taken off because physical coordination is easier
than complicated problem-solving is also incomplete. Hardware cost, safety certification,
maintenance, manufacturing, energy, dexterity, data, liability, and consumer economics all
matter.

A model update may improve an existing robot stack if the interface exposes the right
observations and actions. Transfer is not automatic, and the system still requires
integration, validation, and safety engineering for each embodiment and deployment setting.

## Bottom line

VIA shows that a frontier coding agent can use a carefully engineered visual interface to
control a commercial robot across five quasi-static tasks without robot-specific fine-tuning.
The 24/25 result is correctly reported and includes meaningful within-episode replanning.

The agent did not directly control every motor, learn a new policy during the task, or operate
without robot-specific scaffolding. The evaluation is small, latency is high, costs exclude
failures, and the paper explicitly limits the method to slow environments.

The work strengthens the case for robot-use agents as a research direction. It does not settle
the competition with specialized robotics models or show that general coding-agent updates
alone will make robots fast, safe, reliable, and economical.

## Sources

- Hu et al., *VIA: Visual Interface Agent for Robot Control*. arXiv:2607.11119v2.
- Sutton, *The Bitter Lesson* (2019).
- Chu et al., *OpenRUA: Robot-Use Agents Are Zero-Shot Visuomotor Policies*.
arXiv:2610.02459.
- Joint Research Team, *Has GPT-6-Astra Achieved Embodied Intelligence?*.
arXiv:2610.22471v2.
- Yuan et al., *Democratizing Robot-Use Agents: A Unified Harness with Open Models*.
arXiv:2611.01560v2.
- Isola, *Robot-use agents*.
- The Decoder, *OpenAI reassigns robotics researchers to other teams*.
