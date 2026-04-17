---
title: Literature Review Workflow
tags:
  - workflow
  - literature-review
  - thesis
aliases:
  - Lit Review Workflow
  - Reading Plan - Literature Review
  - Literature Review Reading Plan
---
# Literature Review Workflow

This folder contains the working literature review for the thesis. The workflow spans three layers that feed into each other: Zotero (reading record), Obsidian (per-paper headers + thematic synthesis), and the Synthesis notes where cross-paper argument develops.

## Core Principle

- **Zotero** holds sources, metadata, PDFs, highlights, and in-situ reading reactions. This is the full reading record.
- **Obsidian per-paper layer** holds a thin header per paper (title + Zotero metadata + links). Paper-level thinking lives in the Zotero note, not here.
- **Obsidian synthesis layer** holds thematic notes in [[Literature Review/Synthesis/README|the Synthesis folder]] where arguments develop across papers.

See [[Literature Review/Synthesis/README|Synthesis folder]] for the six thematic synthesis notes: The Problem, Theoretical Foundations, Design Strategies, Usage Strategies, AI Roles, Adoption and Friction.

## Workflow Per Paper

1. Add the paper to Zotero.
2. Read and annotate it in Zotero, capturing highlights and in-situ reactions.
3. Run `Import overview paper` to create the thin header note in `Literature Review/imports/` (or `Literature Review/Overview Papers/` for overview-type papers).
4. Run `Import Zotero notes` to create the companion imported-material note in `Literature Review/zotero_notes/`.
5. Leave the Zotero-notes imports and their assets in `zotero_notes` so re-imports keep updating the same files.
6. Open the 1–3 synthesis notes the paper touches. For each:
   - Add 2–6 bullets under an H3 subheading wikilinked to the overview paper
   - If the paper shifts your thinking, update the **Working Thoughts** section of Current Argument. Once multiple papers back a claim, promote it into **Synthesized Position** with citations.
7. If the paper references sources worth tracking (without being read yet), add them to [[Literature Review/Sources by Domain]] under the relevant theme.

## Good Defaults

- Keep raw highlights and in-situ reactions in Zotero.
- Keep paper-level structure minimal in Obsidian — the Zotero note already does that work.
- Paper Contributions bullets in synthesis notes are 1–2 sentences max; compress further if they drift longer.
- In synthesis prose (Working Thoughts, Synthesized Position), use plain citekeys in parentheses like `(zhang2026tools)`. The H3 wikilink in Paper Contributions handles backlink coverage.
- Stable terms go in [[Glossary]]. Open research questions live there too.
- Use Obsidian wikilinks for all internal vault references.

## Current Reading Orientation

This section is a **working reading orientation**, not a final settled literature position.

The canonical overview note for the current source map is [[Literature Review/Overview Synthesis and Reading Map]].

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

The canonical source list and reading priority lives in [[Literature Review/Overview Synthesis and Reading Map]]. Treat that as provisional, not a final canon.

## Reading Sequence

The literature review should answer one guiding question:

**What design and usage strategies exist, or can be derived, that help prevent cognitive offloading  or cognitive augmentation when people use GenAI?**

Reading happens in phases defined in [[Literature Review/Overview Synthesis and Reading Map]]. Stage 0 (overview pass) is substantially complete: Tankelevitch 2025, Zhang 2026, and Tankelevitch 2024 all have Zotero notes.

## What To Extract From Each Paper

When reading, capture these points across the Zotero note and the relevant synthesis notes:

1. What cognitive problem or risk the paper identifies.
2. What mechanism explains the problem.
3. What strategy the paper proposes, tests, or implies.
4. Whether that strategy is mainly a design strategy or a usage strategy.
5. What AI role the paper suggests, if any.
6. What cognitive function is being protected or augmented.
7. How strong the evidence is.
8. What tension or trade-off remains open.

Items 1–2 land in [[Literature Review/Synthesis/The Problem]]. Items 3–4 land in [[Literature Review/Synthesis/Design Strategies]] or [[Literature Review/Synthesis/Usage Strategies]]. Item 5 lands in [[Literature Review/Synthesis/AI Roles]]. Item 6 is a tagging dimension across strategies. Item 8 often belongs in [[Literature Review/Synthesis/Adoption and Friction]].

## Start Here

- [[Literature Review/Overview Synthesis and Reading Map]] — the reading map and source priorities
- [[Literature Review/Synthesis/README|Synthesis]] — the six thematic synthesis notes
- [[Literature Review/templates/overview-paper-template]] — the paper header template
- [[Literature Review/Sources by Domain]] — tracking for sources referenced but not yet read
- [[Glossary]] — stable definitions
