# Agent instructions

Personal knowledge library from video transcripts and web articles.

## This file

- Agent-only instructions. Keep under 100 lines total.
- Every line must prevent an observed mistake — delete everything else.
- When told "update CLAUDE.md" — add only the minimal rule, not a paragraph.

## Structure

All three directories use identical `<author>/<YYYY-MM-DD>-<slug>` layout:
- `raw/<author>/<slug>.txt` — downloaded transcript/content
- `articles/<author>/<slug>.md` — refactored article
- `summary/<author>/<slug>.md` — 30-50 line summary

Author dir is kebab-case full name (e.g. `nate-b-jones`, `margulan-seissembai`).
For videos: use the main featured person (interviewee, guest expert) as author, not the channel.
If no specific person is featured, fall back to the channel name (kebab-case).

## Workflow

1. User gives a URL
2. Download content into `raw/<author>/<YYYY-MM-DD>-<slug>.txt`
3. Refactor into `articles/<author>/<YYYY-MM-DD>-<slug>.md`
4. Generate `summary/<author>/<YYYY-MM-DD>-<slug>.md` — 30-50 lines
5. Update `index.md`

## Rules

- Filenames: `YYYY-MM-DD-slug` — original publication date prefix + kebab-case slug.
- Same slug across raw/, articles/, summary/ for a given entry.
- Markdown line length: hard limit 100 chars.
- Summaries preserve concrete numbers, names, and key arguments.
- Raw files kept as-is — never modify them after download.
- Use `date '+%Y-%m-%d %H:%M'` for index timestamps — never guess.
- Clean up temp files (`.vtt`) before committing.
