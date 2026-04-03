# Agent Entry Point

This file is the canonical source for general agent conventions in this vault.

## Read Order

If you are an AI agent working in this vault:

1. Read this file first.
2. Then read [[CLAUDE]] for fuller project context.
3. If the task touches Zotero imports, note templates, or literature workflow setup, also read [[ai/zotero-import-template-guide]].
4. For active literature-note work, inspect the relevant notes in [[Literature Review/README]] and [[ai/zotero-import-template-guide]].

## General Conventions

- Accuracy and attribution matter. Do not fabricate claims or sources.
- Keep the user in the thinker role. Avoid replacing their judgment with unsupported conclusions.
- Respect the existing vault structure and naming conventions.
- Use Obsidian wikilinks for internal vault references so links survive renames.
- Prefer updating canonical notes over duplicating the same rules in multiple places.

## Shared Documentation Rule

If you change anything that should survive across chat contexts, update the relevant shared documentation before finishing.

This includes:

- workflow changes
- folder or path changes
- command or config changes
- naming-convention changes
- major project-phase/context changes
- new reusable handoff notes in [[ai/README]]

Relevant files usually include:

- [[CLAUDE]]
- notes in [[ai/README]]
- the relevant workflow note in [[Literature Review/README]] or the relevant note in [[ai/README]]

## Validation

If you changed shared workflow, config, or AI documentation, the task is not done until you run:

- `python3 ai/scripts/validate_ai_docs.py`

## Zotero Import Conventions

- Main paper notes import into `Literature Review/imports/`.
- Raw Zotero notes and their assets live in `Literature Review/zotero_notes/`.
- Imported filenames should stay citekey-based.

See [[ai/zotero-import-template-guide]] for the detailed Zotero setup.
