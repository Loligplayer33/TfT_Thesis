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

The canonical overview note for the current source map is:

- [[Literature Review/Overview Synthesis and Reading Map]]

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

| Source                                                 | Contribution                                    |
| ------------------------------------------------------ | ----------------------------------------------- |
| Zhang et al. CHI 2026                                  | Primary framing paper for current TfT direction |
| Tankelevitch et al. 2025 (CHI 2025 workshop synthesis) | Broad landscape of concrete TfT designs         |
| Zhang & Reicherts 2025                                 | Process-oriented support and forward reasoning  |
| Sarkar 2024 ("AI Should Challenge, Not Obey")          | The Provocateur role                            |
| Rogers et al. 2025                                     | Intermediary, cognitive, and task outcomes      |
| Bjork — Desirable Difficulties                         | Learning through strategic difficulty           |
| Kapur — Productive Failure                             | Struggle before instruction                     |
| Vygotsky — Scaffolding / ZPD                           | Temporary support structures                    |
| Kreijkes et al. 2025                                   | Perception-performance paradox                  |
| Lehmann et al. 2024                                    | Explanation-seeking vs. solution-seeking        |
| Fan et al. 2025                                        | Metacognitive laziness                          |
| Ashktorab et al. 2025                                  | Resistance to cognitive forcing functions       |
| Kazemitabaar et al. 2025                               | Cognitive engagement techniques                 |
| Lira et al. 2025                                       | Cases where AI can support skill development    |

## Reading Sequence

The literature review should answer one guiding question:

**What design and usage strategies exist, or can be derived, that help prevent cognitive offloading when people use GenAI?**

To answer that, read in this sequence:

0. Start with the overview pass in [[Literature Review/Overview Synthesis and Reading Map]].
1. Understand the problem.
2. Understand the theoretical foundations.
3. Map the current strategy landscape.
4. Deepen the core learning-science anchors from the thesis spec.

### Stage 0: Overview First

Goal: get the field map, thesis framing, and metacognitive problem lens before deep reading.

- Priority: Tankelevitch et al. (2025) workshop synthesis
- Priority: Zhang et al. (2026) workshop framing paper
- Priority: Tankelevitch et al. (2024)

### Phase 1: Understand The Problem

Goal: build a precise picture of how GenAI can erode cognition and why a TfT framing is needed.

- Priority: Colombatto, Rintel & Tankelevitch (2025)
- Priority: Tankelevitch et al. (2024)
- Priority: Lee et al. (2025)
- Priority: Fan et al. (2025)
- Priority: Kreijkes et al. (2025)
- Then: Bastani et al. (2025), Noy & Zhang (2023)

### Phase 2: Understand The Theoretical Foundations

Goal: identify the design principles and explanatory frameworks the taxonomy will lean on.

- Priority: Lehmann, Cornelius & Sting (2024)
- Priority: Zhang & Reicherts (2025)
- Priority: Lira et al. (2025)
- Then: Kazemitabaar et al. (2025), Ashktorab et al. (2025), Rogers et al. (2025), Singh et al. (2025)
- Supporting framing: Sarkar (2024), Sarkar (2024) "Intention Is All You Need", Sarkar et al. (2024)

### Phase 3: Map The Strategy Landscape

Goal: extract concrete strategy patterns, roles, and design examples from TfT work and adjacent research.

- Priority: Tankelevitch et al. (2025) workshop synthesis
- Priority: Zhang et al. (2026) framing paper
- Then: Zheng et al. (2023), Terzimehic et al. (2025)
- Context only: Robinson (2024), EY Americas (2023)

### Phase 4: Deepen The Thesis Anchors

Goal: connect the literature review back to the explicit theory base named in the thesis spec.

- Bjork: Desirable Difficulties
- Kapur: Productive Failure
- Vygotsky / Wood, Bruner & Ross: Scaffolding and the Zone of Proximal Development

## Suggested Sequence

| Week | Focus | Sources |
| --- | --- | --- |
| 1 | The problem | Colombatto et al., Lee et al., Fan et al., Kreijkes et al. |
| 2 | Core design principles | Zhang & Reicherts, Lehmann et al., Sarkar, Lira et al. |
| 3 | Strategy landscape | Tankelevitch et al. synthesis, Kazemitabaar et al., Ashktorab et al. |
| 4 | Theoretical anchors | Bjork, Kapur, Wood/Bruner/Ross |
| 5 | Framework sources | Rogers et al., Singh et al., Sarkar follow-up pieces |
| 6 | Adoption and context | Zheng et al., Terzimehic et al., Tankelevitch et al. (2024) |

Treat this as a guide, not a rigid schedule. The starred or priority papers should anchor the reading, and the rest can be skimmed or deferred depending on time.

## What To Extract From Each Paper

When you read, capture these points in the overview note:

1. What cognitive problem or risk the paper identifies.
2. What mechanism explains the problem.
3. What strategy the paper proposes, tests, or implies.
4. Whether that strategy is mainly a design strategy or a usage strategy.
5. What AI role the paper suggests, if any.
6. What cognitive function is being protected or augmented.
7. How strong the evidence is.

## Start Here

- Use [[Literature Review/Overview Synthesis and Reading Map]]
- Use [[Literature Review/templates/overview-paper-template]]
- Use [[Literature Review/Overview Papers/week-01-current-focus]]
