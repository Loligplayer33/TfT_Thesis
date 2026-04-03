---
title: Workflow Overview
tags:
  - workflow
  - literature-review
  - thesis
status: draft
---

# Workflow Overview

## Core Principle

- `Zotero` is the source manager.
- `Obsidian` is the thinking space.
- `Zotero Integration` creates overview-note shells in the vault.

## What Lives Where

### Zotero

- store papers and PDFs
- manage metadata and citation keys
- annotate while reading
- organize papers into collections

### Obsidian

- capture what a paper means for the thesis
- distill key concepts, distinctions, and tensions
- connect papers to the thesis framing
- track week-by-week reading focus

## Current Plugin Workflow

The working commands are:

- `Import overview paper`
- `Import Zotero notes`

They create notes from a Zotero item using:

- template: [[Literature Review/templates/overview-paper-template]]
- template: [[Literature Review/templates/zotero-notes-template]]
- main note folder: `Literature Review/imports`
- Zotero note folder: `Literature Review/zotero_notes`
- shared asset folder: `Literature Review/zotero_notes/{{citekey}}-zotero-notes-assets`
- filename style: citation-key based

The plugin is useful for:

- creating the main source-note shell
- creating a separate imported-material note
- inserting the title
- inserting the citation key
- inserting the Zotero link
- inserting the source URL
- importing Zotero item notes and PDF annotations
- routing annotation assets into the stable Zotero-notes asset folder

The plugin is not the place where thinking happens. After import, the analytical sections are filled manually.

## How To Work With A Paper

1. Add the paper to Zotero.
2. Read and annotate in Zotero.
3. In Obsidian, run `Import overview paper`.
4. Select the Zotero item in the picker and confirm it.
5. Run `Import Zotero notes` for the same paper.
6. Open the main note in `imports` and the raw note in `zotero_notes`.
7. Leave the raw Zotero note and its assets in `zotero_notes` so re-imports keep updating them.
8. Fill in the sections about:
   - what the paper helps me see
   - key concepts
   - distinctions or categories
   - tensions
   - relevance for the thesis
   - what to follow up on

## Week 01 Setup

The current week-one workspace is:

- [[Literature Review/week_01_overview/week-01-current-focus]]
- [[Literature Review/week_01_overview/tankelevitchUnderstandingProtectingAugmenting2025]]
- [[Literature Review/literature-review-reading-plan]]

The purpose of week one is:

- get a broad overview of the TfT field
- identify recurring concepts
- identify useful distinctions
- decide what to read next

## Current Rule Of Thumb

- keep raw highlights and annotations available through Zotero imports
- keep distilled thesis thinking in the main Obsidian note
- keep annotation assets in the stable `zotero_notes` asset folder
- do not force deep synthesis too early
- use the overview notes to orient first, then synthesize later

## Related Notes

- [[Literature Review/README]]
- [[Literature Review/templates/overview-paper-template]]
- [[Literature Review/templates/zotero-notes-template]]
- [[Literature Review/week_01_overview/week-01-current-focus]]
