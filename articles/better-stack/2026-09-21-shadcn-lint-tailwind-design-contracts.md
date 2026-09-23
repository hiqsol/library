---
title: shadcn/lint and Agent-First Tailwind Design Contracts
author: Better Stack
channel: Better Stack
url: https://youtu.be/tPQgw_DPIoM?is=GWUSYRpr-5Z5jIYn
date: 2026-09-21 15:00
tags: ai, development
---

# shadcn/lint and Agent-First Tailwind Design Contracts

## The narrower thesis behind the headline

Better Stack presents `@shadcn/lint` as a fix for Tailwind's “biggest problem.”[1]
The demonstrated claim is narrower: the linter can turn selected design-system
constraints into executable checks and give coding agents local repair guidance.
It does not solve every Tailwind problem, prove that design systems are Tailwind's
single greatest weakness, or certify that a passing interface is well designed.

The project targets Tailwind CSS v4 and does not require `shadcn/ui`. Its official
repository documents React, Vue, and Svelte support through ESLint or Oxlint.[2]
At the time covered by the video, there is no Biome plugin. Teams standardized on
Biome must add ESLint or Oxlint for these checks, or wait for that integration.

## Why restyling creates drift

A Tailwind class list is usually just a string to TypeScript. A caller can therefore
put `p-4` on a `Button` that should own its padding, add `bg-pink-500` beside a
semantic theme color, or use `p-[13px]` between approved spacing steps. The code may
compile and Tailwind may generate valid CSS, even though the component contract has
been violated.

Humans do this under delivery pressure; coding agents do it when a prompt requests a
specific visual result. “Make it pop,” “use pill corners,” or “match 13px exactly”
invites a locally plausible class that bypasses the shared vocabulary. A Markdown
style guide can describe the policy, but it cannot fail CI. Loading a long guide into
every agent context also consumes tokens without proving that the final edit complies.

The problem is not utility classes themselves. It is the gap between what Tailwind
can express and what a particular product permits. `@shadcn/lint` narrows that gap by
making permitted changes machine-checkable.

## Contracts: component APIs beyond TypeScript

The central mechanism is a component contract: a policy selected by a regular
expression over the resolved component name. A top-level rule can establish a
default, while contracts specialize components or component parts.

```js
"shadcn/no-restyle": ["error", {
  allow: ["layout"],
  contracts: [
    {
      pattern: "^CardTitle$",
      allow: ["layout", "typography"],
      deny: ["font-*"],
    },
    {
      pattern: "^CardContent$",
      allow: ["layout", "spacing"],
    },
  ],
}]
```

This policy lets a page place either component. It also lets `CardTitle` change text
size without changing font family or weight, and lets `CardContent` change padding
without changing typography. Thus `text-lg` on `CardTitle` and `p-6` on
`CardContent` pass, while `font-bold` on the title is reported.

A contract replaces the keys it writes and inherits other keys from the top level.
If several patterns match, only the last matching contract applies; contracts do not
merge with one another. Anchors matter: `^Button$` matches only `Button`, whereas
`Button` can also match `IconButton`.

Policy entries may be categories such as `layout`, class groups such as `p`, exact
classes such as `p-4`, or wildcard patterns such as `mt-*`. `deny` removes matches
from `allow`. With `deny` but no `allow`, everything except the denied matches is
exempt, so that mode should be chosen deliberately.

Contracts are not equivalent to CSS semantics. `w-*` does not cover every class or
arbitrary property that produces `width`. Each lint rule also has its own policy:
allowing padding through `no-restyle` does not exempt `p-[13px]` from
`no-arbitrary-values`.

## Install and wire it into the workflow

The documented baseline is Node.js 20.19 or later, Tailwind CSS v4, and either
ESLint 9.30 or later or Oxlint 1.80 or later.[2] A strict component API with named
variants is not required to run the plugin, but it makes repair suggestions useful.
A component that accepts any class and defines no variants gives the linter little to
recommend.

For a React project using ESLint:

```bash
npm install -D @shadcn/lint eslint @typescript-eslint/parser
```

Register the plugin in `eslint.config.mjs`, preserving an existing parser setup:

```js
import { plugin as shadcn } from "@shadcn/lint"
import tsParser from "@typescript-eslint/parser"
import { defineConfig } from "eslint/config"

export default defineConfig([
  {
    files: ["**/*.{js,jsx,ts,tsx}"],
    languageOptions: {
      parser: tsParser,
      parserOptions: { ecmaFeatures: { jsx: true } },
    },
    plugins: { shadcn },
    rules: {
      "shadcn/no-restyle": ["error", { allow: ["layout"] }],
    },
  },
  {
    files: ["components/ui/**"],
    rules: {
      "shadcn/no-restyle": "off",
      "shadcn/no-arbitrary-values": "off",
      "shadcn/require-static-classes": "off",
    },
  },
])
```

