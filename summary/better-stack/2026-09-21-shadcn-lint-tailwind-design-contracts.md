---
title: shadcn/lint and Agent-First Tailwind Design Contracts
author: Better Stack
channel: Better Stack
url: https://youtu.be/tPQgw_DPIoM?is=GWUSYRpr-5Z5jIYn
date: 2026-09-21 15:00
tags: ai, development
---

# shadcn/lint and Agent-First Tailwind Design Contracts

[article](../../articles/better-stack/2026-09-21-shadcn-lint-tailwind-design-contracts.md)

## What it addresses

Tailwind accepts valid classes that may still violate a product's design system.
Humans or agents can add `p-4`, `bg-pink-500`, or `p-[13px]` to a component.
TypeScript usually sees only a string, while Markdown guidance cannot fail CI.
`@shadcn/lint` turns selected constraints into checks and repair guidance.[1][2]

## Contracts and rules

A `no-restyle` contract matches component names by regex and defines `allow` or `deny`.
With `allow: ["layout"]`, margin, width, flex, and visibility pass; appearance does not.
Per-component contracts can allow typography on `CardTitle` or spacing on `CardContent`.
The six rules are `no-restyle`, `no-raw-colors`, and `no-arbitrary-values`;
they also include `no-inline-styles`, `no-unknown-classes`, and
`require-static-classes` for unreadable values such as `` `bg-${color}` ``.
Rules run at `warn` or `error`; most support exceptions, contracts, and messages.
`scanAllStrings` broadens color and arbitrary-value checks, with false-positive risk.

## Setup and agent workflow

It requires Tailwind v4 and Node.js 20.19+, plus ESLint 9.30+ or Oxlint 1.80+.[2]
Install with `npm install -D @shadcn/lint eslint @typescript-eslint/parser`, or
use `npm install -D @shadcn/lint oxlint`; then register the `shadcn` plugin.
Run `npx eslint .` or `npx oxlint`, expose it as `npm run lint`, and call it from CI.
Tell agents in `AGENTS.md` to run lint after edits and fix every error.
Vue needs `vue-eslint-parser`; Svelte needs `svelte-eslint-parser` for ESLint.
Oxlint sees `.vue` and `.svelte` script blocks, not templates; Biome has no plugin yet.
Diagnostics can list actual `cva` or `tv` sizes, variants, tokens, and source files.
Custom placeholders and a global `settings.shadcn.note` can link team guidance.

## Limits, evidence, and adoption

The linter sees static class sites, known helpers, one-hop values, themes, and SVG colors.
It cannot police plain CSS or `@apply`, trace arbitrary data flow, or judge visual taste.
A new token or variant can pass while remaining redundant, inaccessible, or off-brand.
Better Stack reports zero post-lint violations in its shown model runs.[1]
Official evals report over 150 bounded runs, usually converging in one correction round.[3]
Those tests support explicit constraint enforcement, not universal design quality.
Start `no-restyle` at `warn`, baseline legacy findings, then promote clean rules to errors.
Review tokens, variants, contracts, suppressions, and rendered UI as design decisions.
The supplied English transcript uses automatic captions, so code-like text may be wrong.

## Sources
[1] https://youtu.be/tPQgw_DPIoM?is=GWUSYRpr-5Z5jIYn
[2] https://github.com/shadcn-ui/lint
[3] https://github.com/shadcn-ui/lint/blob/main/docs/evals.md
