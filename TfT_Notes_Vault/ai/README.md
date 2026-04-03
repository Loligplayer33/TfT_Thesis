---
title: AI Notes
tags:
  - ai
  - workflow
  - handoff
---

# AI Notes

This folder stores notes meant to help future AI chats pick up important workflow context quickly.

## Maintenance Rule

Whenever a change should survive across chat contexts, update the relevant note(s) in this folder.

Examples:

- Zotero or Obsidian config changes
- import command changes
- folder or path renames
- naming convention changes
- new workflow rules
- new project phases or changes in research focus
- adding a new reusable AI handoff note

If an agent changes something that future chats should know, this folder should usually be updated before the task is considered complete.

General agent conventions live in [[AGENTS]]. This folder should focus on reusable AI handoff/context notes rather than duplicating the full rule set.

## Validation

After changing shared AI documentation, workflow docs, or Zotero import config, run:

- `python3 ai/scripts/validate_ai_docs.py`

## Current Guides

- [[ai/zotero-import-template-guide]]
