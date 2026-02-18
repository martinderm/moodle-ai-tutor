# moodle-ai-tutor

`moodle-ai-tutor` is a Codex skill for tutoring from Moodle course exports and maintaining tutor-ready course knowledge files.

## Scope

Use this skill when the input is a Moodle course export and you need to:

- Teach learners directly from course materials.
- Build or update a tutor-ready knowledge base.
- Create or refresh `syllabus.md`, `00_topic_index.md`, and per-topic summaries.
- Map learner questions to source lectures/slides/media with citations.
- Recover missing course metadata through targeted user questions.

## Input

Expected input is an exported Moodle course folder (or equivalent course package), including any available:

- Topic folders.
- Slides/docs/text files (for example `.pdf`, `.txt`, `.html`, `.imscc`).
- Course metadata files (course overview, syllabus, intro docs).
- Optional exercise files and media folders.

## Operating Modes

### 1) Tutor Mode

Learner-facing teaching mode with strict response behavior:

- Start by asking: `Before we start: what is your professional context (domain, role, goals, and current level)?`
- Keep each teaching chunk at or below 150 words.
- Prefix lecture-grounded facts with `Info:`.
- Cite sources inline as:
  - `[source: <filename>, p.<page>]`
  - `[source: <filename>, p.n/a]`
- End each chunk with: `Are you ready to continue?`
- Use predefined exercises when present; otherwise generate short applied check questions.

### 2) Content Maintenance Mode

Knowledge-base build/update mode:

- Discovers existing structure or creates missing tutor files.
- Produces/updates:
  - `<target-summary-folder>/syllabus.md`
  - `<target-summary-folder>/00_topic_index.md`
  - `<target-summary-folder>/<topic>.md` (one summary per topic)
  - `<target-summary-folder>/README.md` (tutor response rules)
- Keeps one consistent frontmatter schema across topic files.
- Includes section-level citations and practical explanations (not headline-only notes).
- References media paths where relevant (without image/video interpretation unless requested).

## Required Workflow Checks

Before running Content Maintenance Mode:

1. `python --version`
2. `pdftotext -v`
3. Optional: `pdfinfo -v`
4. Optional (skill tooling only): `python -c "import yaml; print('ok')"`

If Python or `pdftotext` is missing, request user approval before installation.

## Missing-Info Protocol

Ask only for missing essentials:

1. Official course title.
2. Syllabus source (file or metadata).
3. Topic/material folder locations.
4. Target summary folder name (suggest `<course>-ai-tutor`).
5. Whether to generate exercises when none exist.

## Guardrails

- Stay within course tutoring and course-material maintenance scope.
- Prefer repository/course evidence first.
- Label non-course general knowledge clearly when used.
- If evidence is insufficient, state the limitation and ask focused follow-ups.

## References

Behavioral and maintenance rules are defined in:

- `SKILL.md`
- `references/repo-map.md`
- `references/tutor-response-contract.md`
- `references/maintenance-checklist.md`