Run it with:

```bash
npx eslint .
```

For Oxlint:

```bash
npm install -D @shadcn/lint oxlint
```

Create or extend `.oxlintrc.json`:

```json
{
  "jsPlugins": ["@shadcn/lint"],
  "rules": {
    "shadcn/no-restyle": ["error", { "allow": ["layout"] }]
  }
}
```

Then run:

```bash
npx oxlint
```

Add the chosen command to the `lint` script in `package.json`, run it in CI, and put
an explicit loop in `AGENTS.md`:

```md
After making changes, run `npm run lint` and fix all errors.
```

For Vue, ESLint also needs `vue-eslint-parser`; for Svelte, it needs
`svelte-eslint-parser`. Oxlint reads the `<script>` blocks of `.vue` and `.svelte`
files, not their templates, so ESLint is needed for template coverage. This is an
important reason not to treat “Oxlint support” as identical across frameworks.

A setup agent should detect the package manager, workspace boundaries, component
folders, import aliases, themes, and the linter already responsible for UI files.
Installing the plugin without enabling a rule verifies configuration only; it creates
no design-system enforcement.

## The six rules and their operating modes

Each rule can run at `warn` or `error`. Most accept `allow`, `deny`, `contracts`, and
`message`; `require-static-classes` accepts no policy exceptions because it checks
readability rather than style. `no-inline-styles` uses CSS property names and has no
component-recognition options. The other rules can recognize custom imports, merge
functions, and variant functions.

### `shadcn/no-restyle`

This rule checks classes passed to recognized design-system components. The video's
featured mode is:

```js
"shadcn/no-restyle": ["error", { allow: ["layout"] }]
```

That allows placement and layout such as margin, width, `flex-1`, `hidden`, and
positioning. It reports component restyling in color, typography, spacing, shape,
effects, motion, and unclassified classes. Padding and gap count as spacing; margin,
transforms, and text alignment count as layout.

The rule should normally be off inside the component implementation directory, where
components define their own appearance. It can follow imports, re-exports, selected
wrappers that forward `className`, known helpers such as `cn`, and same-file values.
It reads `cva` or `tv` variants and can suggest the component's actual sizes or
variants. A custom class that the grammar cannot classify is reported unless allowed
by name; the rule does not inspect that class's CSS effect.

### `shadcn/no-raw-colors`

This reports raw palette classes such as `bg-pink-500`, undeclared semantic color
names, and literal SVG colors in `fill`, `stroke`, `color`, `stopColor`,
`floodColor`, and `lightingColor`. Theme tokens such as `bg-primary` pass. For SVG,
its guidance can recommend `currentColor` plus a text color class.

It can suggest nearby theme colors or spelling corrections based on the readable
Tailwind theme. With `scanAllStrings: true`, it checks every string literal rather
than only recognized class sites; that increases coverage and false-positive risk.
Variable shorthand such as `bg-(--brand)` passes without proving the variable exists.
Keep this rule enabled inside component implementations.

### `shadcn/no-arbitrary-values`

This reports values such as `p-[13px]`, `rounded-[10px]`, and `bg-[#333]`. When it
can, it suggests an equivalent scale step or nearby token. The video shows `p-3.25`
as the on-scale equivalent for 13px under a 4px spacing unit, and `rounded-lg` when
the project's radius token equals 10px.

The practical modes differ. A bare `"error"` also checks arbitrary layout values;
`["error", { allow: ["layout"] }]` permits arbitrary widths and margins while
checking appearance. `scanAllStrings: true` broadens scanning. Exact spacing
replacements require supported units and scale math, while unsupported shadows or
values receive general guidance. This rule is often disabled in component internals,
where structural arbitrary values such as `ring-[3px]` may be intentional.

### `shadcn/no-inline-styles`

This reports ordinary inline CSS properties, hardcoded colors in custom properties,
unreadable style objects, and JSX `<style>` elements. Dynamic values may flow through
CSS custom properties when a class consumes them, but a hardcoded color such as
`"--label-color": "#ec4899"` is still reported.

