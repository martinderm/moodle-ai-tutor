# Maintenance Checklist (Any Moodle Export)

## Environment Preflight

Run before content generation:

1. Check Python: `python --version`
2. Check PDF text extraction tool: `pdftotext -v` (Poppler or equivalent)
3. Optional check: `pdfinfo -v` (better PDF page/metadata handling)
4. Optional check: PyYAML with `python -c "import yaml; print('ok')"` (needed for skill-creator script operations only)

If Python or `pdftotext` is missing, ask user for install approval before proceeding.
If optional dependencies are missing, ask user whether to install with a brief impact note.

## Input Discovery

1. Confirm course name.
2. Confirm syllabus source (file or user-provided metadata).
3. Confirm topic folder(s) to summarize.
4. Confirm target summary folder name (suggest `<course>-ai-tutor`).
5. Confirm whether to generate exercises when missing.

Ask user for only missing items.

## When Updating Topic Summaries

1. Preserve one frontmatter schema across all topic files.
2. Use text sources only (`.pdf`, `.txt`, `.html`, `.imscc`, `.xxx`) unless user requests otherwise.
3. Skip image/video interpretation.
4. Keep `related_media` references when media exists.
5. Avoid headline-only output:
   - include concept, purpose, mechanism/workflow, practical relevance, constraints/trade-offs.
6. Keep citations at section level.

## When Updating Syllabus

1. Merge official document facts with user-provided program details.
2. Keep absolute dates for cohort-specific schedule entries.
3. Mark date-bound schedule items as cohort-specific when needed.
4. Keep citations for all factual statements.

## Validation Before Finish

1. Verify every updated markdown file has valid frontmatter.
2. Verify major sections have at least one citation.
3. Verify tutor constraints remain explicit:
   - context-first question
   - <=150-word chunks
   - `Info:` facts
   - `Are you ready to continue?`
4. Verify all generated files are written to the chosen target summary folder.
