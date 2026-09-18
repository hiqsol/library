---
title: "Omarchy and the Agentic Desktop: Making an Operating System Personal"
author: Nate B. Jones
channel: AI News & Strategy Daily | Nate B Jones
url: https://youtu.be/zDPuEPDXCpU?is=CLIJlOXZKJRJfE5Q
date: 2026-09-11 14:00
tags: ai, development
---

# Omarchy and the Agentic Desktop: Making an Operating System Personal

An operating system looks neutral only because its choices have become familiar. Where
notifications appear, which apps open, how windows move, and what can be automated are
all decisions made for a mass audience. Nate B. Jones's argument is that AI agents can
lower the cost of revisiting those decisions. The important change is not an "AI OS" as
a new product category. It is software that an individual can reshape for an audience of
one.

Omarchy is Jones's clearest example, not a prescription that everyone should replace macOS
or Windows. It shows what happens when a desktop exposes enough structure for an agent to
inspect a preference, change it, reload the relevant component, observe the result, and
reverse the change. The broader lesson applies to any system with usable handles.

> Source note: This article explains claims and examples presented by Nate B. Jones in his
> video and description. Product details, user reports, and security behavior are attributed
> to Jones unless otherwise stated; they were not independently verified here. The source
> transcript comes from automatic captions, which may contain errors in names, terms, and
> wording.

## Software for an audience of one

Traditional software economics reward features that serve many users. A family may still
need rules designed for one child, not for an abstract average household. Jones gives the
example of a father who wanted two different screen-time systems. One child's computer
would lock when time expired and award more time after multiplication exercises. Another
child needed a recorded parent-child agreement rather than locks and rewards.

That example is not mainly about parental controls. It demonstrates a new threshold for
software worth making. If an agent can assemble or adapt the behavior cheaply enough, one
person's unusual requirement can justify its own implementation. Open source always gave
users legal permission to modify software, but permission was not the only obstacle. A
user also had to understand the system, find the correct file or setting, make the change,
test for side effects, and recover if it failed. An agent can reduce that expertise and
effort, although it does not remove responsibility.

This changes the role of defaults. Defaults remain valuable because most people want to
open a computer and work. Personal software does not abolish defaults; it makes selected
defaults negotiable when the benefit exceeds the cost and risk of changing them.

## Omarchy's design: a coherent desktop with agent handles

Jones describes Omarchy as a Linux desktop assembled by David Heinemeier Hansson, or DHH.
It arrives with applications, shortcuts, window management, and a visual system already
chosen. That coherence matters: personalization starts from a working opinionated system,
not a box of unrelated parts.

According to Jones, Omarchy 4, called Quattro, brought the bar, launcher, notifications,
and other desktop controls into a programmable system called QuickShell. He says it also
added a plug-in system and easier access to a chosen coding agent. The exact release facts
should be checked against current Omarchy documentation before acting on them.

The decisive feature is not visual style. It is the availability of **agent handles**:
readable configuration, documented commands, supported actions, reload mechanisms, and
observable results. A useful tool should let an agent answer three questions:

1. Can it invoke the required action?
2. Can it read what happened?
3. Can it write or supply the necessary input?

A graphical control hidden behind an unreliable sequence of clicks is a weak handle. A
known configuration file plus a documented reload command is a strong one. An agent that
can act but cannot inspect the outcome is also incomplete; it needs feedback to distinguish
success from a plausible-looking failure.

This is why the sensible first experiment is small and reversible. Instead of asking an
agent to "redesign my desktop and make it magical," specify a concrete rule: put the
browser on the right, notes on the left, or a particular app on the second display. Ask the
agent to identify the setting, preserve the original, make the edit, test it, and undo it.
That cycle teaches both the system's capabilities and its limits without betting the whole
machine on one prompt.

## Omaport: customize the experience, reuse the machinery

Omaport illustrates another part of the argument: personal software need not reimplement
every hard layer underneath it. Jones recounts a French web developer who missed a Mac-like
file-transfer workflow after moving to Omarchy. The desired experience included saved
connections, a remote file browser, and a transfer queue.

According to Jones, the resulting Omaport application wraps **rclone**, an established tool
for connecting to remote storage. The agent did not invent file transfer from first
principles. It helped build a personal interface and workflow around maintained underlying
machinery.

That division is a practical model for agentic software. Keep the difficult, general
service stable; adapt the local presentation and behavior. The individual gets the part
that matters personally without assuming responsibility for every protocol and edge case.
The caveat is that the wrapper, its dependencies, and any plug-ins still form a software
supply chain. A custom surface is not automatically a trustworthy one.

## Permission is a ladder, not a switch

An agent can read a configuration file, edit it, install a package, or operate with
administrator rights. Those are different powers and should be approved separately. A
model's confidence or enthusiasm is not evidence that a higher tier is necessary.

A safer progression is:

1. Let the agent inspect documentation and relevant settings.
2. Permit a proposed edit only after it names the file and explains the change.
3. Keep a backup and require a narrow test with a clear success condition.
4. Grant package installation only when the task actually requires it.
5. Reserve administrator access for a specific, justified operation.

Jones says Omarchy documents an option for 15 minutes of passwordless administrator
access. He also stresses the trade-off: during that window, every process running as the
user may be able to use that access, not only the agent that requested it. A time limit
reduces duration but does not create process-level isolation. Experienced users may accept
that exposure deliberately; it should not be the automatic answer to agent friction.