Its `allow` and `deny` entries are CSS properties, not Tailwind classes. A narrow
exception can permit `transform` for an animation component. Imported or otherwise
unreadable style objects are reported rather than inspected, while forwarding a
received `style` prop is allowed. Keep the rule enabled inside component code.

### `shadcn/no-unknown-classes`

This asks the installed Tailwind v4 setup whether a class can generate CSS. It catches
names such as `rounded-huge`, `flex-cols`, or `hovr:flex` and can suggest corrections.
It understands theme utilities, custom utilities, variants, plugins, and plain class
selectors in the theme's import graph.

Start this rule at `warn`, because classes from external stylesheets may need explicit
exceptions. If the theme cannot load, the fallback grammar checks less and emits no
spelling suggestions; a clean fallback run is weaker evidence than a clean run with a
resolved theme. A valid class may still be invalid for a component, which remains
`no-restyle`'s job.

### `shadcn/require-static-classes`

This rule reports class expressions that the other rules cannot read, such as:

```tsx
<Button className={`bg-${color}`}>Save changes</Button>
```

Conditional choices between complete strings are acceptable, as are known helper
calls and same-file constants resolved one hop. Imported values and unknown function
calls are not. The repair is to enumerate complete static classes or use an explicit
variant map so the linter and Tailwind can see the vocabulary.

Turn the rule off inside component implementations because calls to component-owned
variant factories may not be resolvable at the call site. Unlike the other five
rules, it has no `allow`, `deny`, or `contracts` mode.

## Diagnostics as an agent interface

A useful diagnostic does more than reject `p-4`. It can say that `Button` owns its
spacing, list `sm` and `lg` sizes read from the component's `cva` setup, suggest
margin or a parent gap for outside spacing, and name the component file to edit only
when the design explicitly needs a new size.

Messages may include `{{className}}`, `{{property}}`, `{{component}}`,
`{{suggestions}}`, and `{{file}}`. `no-restyle` also exposes `{{category}}`,
`{{variants}}`, `{{wrapper}}`, `{{sizes}}`, `{{around}}`, and `{{entries}}`.
Fallback syntax such as `{{sizes|none defined}}` avoids empty advice.

```js
"shadcn/no-restyle": ["error", {
  allow: ["layout"],
  message: {
    spacing: "Use a {{component}} size: {{sizes|none defined}}.",
    default: "Use a {{component}} variant: {{variants|none defined}}.",
  },
}]
```

A global note can point every finding to team guidance:

```js
settings: {
  shadcn: {
    note: "See DESIGN.md for rules and approved exceptions.",
  },
}
```

This structure gives an agent a short, local feedback loop: edit, run lint, read the
specific allowed vocabulary, repair, and rerun. Better Stack argues that this can
reduce prompt context and token usage because the agent need not repeatedly load the
whole design guide.[1] That is plausible for this workflow, but it depends on agents
actually running lint and on the messages being accurate and actionable.

## Discovery and customization

A `shadcn/ui` project can discover components and themes from `components.json`.
Custom systems can use shared `settings.shadcn` values:

```json
{
  "settings": {
    "shadcn": {
      "ui": "@/ds",
      "componentImports": ["^@acme/ui(/|$)"],
      "ignoreImports": ["^@acme/ui/internal(/|$)"],
      "mergeFunctions": ["customMerge"],
      "variantFunctions": ["variants"],
      "note": "See DESIGN.md for design rules and approved exceptions."
    }
  }
}
```

Built-in class helpers include `cn`, `cx`, `clsx`, `cva`, `tv`, `twMerge`,
`twJoin`, and `classNames`; built-in variant functions are `cva` and `tv`. Custom
helper registration tells the linter where strings live; it does not execute a helper
or prove that the helper's output matches its arguments.

Teams can share rule policy in `design-system.lint.json`, load it from Oxlint with
`extends`, and import it into ESLint. Monorepos should point `ui` or
`componentImports` at shared component packages and scope discovery per application,
because each app may have a different theme.

## What static analysis can and cannot see

The linter sees many static class sites: literal class strings, arrays and objects in
known helper shapes, same-file values resolved one hop, component imports and some
wrappers, Tailwind theme data, `cva` or `tv` variants, and literal SVG color
attributes. This is enough to make common violations executable rather than advisory.

Its boundary is equally important:

- Plain CSS is outside these JavaScript rules. A raw color in `globals.css`, an
  `@apply`, or a Vue or Svelte `<style>` block needs a CSS linter.
- Analysis generally follows values one hop within a file, not arbitrary imported
  data or selectors flowing from a parent to a descendant.
- Dynamic class construction hides the final class unless
  `require-static-classes` rejects it.
