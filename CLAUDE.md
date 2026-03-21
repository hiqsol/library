# Library agent instructions

Personal knowledge library from video transcripts and web articles.

## This file

Keep under 100 lines. Every line must prevent an observed mistake.

## Structure

```
raw/<author>/<YYYY-MM-DD>-<slug>.txt     — downloaded transcript
articles/<author>/<YYYY-MM-DD>-<slug>.md — refactored article
summary/<author>/<YYYY-MM-DD>-<slug>.md  — 30-50 line summary
```

- Author dir: kebab-case full name (e.g. `nate-b-jones`, `margulan-seissembai`)
- For videos: use the featured person (interviewee/guest), not the channel name
- No featured person → fall back to channel name (kebab-case)

## Front matter

Every article and summary opens with:

```yaml
---
title: "Full title"
author: Author Name
channel: Channel or blog name
url: https://...
date: YYYY-MM-DD
tags: [tag1, tag2]
---
```

`channel` is always required — use the blog name for blog posts.

Tags — controlled vocabulary, pick all that apply:
`ai`, `politics`, `war`, `ukraine`, `development`, `startups`

If no existing tag fits, propose a new one to the user before adding it.

## Workflow

1. User gives a URL
2. Download transcript → `raw/<author>/<YYYY-MM-DD>-<slug>.txt`
3. Write article → `articles/<author>/<YYYY-MM-DD>-<slug>.md`
4. Write summary → `summary/<author>/<YYYY-MM-DD>-<slug>.md`
5. Update `index.md`
6. Commit, push, send GitHub article and commit links

## Rules

- Same slug across raw/, articles/, summary/ for a given entry
- Markdown line length: hard limit 100 chars
- Summaries: preserve concrete numbers, names, and key arguments
- Raw files: never modify after download
- Index timestamps: run `date '+%Y-%m-%d %H:%M'` — never guess
- Clean up temp `.vtt` files before committing
