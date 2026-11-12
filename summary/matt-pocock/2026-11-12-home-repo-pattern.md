---
title: Using a Home Repo to Coordinate Coding Agents Across Repositories
author: Matt Pocock
channel: Matt Pocock
url: https://youtu.be/hWe-j78vNpc?is=I9HOw20FCQfkoN03
date: 2026-11-12 12:55
tags: ai, development
---

# Using a Home Repo to Coordinate Coding Agents Across Repositories

[article](../../articles/matt-pocock/2026-11-12-home-repo-pattern.md)

## The pattern

A Home Repo is a small Git repository with shared agent skills, cross-project docs, and
pointers to independent code repositories. Sessions start there, then enter only the repos
needed for a task. Child repos keep their code, history, CI, and local instructions.

Matt Pocock proposes it instead of copying `AGENTS.md`, `CLAUDE.md`, skills, and standards
across many repos. Shared guidance becomes versioned and easier to maintain, while build,
deployment, domain, and security rules specific to one codebase remain beside its code.

## Workflow

Inventory repos and steering material. Classify every item as shared, duplicated,
repo-specific, or externally installed. Review a migration table, move only genuinely shared
items, and validate each pointer and remote before deleting duplicates.

For each task, select the minimum repos, record their HEAD and dirty state, and grant write
access only where required. Explicitly load each child repo's instructions. Use one worktree
and branch per repo, then create separate commits, pull requests, tests, and rollback notes.
Verify that no unselected repo changed.

A navigation pointer does not grant filesystem access. Claude Code, Codex, and other agents
differ in how they load sibling directories, instructions, settings, and skills. Markdown
steers behavior; permissions, hooks, sandbox mounts, and scoped identities enforce it.

A Home Repo is not a monorepo, secrets manager, revision lock, or cross-repo transaction
system. Store no credentials in it. Prefer read-only defaults, short-lived tokens, and
confirmation for pushes, messages, deployment, publication, and deletion.

Cross-repo changes are non-atomic. Record every base SHA, commit, PR, dependency order,
compatibility window, and rollback plan. Prefer backward-compatible rollout and integration
tests against exact revisions.

External issues, docs, dependencies, and child steering files can contain prompt injection.
Analyze untrusted content without secrets or broad write credentials, then execute a reviewed
plan with narrowly scoped access.

A flat catalog can serve a modest set of repos. At larger scale, group repos by business area
and load only the relevant section. This reduces context but must be paired with access limits.

Use a monorepo when shared ownership and visibility permit it. Alternatives include versioned
skill packages, update bots, submodules, lock manifests, and isolated per-repo agents with a
coordinator. An ephemeral workspace with selected repos and pinned SHAs is safer than
permanent organization-wide access.
The Home Repo is a useful navigation and shared-knowledge layer. Safe operation still needs
explicit scope, child-specific rules, isolated worktrees, scoped credentials, pinned
revisions, reviewed diffs, and coordinated testing.