The same principle applies to virtual machines and shared folders. Jones says the Omarchy
Mac trial starts folder sharing disabled and can grant a guest read-write access to one
selected folder. A dedicated test folder is a useful boundary. Yet a virtual machine does
not make external consequences fictional. If the agent receives a real online account, it
can still send messages, delete cloud data, or make other real changes through that account.

Third-party scripts and plug-ins require a separate trust decision from the base system.
Check provenance, inspect what they modify, test them, and review requested access. Trust in
Omarchy, a model provider, or one developer does not transfer automatically to every add-on.

## Local control is not local processing

An agent may control a desktop locally while sending prompts, logs, documents, or screenshots
to a hosted model. Jones emphasizes that these are separate properties:

- **Local control** asks where the application and its effects are governed.
- **Local processing** asks where the model handles the data.

Omarchy is presented as optimizing for local control while leaving model choice to the user.
That flexibility is valuable, but it is not a privacy guarantee. Before asking an agent to
inspect a log or document, determine whether its contents may leave the machine, what the
provider retains, and whether local inference is actually in use. "Runs on my computer"
can describe the controller while the intelligence still runs elsewhere.

## What early users gain and surrender

The gain is unusually direct authorship over the daily environment. Jones cites an early
user who created a screen-edge light for video calls, a behavior the user reportedly could
not call out through the previous operating system. Omaport similarly turned a preferred
file-transfer experience into a working personal tool. Small irritations can become
specific, shareable changes instead of permanent compromises.

Early adoption also develops useful literacy: how agents inspect open-source software, how
to scope tasks, how to test changes, and where permissions expand. A spare machine can make
that learning lower impact because little else depends on it. Jones suggests that a retired
computer can be a reasonable playground, though its accounts and network access still need
careful limits.

What users surrender is part of the reliability subsidy supplied by mature platforms.
Jones relays an early user's complaints about sleep behavior and less dependable call
joining than on a Mac. Linux users may have to repair behavior that macOS and Windows users
take for granted. They also assume more responsibility for configuration drift, recovery,
plug-in provenance, model privacy, and deciding when an agent should receive elevated
rights.

The trade is therefore not "freedom versus no freedom." It is more authorship in exchange
for more operational judgment. If a task must work every time, Jones advises keeping it on
a proven system rather than moving it immediately to an experimental desktop. The last one
percent of dependability matters precisely because a primary computer is infrastructure.

## The same idea on macOS and Windows

Installing Omarchy is optional. The practical question is whether the operating system you
already trust exposes narrow, legible handles.

### AeroSpace on macOS

Jones presents AeroSpace as a Mac window manager with a readable configuration file and
documented commands. An agent can inspect a window rule, propose an edit, and use a command
to reload the configuration. That makes a recurring annoyance, such as placing the browser
on one side and notes on the other, a bounded problem with a result the user can judge.

The constraint is useful. AeroSpace gives the agent handles for window management, not a
license to rewrite every application or the operating system. Start by saving the current
configuration, make one rule, reload it, verify placement, and test rollback.

### Apple Shortcuts

Apple Shortcuts offers a more constrained form of agency. Jones notes that existing
shortcuts can be run from the command line and can accept input. A shortcut that prepares
copies of selected files for an application has known inputs, outputs, and folders. An
agent can select the inputs and invoke that established operation as one step in a larger
request.

This can be safer than asking a model to improvise every click. The workflow is defined in
advance and its authority can remain narrow. Caveats remain: some shortcuts require user
interaction, and only applications that expose useful Shortcut actions can participate.
Shortcuts do not make every Mac app inspectable or rewritable.

### PowerToys Workspaces on Windows

PowerToys Workspaces can capture and launch a collection of applications in a chosen
arrangement. A user who repeatedly opens several tools across particular screen regions can
turn that setup into a repeatable launch sequence. An agent can invoke the prepared
workspace to solve the specific setup problem without receiving broad read-write access to
Windows.

This is less dramatic than an agent rebuilding a desktop, and that is the point. A reliable,
narrow handle is often more useful than unconstrained computer control. It also preserves a
mature operating system's dependable base while making one routine personal.

## A practical adoption rule

Begin with an irritation that is frequent, observable, and reversible. Prefer an existing
supported mechanism over a new package, and prefer a maintained tool under a thin wrapper
over a fresh implementation of complex infrastructure. Before approving a change, require
the agent to state:

- the exact behavior it will change;
- the files, commands, accounts, and folders it will touch;
- the permission tier it needs and why;
- how success will be observed;
- how the original state will be restored; and
- whether any data will be processed outside the machine.

Then test with disposable data or a dedicated folder. Do not attach real accounts merely
because the agent runs in a virtual machine. Review each plug-in independently, and keep
critical workflows on the more dependable platform until the alternative earns trust.

## Personal without becoming fragile

The agentic desktop is not valuable because it maximizes what an agent can touch. It is
valuable because it makes the right parts of a computer legible and changeable at the right
scope. Omarchy points toward desktops whose defaults are coherent but not final, whose
actions can be invoked and observed, and whose modifications can be shared without becoming
mandatory for everyone.

The difficult design target is to be modifiable and dependable at once. Early Omarchy users,
as described by Jones, receive more room to make the machine theirs while accepting rough
edges and more security judgment. Mac and Windows users can take the same idea more
conservatively through AeroSpace, Apple Shortcuts, PowerToys Workspaces, and overlooked
native settings. In either case, the future is not one universal AI operating system. It is
a dependable base with enough well-bounded handles to let one person's computer fit that
one person.