- A newly declared theme token is “on system” by definition. The linter cannot decide
  whether a new orange belongs in the product palette.
- A newly added component variant can satisfy the contract while still being ugly,
  inaccessible, redundant, or inconsistent with product intent.
- Color proximity is guidance based on resolved values, not semantic design proof.
- Dynamic SVG expressions and some framework-specific template or style areas remain
  outside the relevant rule.
- A bounded red-team exercise found raw CSS and newly minted theme tokens escaped;
  it was not proof that no other bypass exists.[3]

Review therefore moves rather than disappears. Humans should focus on changes to
tokens, variants, contracts, settings, suppression comments, and the rendered result,
instead of rediscovering every ordinary class violation by eye.

## What the evals support

Better Stack summarizes an eight-task demonstration in which models produced many
violations before lint feedback and zero afterward.[1] The repository reports more
than 150 task runs and says almost every task reached zero violations in one correction
round.[2] Its README also presents one eight-task run per model, including Sonnet 5,
Haiku 4.5, Opus 5, GPT 5.6 Terra, and GPT 5.6 Sol; Sol completed six of eight tasks.

The detailed eval suite pairs a fresh generation with a fresh correction agent. The
corrector receives the task, rule descriptions, and diagnostics for up to three
rounds. A rules-only control receives the same rule text but no diagnostics. Temptation
tasks request off-system styling, while neutral tasks contain no styling language.
Playwright renders before and after versions, and a judge model scores fidelity over
three passes with the median reported.[3]

The documented results support three useful observations: diagnostics usually drove
violations to zero quickly; fixes often became component variants or existing tokens;
and Claude correction runs with diagnostics cost 10% to 48% less than rules-only
controls. Neutral tasks also showed agents restyling components without explicit
visual temptation.[3]

They do not establish a universal guarantee. The detailed runs emphasize three Claude
models, use a judge from the same model family, give the corrected condition extra
turns, and cover small fixtures and bounded tasks. Rules and prompts changed between
runs. Corrections add work, and first drafts did not become cleaner. Two visually
unjudgeable cases rendered empty on both sides. A passing lint result was evaluated
separately from visual fidelity and still did not approve a design.[3]

The headline should therefore be read as promotional compression. The evidence shows
that explicit, statically visible constraints can be enforced and repaired reliably
in the tested workflow. It does not prove that `@shadcn/lint` fixes Tailwind's broadest
problems, outperforms alternatives such as StyleX in every architecture, or guarantees
quality, accessibility, usability, or taste.

## A practical adoption path

1. Confirm Tailwind v4, Node.js, framework parser, and linter compatibility.
2. Register `@shadcn/lint` without replacing existing parser or rule configuration.
3. Start `no-restyle` at `warn` with `allow: ["layout"]`.
4. Exclude component internals where the rule would reject their owned appearance.
5. Fix repeated patterns first, then define variants and component contracts.
6. Add token, arbitrary-value, inline-style, and static-class rules one at a time.
7. Introduce `no-unknown-classes` at `warn` and document external CSS exceptions.
8. Promote clean rules to `error`, add `npm run lint` to CI and `AGENTS.md`, and
   review new tokens, variants, contracts, suppressions, and rendered output.

A legacy codebase can cap its current warnings with `--max-warnings`, lower the cap as
findings are fixed, and enforce `error` only in new-code folders. Intentional
exceptions should be narrow and carry a reason. This avoids turning adoption into a
large rewrite while still preventing drift from increasing.

The tradeoff is policy maintenance. Contracts must reflect real component ownership,
helpers and imports need discovery settings, and false positives require careful
exceptions. Overly strict rules may push agents toward unnecessary variants; overly
broad allowances merely document drift. The payoff is deterministic feedback and a
review surface centered on design decisions rather than raw class-string policing.

## Sources and transcript note

This article combines Better Stack's video with the project's official documentation
and eval report. The supplied transcript is an English automatic-caption transcript;
it may mishear package names, class names, punctuation, and code. Concrete identifiers
and commands above were cross-checked against the repository where available.

- [1] Better Stack, “Shadcn Just Fixed Tailwind's Biggest Problem”:
  https://youtu.be/tPQgw_DPIoM?is=GWUSYRpr-5Z5jIYn
- [2] `shadcn-ui/lint` repository and README:
  https://github.com/shadcn-ui/lint
- [3] `@shadcn/lint` eval methodology and results:
  https://github.com/shadcn-ui/lint/blob/main/docs/evals.md
