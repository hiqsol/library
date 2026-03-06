# Articles Library

A personal knowledge library built from video transcripts and web articles.
Given a source URL, Claude Code downloads the content, refactors it into
well-structured markdown, and generates a concise summary.

## Structure

```
raw/          — original transcripts and texts
articles/     — refactored markdown articles
summary/      — condensed summaries
index.md      — auto-generated catalog with links and one-line descriptions
```

## Workflow (all done interactively via Claude Code)

1. User gives a YouTube or article URL
2. Download transcript/content into `raw/<slug>.txt`
3. Refactor into clean markdown in `articles/<slug>.md`:
   fix names, remove filler, add structure (headings, lists, tables, quotes)
4. Generate summary in `summary/<slug>.md`:
   30-50 lines, preserve data points and actionable takeaways
5. Update `index.md`

## Conventions

- Filenames: kebab-case slugs derived from content title
- Markdown line length: hard limit 100 chars, prefer 80-99
- Summaries preserve concrete numbers, names, and key arguments
- Refactoring fixes: misspelled proper nouns, verbal artifacts, run-on
  paragraphs, missing structure
- Raw files kept as-is for reference
