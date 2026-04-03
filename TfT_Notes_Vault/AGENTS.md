# Agent Entry Point

This vault uses `CLAUDE.md` as the fuller canonical context note.

If you are an AI agent working in this vault:

1. Read `CLAUDE.md` first.
2. If the task touches Zotero imports, note templates, or literature workflow setup, also read:
   - `ai/zotero-import-template-guide.md`
3. For active literature-note work, inspect the relevant notes inside:
   - `Literature Review/`

Important operational rules:

- This is a research vault for a bachelor thesis on GenAI as a Tool for Thought.
- Accuracy and attribution matter.
- Do not fabricate claims or sources.
- Keep the user in the thinker role; avoid replacing their judgment with unsupported conclusions.
- Respect existing vault structure and naming conventions.
- Use Obsidian wikilinks for internal note/file references inside the vault so links survive renames.
- Keep shared AI documentation up to date when something changes that should survive across chat contexts.
  - This includes workflow changes, folder/path changes, command/config changes, naming conventions, and major project-phase changes.
  - Relevant files usually include `CLAUDE.md`, files in `ai/`, and any workflow note those files point to.
- If you changed shared workflow, config, or AI documentation, the task is not done until you run:
  - `python3 scripts/validate_ai_docs.py`
- For Zotero imports:
  - main notes live in `Literature Review/imports/`
  - raw Zotero notes live in `Literature Review/zotero_notes/`
  - imported filenames should stay citekey-based

This file is the canonical place for general agent conventions in the vault. Avoid copying the same rule set into multiple notes unless a shorter pointer is enough.
