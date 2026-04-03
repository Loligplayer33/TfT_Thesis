---
title: Literature Review Workflow
tags:
  - workflow
  - literature-review
  - thesis
aliases:
  - Lit Review Workflow
---

# Literature Review Workflow

This folder contains a lightweight workflow for handling your first thesis reading phase across Zotero, Obsidian, and Codex.

## Core Principle

- `Zotero` tracks sources, metadata, PDFs, citations, and highlights.
- `Obsidian` holds distilled thinking notes after you finish reading.
- `Codex` helps you compare, refine, and connect notes inside the vault.

## Simple Workflow

1. Add a paper to Zotero.
2. Read and annotate it in Zotero.
3. After reading, run `Import overview paper` to create the main note in `Literature Review/imports`.
4. Run `Import Zotero notes` to create the companion imported-material note in `Literature Review/zotero_notes`.
5. Leave the Zotero-notes imports and their assets in `zotero_notes` so re-imports keep updating the same files.
6. Capture only what the paper helps you see for your thesis.
7. Let synthesis happen later, once you have actually read several papers.

The imported filenames stay compact and stable by using the citation key, while the full paper title remains inside the note content.
Overview-paper imports share the Zotero-notes asset folder so the plugin does not drop stray annotation images at the vault root.

## Good Defaults

- Keep raw highlights in Zotero.
- Keep distilled thinking in the main Obsidian note.
- Keep imported Zotero notes and PDF annotations in the companion Zotero-notes file.
- Keep raw Zotero note assets in `zotero_notes` as the stable asset location.
- Do not force a rigid claim/problem structure too early.
- Link notes with Obsidian wikilinks instead of repeating content.

## Current Reading Orientation

This section is a **working reading orientation**, not a final settled literature position.

### Current Framing Anchor

One important current framing paper is:

- Zhang et al. (CHI 2026), *Tools for Thought: Understanding, Protecting, and Augmenting Human Cognition with Generative AI — From Vision to Implementation*

Useful current concepts associated with this line of work:

- process-oriented support
- forward reasoning instead of backward reasoning from AI-generated answers
- the perception-performance paradox
- intermediary artifacts
- adoption tension around productive friction

### Current Sources To Engage

These are important working sources, but they should be treated as a provisional reading map rather than a final canon:

| Source | Contribution |
| --- | --- |
| Zhang et al. CHI 2026 | Primary framing paper for current TfT direction |
| Tankelevitch et al. 2025 (CHI 2025 workshop synthesis) | Broad landscape of concrete TfT designs |
| Zhang & Reicherts 2025 | Process-oriented support and forward reasoning |
| Sarkar 2024 ("AI Should Challenge, Not Obey") | The Provocateur role |
| Rogers et al. 2025 | Intermediary, cognitive, and task outcomes |
| Bjork — Desirable Difficulties | Learning through strategic difficulty |
| Kapur — Productive Failure | Struggle before instruction |
| Vygotsky — Scaffolding / ZPD | Temporary support structures |
| Kreijkes et al. 2025 | Perception-performance paradox |
| Lehmann et al. 2024 | Explanation-seeking vs. solution-seeking |
| Fan et al. 2025 | Metacognitive laziness |
| Ashktorab et al. 2025 | Resistance to cognitive forcing functions |
| Kazemitabaar et al. 2025 | Cognitive engagement techniques |
| Lira et al. 2025 | Cases where AI can support skill development |

## Start Here

- Use [[overview-paper-template]]
- Use [[week-01-current-focus]]
