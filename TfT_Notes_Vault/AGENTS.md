# Agent Rules

This file is the canonical source for agent rules in this vault. `CLAUDE.md` symlinks here — if you are reading this as `CLAUDE.md`, you are in the right place.

## Completion Checklist

You MUST complete these steps before finishing any task that modifies shared documentation, workflow, folder paths, naming conventions, or config. Do not skip these. Do not mark the task as done until both steps pass.

1. Update all affected shared docs: [[THESIS_CONTEXT]], notes in [[ai/README]], and relevant workflow notes in [[Literature Review/README]].
2. Run `python3 ai/scripts/validate_ai_docs.py` and confirm it passes.

## Rules

- Do NOT fabricate claims, sources, or citations. Accuracy and proper attribution are non-negotiable.
- Keep the user in the thinker role. When in doubt, ask questions rather than producing conclusions. Do not replace the user's judgment with unsupported recommendations.
- Respect the existing vault structure and naming conventions. If unsure, ask before reorganizing.
- Use Obsidian wikilinks for all internal vault references.
- Update canonical notes rather than duplicating content across files.
- Treat substantive argument text in `Literature Review/Synthesis/` as user-owned. Do not rewrite `Current Argument`, `Working Thoughts`, or `Synthesized Position` there unless the user explicitly asks; bottom tracking lists and reading-stub cleanup are okay when requested.

## Project Context

This vault is the research workspace for a bachelor thesis at KIT titled **"Strategies for Thoughtful Cognition."** It investigates how GenAI can be designed and used as a Tool for Thought (TfT) — protecting and augmenting human cognition rather than replacing it. The core concern is cognitive offloading: users deferring thinking to AI and unreflectively relying on its outputs.

Deliverables: (1) Systematic Literature Review, (2) Strategy Taxonomy (Design Strategies vs. Usage Strategies), (3) Conceptual Framework (AI Role → Strategy → Cognitive Function), (4) Prototypical Validation (lives outside this vault).

This vault covers deliverables 1–3: literature collection, strategy extraction, taxonomy and framework development, and thesis writing. The prototype is developed separately.

For the full project context, literature workflow details, and current reading orientation, read [[THESIS_CONTEXT]].

For Zotero import setup and template conventions:

- [[ai/zotero-import-template-guide]]

For active literature-review work:

- [[Literature Review/README]]

For paper synthesis integration (the "generate synthesis additions" workflow):

- [[ai/synthesis-integration-workflow]]

## Zotero Import Conventions

- Main paper notes import into `Literature Review/imports/`.
- Raw Zotero notes and their assets live in `Literature Review/zotero_notes/`.
- Imported filenames MUST be citekey-based, not title-based.

See [[ai/zotero-import-template-guide]] for the full setup.
