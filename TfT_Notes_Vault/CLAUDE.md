This vault is the working space for a bachelor thesis at KIT (Karlsruhe Institute of Technology), supervised by Joshua Holstein at the Digital Service Innovation group (Prof. Dr. Gerhard Satzger).

## What the Thesis Is About

The thesis is titled **"Strategies for Thoughtful Cognition"** (Thesis A from the offering). It investigates how Generative AI can be designed and used as a **Tool for Thought (TfT)** — a system that protects and augments human cognition rather than replacing it.

The core problem: current GenAI systems optimize for productivity and task completion, which leads to **cognitive offloading** — users defer thinking to the AI and unreflectively rely on its outputs. This erodes higher-order cognition: critical thinking, metacognition, reasoning, and reflection.

The thesis aims to counter this by identifying, systematizing, and demonstrating design and usage strategies that keep the user in the driver's seat — actively thinking rather than passively consuming AI output.

## The Four Deliverables

1. **Systematic Literature Review** — Survey existing design patterns and theories from HCI, Learning Sciences, and Cognitive Psychology that can prevent cognitive offloading. Key anchoring theories: Desirable Difficulties (Bjork), Scaffolding (Vygotsky/ZPD), Productive Failure (Kapur).
    
2. **Strategy Taxonomy** — Organize findings into Design Strategies (how the system is built) and Usage Strategies (how the user interacts), following the distinction from the CHI 2026 TfT workshop paper (Zhang et al.).
    
3. **Conceptual Framework** — Map AI roles (e.g., Socratic Tutor, Provocateur, Facilitator) to the cognitive functions they augment (critical thinking, metacognition, sensemaking), with strategies as the concrete mechanisms connecting them. Structure: Role → Strategy → Cognitive Function.
    
4. **Prototypical Validation** — A proof-of-concept demonstrating how a specific strategy shifts the user from passive consumer to active thinker. (The architecture for this lives outside this vault.)
    

## What This Vault Is For

This vault is the **research and thinking workspace** for deliverables 1–3. It is where:

- Literature is collected, read, and annotated
- Design patterns and strategies are extracted and organized
- The taxonomy and conceptual framework are developed iteratively
- Thesis writing happens

This vault is **not** the prototype codebase. The prototype is developed separately.

## Current Literature Workflow

The current literature-review workflow in this vault is centered in:

- [[Literature Review/README]]
- [[Literature Review/workflow-overview]]
- [[ai/zotero-import-template-guide]]

### Import Logic

- Main literature notes are imported into `Literature Review/imports/`.
- Raw Zotero notes and annotation-heavy imports are stored in `Literature Review/zotero_notes/`.
- Raw Zotero notes and their asset folders should stay in `zotero_notes` so re-imports keep updating the same files.
- Imported filenames should stay **citekey-based**, not title-based, because long title-based filenames caused problems in the OneDrive-backed vault.

### Current Zotero Integration Commands

- `Import overview paper`
  - creates the main thinking note for overview-type papers
- `Import Zotero notes`
  - creates the companion raw note with Zotero item notes and PDF annotations
  - uses the stable `zotero_notes` folder

### Asset Handling

- The Zotero-notes import owns the stable asset location:
  - `Literature Review/zotero_notes/{{citekey}}-zotero-notes-assets`
- Main-note imports may still trigger annotation asset extraction because of plugin behavior.
- To avoid stray top-level asset files, main-note imports should share the same asset path and base naming as the Zotero-notes import, rather than creating a separate asset folder.

## Literature Framing

The detailed literature framing for this thesis should be treated as **provisional** and may evolve during the review.

For current reading orientation and source priorities, consult:

- [[Thesis Overview]]
- [[Literature Review/README]]

Do not assume that one workshop paper or one current source list is the final settled grounding unless the notes in those locations clearly say so.

## How to Help in This Vault

When working in this vault, keep in mind:

- **This is a research project.** Accuracy, proper attribution, and academic rigor matter. Do not fabricate claims or sources.
- **The user is the thinker.** This vault exists to scaffold _David's_ thinking. When in doubt, ask questions rather than produce conclusions. This is a thesis about preventing cognitive offloading — practice what it preaches.
- **Respect the structure.** If the vault has a folder structure or naming conventions, follow them. If unsure, ask before reorganizing.
- **Connect, don't duplicate.** When creating or editing notes, link to existing relevant notes rather than restating their content.
- **Keep shared AI context current.** If a change affects future chats or multiple agent contexts, update the relevant files in `ai/` and any canonical instruction/context note such as this one.

## Agent Guidance

If you are an AI agent entering this vault fresh:

- Read this file first.
- Then read [[ai/zotero-import-template-guide]] if the task touches Zotero imports, note templates, or workflow automation.
- Then read the most relevant workflow note in [[Literature Review/workflow-overview]] before changing structure or templates.
- If you change shared workflow, config, folder structure, naming conventions, or the project's current phase, update the relevant notes in `ai/` before you finish.

If a tool also supports `AGENTS.md`, use that file as the entrypoint for general conventions and treat this file as the fuller project-context note.
