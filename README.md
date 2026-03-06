# Articles Library

A personal knowledge library built from different sources. Given a URL
or other request, Claude Code downloads the content, refactors it into
well-structured markdown, and generates a summary.

## Structure

```
raw/<author>/      — original transcripts and texts
articles/<author>/ — refactored markdown articles
summary/<author>/  — condensed summaries
index.md           — catalog: date/time, title, links
```

## Workflow (via Claude Code)

1. User provides a source (URL, YouTube link, or other)
2. Download content into `raw/<author>/<slug>.<ext>` (transcript
   for videos)
3. Refactor into `articles/<author>/<slug>.md`: fix names, remove
   filler, add structure (headings, lists, tables, quotes), keep all
   original thoughts. If the source is already a formatted article,
   convert to markdown as-is without refactoring
4. Generate `summary/<author>/<slug>.md`: 30–50 lines, preserve
   data points, insights, and actionable takeaways
5. Update `index.md`: added date/time, author, original
   publication date/time, title, links to article/summary/source;
   newest first

## Conventions

- Files organized by author: `<author>/<slug>.<ext>`
- Author dirs and filenames: kebab-case slugs
- Markdown line length: hard limit 100 chars, prefer 80–99
- Summaries preserve concrete numbers, names, and key arguments
- Refactoring fixes: misspelled proper nouns, verbal artifacts,
  run-on paragraphs, missing structure
- Raw files kept as-is for reference
- Original publication date/time tracked in index (after author),
  article metadata, and summary metadata
