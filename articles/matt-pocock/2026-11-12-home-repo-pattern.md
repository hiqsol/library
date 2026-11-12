---
title: Using a Home Repo to Coordinate Coding Agents Across Repositories
author: Matt Pocock
channel: Matt Pocock
url: https://youtu.be/hWe-j78vNpc?is=I9HOw20FCQfkoN03
date: 2026-11-12 12:55
tags: ai, development
---

# Using a Home Repo to Coordinate Coding Agents Across Repositories

[summary](../../summary/matt-pocock/2026-11-12-home-repo-pattern.md)

A Home Repo is a small coordination repository for coding agents that need to navigate
several independent codebases. It contains shared skills, cross-project documentation, and
pointers to other repositories. Agent sessions start there, then enter only the repositories
needed for a task.

Matt Pocock presents the pattern as a simple alternative to copying the same steering files
across many repositories. It can improve navigation and reduce duplicated guidance, but it
does not create access controls, atomic cross-repository commits, or safe isolation. Those
properties still require tooling and policy outside Markdown instructions.

## The multi-repository problem

A product may have separate repositories for a storefront, payments API, admin dashboard,
internal tools, and documentation. An agent launched in one repository can sometimes open a
second directory, but its startup context normally comes from the first workspace and the
agent harness's own discovery rules.

Teams often respond by copying skills, `AGENTS.md`, `CLAUDE.md`, coding standards, and wiki
links into every repository. Those copies drift. Keeping them aligned across 30 or 40
repositories becomes its own maintenance task.

User-level configuration solves visibility for one machine, but it is less discoverable,
harder to review as a team, and prone to mixing personal preferences with organization-wide
policy. The Home Repo instead makes genuinely shared material a versioned project.

## The basic layout

The Home Repo sits beside the code repositories rather than absorbing them:

```text
~/repos/
├── home/
│   ├── AGENTS.md
│   ├── CLAUDE.md
│   ├── skills/
│   ├── docs/
│   ├── wiki/
│   ├── repos/
│   └── tooling/
├── storefront/
├── payments-api/
└── admin-dashboard/
```

The child repositories remain independent Git repositories with their own history, remotes,
issues, branches, pull requests, and CI. Code and repository-specific instructions stay with
their code.

A navigation section can be as simple as:

```md
## Other Repos

Storefront: ~/repos/storefront.
Clone from git@github.com:acme/storefront.git if missing.

Payments API: ~/repos/payments-api.
Read its AGENTS.md before changing it.
```

Matt also describes cloning child repositories inside the Home Repo and ignoring them. Sibling
checkouts are usually clearer because nested repositories are independent Git trees, not a
single project. If exact child revisions matter, submodules or a lock manifest provide a
property that plain pointers do not.

## What belongs in each place

The Home Repo is suitable for material that is true across repositories:

- shared coding and review standards;
- organization-wide terminology and architectural decisions;
- reusable agent skills;
- common debugging, testing, and release procedures;
- a Markdown wiki or system map;
- repository locations, clone URLs, owners, and responsibilities;
- shared orchestration scripts and integration tooling.

The child repository should retain anything specific to its own operation:

- build, test, and deployment commands;
- service architecture and domain rules;
- repository-specific security requirements;
- local coding conventions and generated-file policies;
- source code, version history, issues, and release configuration.

Security-critical instructions should not exist only in the Home Repo. Contributors, CI, and
agents launched directly in a child repository must still see the rules that protect it.

## A careful migration process

Matt's article proposes four stages.

First, inventory Git repositories, their paths, remotes, visibility, and recent activity.
Decide which repositories belong in the workspace, whether the Home Repo is personal or
shared, and which instruction file the agent harness actually loads.

Second, inventory skills and steering material. Classify each item as shared, duplicated,
repository-specific, or installed through an external package or marketplace. Comparing
copies matters more than choosing whichever file has the latest modification time.

Third, approve a migration table before changing files. Move shared material to the Home
Repo, leave repository-specific guidance in place, and preserve externally installed tools
through their original distribution mechanism.

Fourth, apply the plan incrementally. Create a branch in each affected child repository,
copy shared material, remove reviewed duplicates, and commit the Home Repo separately. Test
the result from a clean environment before treating it as portable.

Useful validation includes checking that every pointer resolves, every clone URL matches the
expected remote, and no repository lost instructions required for local work.

## Daily workflow

A cross-repository task can follow this sequence:

