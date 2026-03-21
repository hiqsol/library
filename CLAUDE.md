# Library agent instructions

Personal knowledge library from video transcripts and web articles.

## This file

- Specifies desired result, not process — how is up to the agent.
- Keep under 100 lines.
- Every line must prevent an observed mistake.

## Structure

```
raw/<author>/<YYYY-MM-DD>-<slug>.<ext>   — original content
articles/<author>/<YYYY-MM-DD>-<slug>.md — article
summary/<author>/<YYYY-MM-DD>-<slug>.md  — 30-60 line summary
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
date: YYYY-MM-DD HH:MM
tags: [tag1, tag2]
---
```

- `channel` is always required — use the blog name for blog posts.
- `date` — original publication date and time; use `00:00` if exact time
  is unavailable
- `tags` — controlled vocabulary (lowercase), pick all that apply:
  `ai`, `politics`, `war`, `ukraine`, `development`, `startups`
  If no existing tag fits, propose a new one to the user before adding it.

## Workflow

1. User gives a URL
2. Download transcript or original content → `raw/<author>/<YYYY-MM-DD>-<slug>.<ext>`
3. Write article → `articles/<author>/<YYYY-MM-DD>-<slug>.md`
4. Write summary → `summary/<author>/<YYYY-MM-DD>-<slug>.md`
5. Update `index.md`
6. Commit, push, send GitHub article and commit links

## Index format

```
- 2026-03-21 13:30 - Andrej Karpathy - 2026-03-20 15:00
  Code Agents, AutoResearch, and the Loopy Era of AI
  tags: ai, development
  [article](...) | [summary](...) | [source](...)
```

## Rules

- All articles and summaries must be in English, regardless of source language
- Same slug across raw/, articles/, summary/ for a given entry
- Slug: derive from title — lowercase, dashes, drop articles (a/the), max 10 words
- Directory and file names must use only dashes, English letters and numbers
- For videos original content is text transcript
- If original content is article don't change text just format to markdown
- Markdown line length: hard limit 100 chars
- Summaries: preserve concrete numbers, insights, and key arguments
- Raw files: never modify after download
- Index entries: newest first, ordered by added time
- Index timestamps: run `date '+%Y-%m-%d %H:%M'` — never guess
- Use system timezone for all the dates
- Clean up temp/intermediate files before committing
