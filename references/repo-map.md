# Repository Mapping for Moodle Exports

## Preferred Tutor-Ready Structure

When available, use:

- `<target-summary-folder>/syllabus.md`
- `<target-summary-folder>/00_topic_index.md`
- `<target-summary-folder>/<topic>.md`
- `<target-summary-folder>/README.md` (tutor operating rules)

If `<target-summary-folder>` is not provided, ask:
"What should the target summary folder be named? Suggested: `<course>-ai-tutor`."

## If Tutor-Ready Files Are Missing

Discover from raw export:

- Course meta files (e.g., `Infos.txt`, welcome PDFs, course homepage export)
- Topic folders (often under `Topics/` or similarly named directories)
- Slides/docs (`.pdf`, `.docx`, `.pptx`, `.txt`, `.html`, `.imscc`, code snippets)
- Media folders (images/videos/h5p)

Then build:
1. `syllabus.md`
2. `00_topic_index.md`
3. topic summaries in `<target-summary-folder>/`

## Generic Source Mapping

- Syllabus source: any official program overview/fact sheet/user-provided metadata
- Topic list source: folder structure + index file you generate
- Materials source: each topic summary frontmatter (`source_files`, `source_file_details`)
- Exercises source: explicit exercise files/sections or generated applied check questions

## Missing-Info Escalation

If critical items are absent, ask user for:
1. official course name
2. preferred syllabus source or minimum fields
3. target topic folder
4. target summary folder name (suggest `<course>-ai-tutor`)
5. whether exercises should be generated when missing
