# Record Reading Notes Skill Discussion Checklist

## Intent Anchor

- Create a repository-local skill for recording reading notes under `reading-notes/`.
- Require confirmation of the exact content before any note file is written.
- Follow the repository's existing reading note convention.

## Questions

- id: q1
  question: Where should the skill live?
  depends_on: []
  status: answered
  answer: The user asked to add it to the current repository; use `.codex/skills/record-reading-notes/`.
  design_trace: Skill location

- id: q2
  question: What should the skill do before writing notes?
  depends_on: []
  status: answered
  answer: Confirm the exact note content with the user and write only after approval.
  design_trace: Confirmation requirement

- id: q3
  question: Which note directory and file convention should it use?
  depends_on: []
  status: answered
  answer: Use `reading-notes/` and follow `reading-notes/README.md`, currently `reading-notes/YYYY-MM-DD.md`.
  design_trace: Note format

## Spec-Gap Closure

- external_io: answered - One bounded operation is one confirmed write to a reading note Markdown file.
- concurrency_retries: deferred - Not relevant for local note recording.
- single_knob_workers: deferred - Not relevant; no worker pool or concurrency setting.
- other_backends: deferred - Out of scope; this skill only writes repository Markdown files.
- ordering_fairness: answered - Preserve existing notes and append new document sections in the order they are recorded.
- backpressure: deferred - Not relevant for small local Markdown edits.
- acceptance: answered - Validate by reading back the changed section after writing.
- doc_precedence: answered - `reading-notes/README.md` wins for note format conventions.
