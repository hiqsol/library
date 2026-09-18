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
- For videos: use the featured person (interviewee/guest)
- No featured person → fall back to channel name

## Front matter

```yaml
---
title: Full title
author: Author Name
channel: Channel or blog name
url: https://...
date: YYYY-MM-DD HH:MM
tags: tag1, tag2
---
```

- `title` — quote if it contains a colon: `title: "Foo: Bar"`
- `channel` is always required — use the blog name for blog posts.
- `date` — original publication date+time; `00:00` if time unknown
- `tags` — controlled vocabulary (lowercase), pick all that apply:
  `ai`, `politics`, `war`, `ukraine`, `development`, `startups`, `health`
  If no existing tag fits, propose a new one to the user before adding it.

## Workflow

1. User gives a URL
2. **DEDUP CHECK**: grep index.md for the URL (or video ID). If found → STOP,
   tell user "Already processed: [title](article-link)" and do nothing else.
3. Download transcript or original content → `raw/<author>/<YYYY-MM-DD>-<slug>.<ext>`
4. Write article → `articles/<author>/<YYYY-MM-DD>-<slug>.md`
5. Write summary → `summary/<author>/<YYYY-MM-DD>-<slug>.md`
6. Update `index.md`
7. Commit and push

## Index format

```
- 2026-03-21 12:25 - ThePrimeagen - 2026-03-19 00:00
  "We're So Back": AI Solved Mitchell's 6-Month Ghosty Bug
  tags: ai, development
  [article](...) | [summary](...) | [source](...)
```

## Rules

- Articles and summaries: always English
- Same slug across raw/, articles/, summary/: lowercase, dashes, max 10 words
- File/dir names: only dashes, English letters, digits
- Videos: raw content is text transcript
- Web articles: don't change text, just format as markdown
- Markdown line length: hard limit 100 chars
- Summaries: preserve concrete numbers, insights, and key arguments
- Raw files: never modify after download
- Index entries: newest first, ordered by added time
- Index timestamps: run `date '+%Y-%m-%d %H:%M'` — never guess
- All timestamps: system timezone
- Clean up temp/intermediate files before committing
