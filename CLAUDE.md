# Agent instructions

Personal knowledge library from video transcripts and web articles.

## This file

- Agent-only instructions. Keep under 100 lines total.
- Every line must prevent an observed mistake — delete everything else.
- When told "update CLAUDE.md" — add only the minimal rule, not a paragraph.

## Workflow

1. User gives a URL
2. Download content into `raw/<YYYY-MM-DD>-<slug>.txt`
3. Refactor into `articles/<YYYY-MM-DD>-<slug>.md` — fix names, filler, structure
4. Generate `summary/<YYYY-MM-DD>-<slug>.md` — 30-50 lines, preserve data points
5. Update `index.md`

## Rules

- Filenames: `YYYY-MM-DD-slug` — original publication date prefix + kebab-case slug.
- Markdown line length: hard limit 100 chars.
- Summaries preserve concrete numbers, names, and key arguments.
- Raw files kept as-is — never modify them after download.
- Use `date '+%Y-%m-%d %H:%M'` for index timestamps — never guess.
