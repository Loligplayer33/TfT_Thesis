---
title: Zotero Import Template Guide
tags:
  - ai
  - zotero
  - obsidian
  - workflow
  - handoff
status: active
---

# Zotero Import Template Guide

Use this note in future AI chats when changing or extending the Zotero Integration setup for literature notes.

## Current Working Setup

- Plugin config file:
  - `TfT_Notes_Vault/.obsidian/plugins/obsidian-zotero-desktop-connector/data.json`
- Main note template:
  - `TfT_Notes_Vault/Literature Review/templates/overview-paper-template.md`
- Raw Zotero import template:
  - `TfT_Notes_Vault/Literature Review/templates/zotero-notes-template.md`
- Main import folder:
  - `TfT_Notes_Vault/Literature Review/imports/`
- Stable raw Zotero folder:
  - `TfT_Notes_Vault/Literature Review/zotero_notes/`

## Current Commands

- `Import overview paper`
  - creates the main thinking note for overview paper types
  - output path:
    - `Literature Review/imports/{{citekey}}.md`
  - important:
    - this command should not create its own separate asset folder
    - it shares the stable Zotero-notes asset folder to avoid stray top-level assets caused by the plugin fallback behavior

- `Import Zotero notes`
  - universal raw-material import
  - creates the companion note with Zotero item notes and PDF annotations
  - output path:
    - `Literature Review/zotero_notes/{{citekey}}-zotero-notes.md`
  - image output path:
    - `Literature Review/zotero_notes/{{citekey}}-zotero-notes-assets`

## Naming Rules

- Use `{{citekey}}` for imported filenames.
- Do not use `{{title}}` for filenames in this vault.
- Reason:
  - title-based filenames became too long for the OneDrive-backed vault and caused timeouts and broken reads.
- Keep the full paper title inside the note body, not in the path.

## Structure Rules

- Main note commands are paper-type-specific.
  - `Import overview paper` is specific to overview papers.
  - future commands for other paper types should also be type-specific

- `Import Zotero notes` is universal.
  - it should stay generic across paper types
  - it imports raw Zotero material, not thesis-specific thinking structure

- PDF annotation assets should only be exported by `Import Zotero notes`.
- In practice, the overview-paper command shares the Zotero-notes asset path because the plugin otherwise falls back to the vault base path and can create stray `image-*` files.
- Do not create a separate asset folder for the main paper-type commands unless there is a very explicit reason.

## Current Template Intent

### Main note

- Holds the thesis-facing thinking note.
- Links to the companion raw note using:
  - `Literature Review/zotero_notes/{{citekey}}-zotero-notes`
- Should stay focused on:
  - why the paper matters
  - key concepts
  - distinctions
  - tensions
  - relevance
  - next follow-up

### Raw Zotero note

- Holds imported raw source material.
- Current order:
  1. `Zotero`
  2. `PDF Annotations`
  3. `Zotero Item Notes`
- Horizontal separators are intentionally placed between all major sections.
- `Zotero Item Notes` means standalone child notes in Zotero.
- Comments typed onto PDF highlights belong to `PDF Annotations`, not `Zotero Item Notes`.

## Important Caveats

- The plugin's built-in `Import notes` command exists but is not part of this workflow.
- Do not patch it out unless explicitly asked.
- The plugin writes to fixed output paths.
- `zotero_notes` is intentionally the stable update location for raw Zotero imports and their assets.
- Do not move raw Zotero notes or their asset folders out of `zotero_notes` if you want re-imports to keep updating the same files.
- The plugin may still try to extract PDF annotation images during main-note imports.
- To avoid stray files at the vault root, main-note imports should share the Zotero-notes asset folder and base naming.

## Safe Procedure For Adding A New Paper-Type Import

1. Inspect the current plugin config in:
   - `TfT_Notes_Vault/.obsidian/plugins/obsidian-zotero-desktop-connector/data.json`
2. Keep `Import Zotero notes` unchanged unless the user explicitly wants raw-import behavior changed.
3. Create a new paper-type template in:
   - `TfT_Notes_Vault/Literature Review/templates/`
4. Add a new export format command with a paper-type-specific name.
   - examples:
     - `Import theory paper`
     - `Import empirical paper`
     - `Import framework paper`
5. Default main note output path:
   - `Literature Review/imports/{{citekey}}.md`
6. Link the main note to:
   - `Literature Review/zotero_notes/{{citekey}}-zotero-notes`
7. Point the main note command's asset path to the same stable Zotero-notes asset folder:
   - `Literature Review/zotero_notes/{{citekey}}-zotero-notes-assets`
   - use the same base naming as the raw import, currently `annotation`
8. Reload the plugin after config changes.
9. Test both:
   - the new paper-type command
   - `Import Zotero notes`

## When To Deviate From The Default

- If the user wants multiple distinct main-note files for the same paper type at once, then the filename strategy must change intentionally.
- Otherwise assume:
  - one canonical main note per paper
  - one canonical raw Zotero note per paper

## Good Future-Chat Summary

If starting from a fresh chat, summarize the setup like this:

> This vault uses Zotero Integration with one universal raw-import command (`Import Zotero notes`) and paper-type-specific main-note commands such as `Import overview paper`. Imported filenames must stay citekey-based because title-based filenames broke in the OneDrive vault. Raw Zotero notes and their assets live in `Literature Review/zotero_notes`, and main-note imports share that asset path to avoid stray image files at the vault root.

## Related Notes

- [[Literature Review/workflow-overview]]
- [[Literature Review/README]]