1. Start the session in the Home Repo.
2. Select the minimum repositories needed for the task.
3. Record each repository's path, remote, branch, HEAD, and dirty state.
4. Grant the agent read access first and write access only where needed.
5. Load the child repository's own instructions explicitly.
6. Use a separate worktree and branch for each repository and task.
7. Make and test independent commits in each repository.
8. Record dependency order, compatibility requirements, and rollback steps.
9. Open separate pull requests and run cross-repository integration tests.
10. Verify that no unselected repository changed.

Worktrees let multiple sessions use one clone without sharing a checkout. They still require
unique branches, separate caches or ports when needed, and cleanup of stale worktrees.

## Tool support is not uniform

A pointer in `AGENTS.md` tells an agent where a repository is; it does not grant access.
Claude Code and Codex can accept additional directories, but those directories normally need
to be added explicitly. Their instruction-discovery and settings behavior also differs.

Claude Code primarily uses `CLAUDE.md`; support for `AGENTS.md`, nested instructions, and
additional directories depends on configuration. Settings from an added directory may not
load like settings from the primary workspace. Codex builds an instruction chain from its
workspace root toward the working directory; a sibling repository is not automatically part
of that chain.

The portable lesson is to verify the effective instruction set before edits. A one-line
`CLAUDE.md` pointer to `AGENTS.md` can improve compatibility, but prose remains guidance, not
enforcement. Hard controls belong in permissions, hooks, sandbox mounts, and scoped identities.

## Security boundaries

A private Home Repo is not a secrets manager. It should not contain API keys, cookies, SSH
keys, OAuth tokens, `.env` files, or credentials embedded in clone URLs. Commit variable names
and setup documentation; inject values from a credential manager only when required.

Centralizing Gmail, Slack, Discord, GitHub, calendar, deployment, or publishing tools expands
the blast radius of one compromised session. Give each task the smallest set of repositories
and services it needs. Prefer read-only access, short-lived credentials, and explicit approval
for commits, pushes, messages, publication, deployment, or deletion.

External issues, messages, documents, dependencies, and child-repository instructions can
contain prompt injection. Do not combine untrusted pull-request content with broad
cross-repository write credentials. Analyze untrusted material in a read-only sandbox without
secrets, then pass a reviewed plan into a narrowly privileged execution stage.

Before and after work, compare canonical repository roots and changed paths against an
allowlist. Broad formatters, search-and-replace commands, generators, and deletion commands
can otherwise cross repository boundaries.

## Cross-repository Git is not atomic

A single agent session may produce several commits, but Git cannot commit or merge atomically
across independent repositories. One pull request can merge while another fails, temporarily
breaking an interface.

Prefer backward-compatible sequencing: add a new interface before switching consumers, then
remove the old interface only after adoption. A change-set manifest should record each repo,
base SHA, commit, pull request, dependency order, compatibility window, and rollback plan.
Integration tests should run against the exact combination of SHAs rather than moving default
branches.

In CI, cloning private repositories requires separate credentials; a token for one repository
usually should not grant organization-wide access. Pin every checkout, disable persisted Git
credentials when unnecessary, and separate unprivileged discovery from privileged PR creation.

## Scale and alternatives

Matt reports that a flat list works for dozens of repositories. At larger scale, group pointers
by business area and load only the relevant catalog. Progressive disclosure reduces context,
but it does not reduce authority unless access is also scoped.

A monorepo remains preferable when projects share ownership, visibility, and release tooling;
it supports atomic commits and native whole-system analysis. Other alternatives include
versioned skills packages, update bots for synchronized local files, Git submodules, multi-root
editor workspaces, and isolated per-repository agents coordinated by a planning service.

The safest extension of the Home Repo is an ephemeral task workspace. A controller selects the
needed repositories, checks out reviewed SHAs in a disposable sandbox, grants narrow access,
and emits separate patches or pull requests. This preserves shared navigation without giving
every session permanent access to everything.

## A calibrated conclusion

The Home Repo is useful as a catalog, shared knowledge base, and orchestration entry point. It
reduces copied steering material and helps agents reason across independently managed systems.
It is especially practical for a modest number of repositories within one trust domain.

It should not be mistaken for a monorepo, permission boundary, dependency lock, or transaction
coordinator. Reliable use requires explicit repository selection, child-specific instructions,
scoped credentials, isolated worktrees, reviewed diffs, pinned revisions, and coordinated
testing. The Markdown pointers make navigation convenient; the surrounding controls make it
safe.

## Sources

- Matt Pocock, *The Home Repo Pattern*, AI Hero, November 12, 2026.
- Anthropic, Claude Code documentation on memory, permissions, and security.
- OpenAI, Codex documentation on `AGENTS.md` and CLI directory access.
- GitHub, `actions/checkout` and workflow token-permission documentation.
- The `AGENTS.md` convention documentation.
