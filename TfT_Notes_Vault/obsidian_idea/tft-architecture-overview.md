# Tools for Thought — Architecture & Decision Overview

## 1. Foundation: The Research Paper and Its Core Ideas

The CHI 2026 workshop proposal "Tools for Thought: Understanding, Protecting, and Augmenting Human Cognition with Generative AI — From Vision to Implementation" (Zhang et al.) establishes the conceptual foundation for this project. The paper's central argument is that GenAI tools should be evaluated not just on whether they help users complete tasks, but on whether they protect and augment the cognitive processes underlying human thought.

### 1.1 Key Concepts from the Paper

**Tools for Thought (TfT)** are sociotechnical systems that prioritize their impact on cognition — reasoning, memory, ideation, critical thinking — over mere productivity. The focus is on how systems affect and support higher cognitive functions, not just on the artifacts being produced.

**Process-oriented support** emerged as a key design strategy from the CHI 2025 workshop: helping users reason *forward* to their own solution rather than *backward* from an AI-generated one. This is the central design tension that informs every architectural decision below.

**The perception-performance paradox**: Users may perceive AI as more helpful even when their learning outcomes are worse. This means the system cannot rely on user satisfaction as a proxy for cognitive benefit — it needs to make the quality of thinking visible.

**Intermediary artifacts**: Notes, diagrams, outlines, and other tangible outputs that emerge during thinking. AI often causes users to skip these, but they are critical scaffolding for cognition. A TfT should ensure these artifacts are created, not bypassed.

### 1.2 The Paper's Three Research Themes

| Theme | Focus | Core Question |
|-------|-------|---------------|
| **TfT Strategies** | Design patterns and usage strategies | How can GenAI be designed and applied as a TfT? |
| **TfT Outcomes** | Defining and measuring success | What counts as a desirable outcome beyond task performance? |
| **TfT Experience & Adoption** | Friction vs. productivity | How do we get users to adopt tools that may slow them down? |

These three themes map directly onto the architectural layers of our proposed system.

---

## 2. The First Architectural Question: Orchestration vs. Flexibility

### 2.1 The Decision

When implementing TfT strategies, should the system use a tightly orchestrated pipeline (e.g., LangGraph) or a flexible, tool/skill-based approach where the LLM decides what to do?

### 2.2 Options Considered

#### Option A: Full Orchestration (LangGraph-style state machine)

A graph-based workflow where the system enforces specific steps — elicit user reasoning before generating solutions, route to reflection nodes after producing output, ensure intermediary artifacts are created.

**Strengths:**
- Directly enforces the paper's design strategies (e.g., process-oriented support)
- Prevents the LLM from defaulting to "just give the answer" mode
- Predictable, testable cognitive scaffolding
- Ensures intermediary outcomes aren't skipped

**Weaknesses:**
- Rigid — may feel paternalistic or scripted
- Poor adaptability to diverse cognitive tasks and user contexts
- The paper cites Ashktorab et al.: users react negatively to cognitive forcing functions that create extra work
- Difficult to accommodate the variety of "usage strategies" users might pursue

#### Option B: Flexible Skills / Tools (LLM decides)

Give the LLM access to a rich toolkit and let it adapt to context. Different users in different situations get different support.

**Strengths:**
- Adapts to diverse cognitive tasks (sensemaking, brainstorming, debugging, writing)
- Supports the paper's "usage strategies" where users find their own cognitive workflows
- Less friction, better adoption potential
- Natural conversation flow

**Weaknesses:**
- LLMs default to path of least resistance — producing outputs rather than scaffolding thinking
- No guarantee that cognitively beneficial patterns are followed
- Risk of becoming "just another chatbot" without the TfT intent

#### Option C: Hybrid (Chosen Approach) ✅

A structured spine with flexible execution. A lightweight orchestration layer enforces non-negotiable cognitive checkpoints, while within and between those checkpoints, the LLM freely selects skills and adapts to context.

**Strengths:**
- Preserves cognitive guardrails without rigidity
- Adapts to user context within structured phases
- Balances the paper's design strategies (enforced) with usage strategies (flexible)
- Allows the system to evolve — start with more structure, loosen as understanding grows

**Weaknesses:**
- Requires careful calibration of what's enforced vs. what's flexible
- More complex to design than either pure approach
- Risk of the "flexible" parts undermining the "structured" parts if not well-integrated

### 2.3 Implications of the Hybrid Choice

The hybrid approach means the system architecture has a clear separation between:
1. **Cognitive flow management** (orchestration) — when to prompt reflection, when to surface contradictions, when to transition between thinking modes
2. **Interaction execution** (skills) — how to actually engage the user within each phase

This separation directly influences how skills are designed: they become conversational stances rather than output-producing functions.

---

## 3. Redefining Skills: Conversation-Driven, Artifact-Driven

### 3.1 The Decision

Skills should not be output-driven (e.g., "summarize this document") but conversation-style-driven and artifact-driven. Each skill defines a mode of cognitive engagement, not a deliverable.

### 3.2 What a Skill Defines

Each skill is a configuration that includes:

| Component | Description | Example |
|-----------|-------------|---------|
| **Conversational role** | What stance the AI takes | Socratic tutor, devil's advocate, structured facilitator, provocateur |
| **Artifact types** | What intermediary artifacts it produces | Questions, comparison tables, concept maps, annotated highlights, reflection prompts |
| **Withholding rules** | What the AI deliberately refuses to do | Won't give direct answers before user articulates their own position |
| **Transition offers** | When it suggests moving to a different mode | Offers synthesis only when user signals readiness |

### 3.3 Implications

- Skills persist across conversation turns — they shape ongoing engagement, not single responses
- The orchestration layer manages skill selection and transitions rather than rigid workflow steps
- The skill library becomes the primary way design strategies are encoded
- Users can explicitly select skills or accept AI-suggested ones
- New skills can be added without changing the orchestration logic

---

## 4. The Canvas Concept

### 4.1 The Decision

Build a shared workspace where users upload materials and interact with AI through artifacts on a spatial canvas, rather than through pure chat. The AI operates *on and within* the canvas, offering provocations, questions, and structural scaffolds rather than direct solutions.

### 4.2 Canvas Implementation Options Considered

#### Option 1: Node-Graph Canvas (React Flow / xyflow)

A spatial graph of typed content nodes connected by edges.

**Strengths:** Rich spatial interaction; graphs serialize to JSON the LLM can reason about; spatial clustering gives signal about user's mental model; closest to the "thinking is spatial" insight.

**Weaknesses:** Complex to build; serialized state grows large; steep learning curve for some users.

**Implication for final product:** A powerful research tool, but potentially intimidating for casual users. Best suited for complex sensemaking and analysis tasks.

#### Option 2: Block-Based Structured Canvas (BlockNote / TipTap)

A structured document made of typed blocks — text, callouts, queries, collapsible sections.

**Strengths:** More predictable for LLM interaction; block operations are simple; familiar document-editing paradigm; each block is a discrete, referenceable artifact.

**Weaknesses:** Less spatial freedom; more linear than truly canvas-like; may not support the paper's emphasis on non-linear thinking.

**Implication for final product:** A comfortable writing environment with structured AI intervention points. Good for writing-centric workflows but less suited for open exploration.

#### Option 3: Hybrid Whiteboard (Excalidraw / TLDraw)

Freeform visual canvas with a semantic data model underneath. LLM works with JSON semantic layer; TLDraw renders visually.

**Strengths:** Richest visual interaction; excellent programmatic API (TLDraw); supports freeform spatial arrangement and visual grouping.

**Weaknesses:** Most complex engineering (bidirectional bridge between visual and semantic state); artifacts less naturally persistent and searchable; LLM cannot "see" the canvas visually.

**Implication for final product:** Maximum creative freedom but highest engineering cost. Risk of the semantic-visual bridge becoming a maintenance burden.

#### Option 4: Card-Based / Column-Based Workspace

Kanban-style interface with typed cards in categorized zones (e.g., "raw material," "questions," "insights," "contradictions," "synthesis").

**Strengths:** Natural mapping to cognitive process stages; clean, manageable serialized state; intuitive for users; easy for LLM to manipulate.

**Weaknesses:** More constrained than freeform canvas; structure may feel imposed rather than emergent.

**Implication for final product:** Most immediately usable. The zone structure itself teaches users about the cognitive process, which aligns with the paper's goals. But may limit users who think non-linearly.

---

## 5. The Obsidian Decision

### 5.1 The Decision

Rather than building a custom canvas, use Obsidian as the UI/canvas layer and focus engineering effort on the backend intelligence.

### 5.2 Why Obsidian

| Benefit | Description |
|---------|-------------|
| **Local-first persistence** | Everything is markdown files in a folder (vault). No database, no cloud dependency. Artifacts are files the user owns permanently. |
| **Built-in Canvas** | Obsidian Canvas is a spatial node-graph workspace stored as JSON — directly manipulable by the backend. |
| **Graph view** | Automatic network visualization of all linked notes — the "thinking structure" becomes visible. |
| **Metadata system** | YAML frontmatter + inline tags make notes queryable and categorizable without rigid folder hierarchies. |
| **Plugin ecosystem** | TypeScript plugins can add sidebar panels, respond to editor events, register commands, modify files. Primary integration point. |
| **Live reload** | External file changes appear instantly in Obsidian. Backend can write files and user sees them in real time. |
| **Philosophical alignment** | Obsidian's community is built around "tools for thought" (Zettelkasten, PKM). The user base already values cognitive augmentation over mere productivity. |

### 5.3 Obsidian Core Concepts

**Vault**: A plain folder on disk containing `.md` files. No proprietary format, no database. Fully portable.

**Internal links**: `[[note name]]` syntax creates connections between notes. The foundation of the knowledge graph.

**Graph view**: Interactive network visualization of all notes and their links. Reveals clusters, orphans, and structural patterns.

**Tags and frontmatter**: YAML metadata at the top of each note (e.g., `type: question`, `status: unresolved`, `skill: socratic`). Enables querying and filtering.

**Canvas**: `.canvas` files stored as JSON. Contain nodes (text cards, embedded notes, images) and edges (connections). Spatially arranged on an infinite workspace.

**Plugins**: TypeScript/JavaScript packages with access to the Obsidian API. Can read/modify files, add UI panels, respond to events, register commands.

**Live reload**: Obsidian watches the filesystem and reflects external changes immediately.

### 5.4 Obsidian CLI vs. Direct File Manipulation

#### Obsidian CLI

The Obsidian CLI is a community tool for interacting with vaults from the command line. It can open notes, create notes, search the vault, and trigger Obsidian URI commands.

**Potential uses:**
- Triggering Obsidian-specific actions (opening a note in the UI, executing plugin commands)
- Quick scripting and testing during development
- Launching Obsidian with a specific vault or note from an external workflow

**Limitations:**
- Designed for human command-line use, not as a programmatic API
- Requires Obsidian to be running (it sends commands to the running instance via URI protocol)
- Limited operation set — cannot do fine-grained file manipulation, canvas JSON editing, or frontmatter modification
- Adds an unnecessary dependency layer for most backend operations
- Not suited for real-time, high-frequency interactions between the backend and the vault

#### Direct File Manipulation ✅ (Recommended for backend operations)

The backend reads and writes files directly in the vault directory. Obsidian picks up changes via filesystem watching.

**Strengths:**
- Simple, fast, no external dependencies
- Full control over file content, frontmatter, link structure, canvas JSON
- Works whether or not Obsidian is running (can pre-generate content)
- Canvas `.canvas` files are plain JSON — trivially parseable and modifiable
- Easily testable — file operations are deterministic

**Weaknesses:**
- Cannot trigger Obsidian UI actions (opening a specific note, scrolling to a section)
- No awareness of Obsidian's current UI state (which note is open, cursor position)

#### Recommended Hybrid ✅

Use **direct file manipulation for all content operations** — creating notes, modifying frontmatter, updating canvas JSON, managing the vault structure. This is the backend's primary interface to the canvas layer.

Use the **Obsidian CLI or URI protocol for occasional UI triggers** — opening a newly created note, navigating the user to a reflection prompt, or triggering a custom plugin command. These are supplementary, not core.

This keeps the backend simple and testable while still being able to guide the user's attention within Obsidian when needed.

### 5.5 Implications of the Obsidian Choice

**Positive implications:**
- **Persistence is free.** Every artifact the AI creates is a file the user owns. No export step needed. Intermediary artifacts live in the user's knowledge system permanently.
- **Composability comes from Obsidian's features.** Users can link, embed, tag, query (via Dataview), and visualize notes without any custom engineering.
- **LLM interface simplifies.** Instead of complex serialized canvas state, the LLM reads/writes files. Context scoping uses the vault's link and folder structure.
- **User agency is preserved.** Users can always edit, reorganize, or delete anything the AI creates. AI contributions aren't locked behind a proprietary interface.
- **Scope reduction.** No frontend to build. Engineering focuses entirely on the intelligence layer.

**Negative implications / risks:**
- **Interactivity ceiling.** The proactive, in-context intervention pattern (AI pops up while you write) is harder to achieve than with a custom editor. See Section 6 for mitigation strategies.
- **Coupling to Obsidian.** If Obsidian's conventions don't support a needed interaction pattern, workarounds may be awkward. Migration to a custom solution later adds cost.
- **Canvas JSON complexity.** While the `.canvas` format is JSON, complex spatial layouts may produce large, noisy state representations that are difficult for the LLM to reason about.
- **Plugin development constraints.** The Obsidian plugin API, while capable, has limits and undocumented behaviors. Community support varies.

---

## 6. Interactivity Within Obsidian: Addressing the Concern

### 6.1 The Core Concern

The envisioned interaction — the AI proactively asking questions, challenging arguments, and surfacing contradictions while the user writes — requires real-time, editor-integrated, proactive engagement. This is the hardest pattern to achieve within Obsidian.

### 6.2 Achievable Interaction Patterns

#### Pattern A: Sidebar Chat Panel

A custom Obsidian plugin adds a chat sidebar. As the user writes, the plugin monitors changes (debounced) and sends context to the backend. AI responses appear in the sidebar.

**Experience:** Like having a thinking partner sitting next to you. The user glances at the sidebar, engages when relevant, continues writing.

**Limitation:** The AI is reacting in a separate panel, not intervening in the writing flow. Pull-adjacent rather than push.

**Technical difficulty:** Low — standard Obsidian plugin pattern.

#### Pattern B: Inline Callout Injection

The plugin inserts Obsidian callout blocks directly into the note the user is editing. After a paragraph, the AI might add:

```
> [!question] Challenge
> You argue X, but [[source-doc]] suggests Y. 
> How do you reconcile this?
```

**Experience:** Closer to the proactive pop-up vision. The challenge appears in the user's writing context. They can respond, dismiss, or incorporate it.

**Limitation:** Insertion timing and placement must be carefully calibrated to avoid being disruptive. Requires debouncing and probably user-configurable triggers (on save, on paragraph break, on explicit pause).

**Technical difficulty:** Medium — requires editor event handling and careful UX design.

#### Pattern C: Canvas-Based Interaction

The user works on an Obsidian Canvas. Their draft is one card, source materials are other cards. The AI adds question cards and challenge cards connected to specific parts of the draft.

**Experience:** Spatially interactive. The user sees their thinking landscape evolve. Connections between ideas, challenges, and sources are visible.

**Limitation:** Writing inside canvas cards is more constrained than in the full editor. Less comfortable for extended prose.

**Technical difficulty:** Medium — requires canvas JSON manipulation and state tracking.

#### Pattern D: Companion Note

The AI maintains a separate "AI companion" note that updates as the user writes. This note contains running questions, observations, and challenges. The user can have it open in a split pane alongside their working note.

**Experience:** The AI's thinking is visible in its own space. The user can consult it when they want. Less intrusive than inline injection.

**Limitation:** Less tightly integrated with the writing flow. The user might ignore it entirely.

**Technical difficulty:** Low — file creation and modification, no editor integration needed.

### 6.3 Recommended Approach

Start with **Pattern A (sidebar) + Pattern D (companion note)** as the initial implementation. These are the easiest to build and validate.

Graduate to **Pattern B (inline callouts)** once you understand user behavior — when they want interruption, what triggers are most useful, how much friction is productive.

Use **Pattern C (canvas interaction)** for specific phases of work — initial exploration, material organization, synthesis — rather than as the primary writing environment.

### 6.4 Implications for the Final Product

The interactivity constraint means the initial product will feel more like "a thoughtful writing companion that maintains a running dialogue" than "an AI that intervenes in real time as you type." This is actually not necessarily worse — it respects the user's focus and flow while keeping cognitive scaffolding available. The paper's adoption theme (Section 1.3) warns that too much friction causes rejection. A companion that's always available but doesn't interrupt may be more adoptable than one that constantly challenges.

---

## 7. Revised Architecture (with Obsidian, Path A)

### 7.1 System Layers

```
┌─────────────────────────────────────────────────┐
│  OBSIDIAN (Canvas Layer)                        │
│  The vault: markdown files, canvas JSON,        │
│  graph view, frontmatter metadata               │
│  User interacts here. AI's artifacts appear     │
│  here. Everything persists as files.            │
├─────────────────────────────────────────────────┤
│  OBSIDIAN PLUGIN (Integration Layer)            │
│  Sidebar chat panel. Editor event monitoring.   │
│  Sends context to backend. Renders responses.   │
│  Optional: inline callout injection.            │
├─────────────────────────────────────────────────┤
│  BACKEND SERVICE (Intelligence Layer)           │
│                                                 │
│  ┌─────────────────────────────────────────┐    │
│  │  Context Assembly                       │    │
│  │  Reads active note + neighbors +        │    │
│  │  relevant metadata. Scopes context for  │    │
│  │  LLM. Summarizes distant vault regions. │    │
│  └─────────────────────────────────────────┘    │
│                                                 │
│  ┌─────────────────────────────────────────┐    │
│  │  Orchestration Layer                    │    │
│  │  Lightweight state tracker.             │    │
│  │  Manages skill transitions.             │    │
│  │  Triggers cognitive checkpoints.        │    │
│  │  Enforces: don't skip to final output.  │    │
│  └─────────────────────────────────────────┘    │
│                                                 │
│  ┌─────────────────────────────────────────┐    │
│  │  Skill Layer                            │    │
│  │  Library of conversational stances.     │    │
│  │  Each skill defines: role, artifact     │    │
│  │  types, withholding rules, transitions, │    │
│  │  and vault interaction patterns.        │    │
│  └─────────────────────────────────────────┘    │
│                                                 │
│  ┌─────────────────────────────────────────┐    │
│  │  Vault Writer                           │    │
│  │  Creates/modifies files in the vault.   │    │
│  │  Manages frontmatter, links, canvas     │    │
│  │  JSON. Primary output channel.          │    │
│  └─────────────────────────────────────────┘    │
├─────────────────────────────────────────────────┤
│  ARTIFACT STORE (Metadata Layer)                │
│  Tracks all AI-generated artifacts: content,    │
│  creation context, skill that produced them,    │
│  relationships, position in thinking trail.     │
│  May be a lightweight DB or structured JSON.    │
│  Feeds back into context assembly.              │
└─────────────────────────────────────────────────┘
```

### 7.2 Data Flow

1. **User writes** in Obsidian (editor or canvas).
2. **Plugin detects change**, sends current note content + relevant context to the backend.
3. **Context Assembly** reads the active note, its linked neighbors, relevant frontmatter metadata, and summarizes the broader vault state. Constructs an LLM-ready context payload.
4. **Orchestration Layer** evaluates the current state: What skill is active? Is a cognitive checkpoint due? Should it suggest a skill transition? It determines the *mode* of engagement.
5. **Skill Layer** shapes the LLM's response according to the active skill's conversational stance — what role it takes, what artifacts it produces, what it withholds.
6. **LLM generates** a response: a chat message (appears in sidebar), artifacts to create (notes, questions, comparisons), and/or vault modifications (callout injection, canvas additions).
7. **Vault Writer** executes file operations — creating notes, updating frontmatter, modifying canvas JSON, optionally injecting callouts.
8. **Obsidian live-reloads** the changed files. The user sees new artifacts appear.
9. **Artifact Store** logs what was created, by which skill, in what context, linking it to the thinking trail.

### 7.3 Vault Interaction Patterns by Skill

Each skill defines not just a conversational stance but also how it interacts with the vault:

| Skill | Vault Interaction Pattern |
|-------|--------------------------|
| **Socratic Questioner** | Creates question notes linked to the user's working note. Questions tagged `type: question`, `status: open`. |
| **Devil's Advocate** | Creates counterargument notes. Adds challenge callouts inline. Links counterarguments to the specific claims they challenge. |
| **Structured Facilitator** | Creates outline/framework notes. May scaffold a canvas with predefined zones. Updates structure as thinking evolves. |
| **Synthesis Helper** | Creates synthesis notes that reference multiple source notes. Highlights gaps and contradictions across linked materials. |
| **Reflective Prompter** | Creates reflection prompt notes at cognitive checkpoints. Tags them for later review. Asks the user to fill in their own assessment. |

---

## 8. Intermediary Artifact Design

### 8.1 Properties of Good Intermediary Artifacts

Drawing from the paper's framework, intermediary artifacts should be:

| Property | What It Means | How Obsidian Enables It |
|----------|---------------|-------------------------|
| **Composable** | Can be combined, merged, fed into later thinking stages | Internal links, note embedding, Dataview queries |
| **Exportable** | Can be pulled out as standalone deliverables | Already markdown files — portable by nature |
| **Referenceable** | AI can point back to them in later conversation | Internal links + frontmatter metadata |
| **Visible** | User can see the structure of their thinking | Graph view, canvas spatial layout |
| **Owned** | User controls, edits, reorganizes freely | Local files — no proprietary lock-in |

### 8.2 Artifact Types and Their Vault Representation

| Artifact Type | Vault Representation | Frontmatter Tags |
|---------------|---------------------|------------------|
| Question | Markdown note with the question and context | `type: question`, `status: open/resolved`, `source-skill: socratic` |
| Counterargument | Note linked to the claim it challenges | `type: counterargument`, `challenges: [[claim-note]]` |
| Comparison table | Markdown table or canvas with side-by-side cards | `type: comparison`, `items: [A, B, C]` |
| Reflection prompt | Note with questions for the user to fill in | `type: reflection`, `checkpoint: true`, `phase: exploration` |
| Concept map | Canvas file with linked concept nodes | `type: concept-map`, `topic: X` |
| Synthesis | Note that weaves together multiple sources | `type: synthesis`, `sources: [[note1]], [[note2]]` |
| Thinking trail | Auto-generated log of the cognitive journey | `type: trail`, `session: YYYY-MM-DD` |

---

## 9. Three Development Paths (From Section 5 Discussion)

### Path A: Obsidian-Native ✅ (Chosen starting point)

Build an Obsidian plugin + backend service. Accept sidebar-plus-callouts interaction model.

**Scope:** Plugin (sidebar chat, file monitoring, callout injection), backend (context assembly, orchestration, skills, vault writer).

**Timeline advantage:** Ship fastest. Validate TfT concepts before investing in custom UI.

**Interactivity:** Good but not maximally immersive. Companion-style rather than interventionist.

**Best for:** Proving the concept works. Understanding what interaction patterns users actually want.

### Path B: Custom Editor + Obsidian Storage

Build a custom writing interface (TipTap / ProseMirror / BlockNote) that reads/writes to the Obsidian vault. Full control over inline annotations, margin comments, real-time AI intervention.

**Scope:** Everything in Path A, plus a custom editor with rich decoration support.

**Timeline:** Significantly longer. Justified only after Path A validates the concept.

**Interactivity:** Maximum. Inline margin comments, tooltip challenges, real-time indicators.

**Best for:** The eventual product, once you know what interaction patterns matter.

### Path C: Fully Custom

Build everything — editor, canvas, persistence, graph visualization.

**Scope:** Full application stack.

**Timeline:** Longest. Justified only if Obsidian's conventions fundamentally cannot support the needed patterns.

**Best for:** A standalone product with unique interaction requirements. Probably not the right starting point.

### Migration Path: A → B → (possibly C)

Start with Path A. Learn what works. Graduate to Path B by building a custom editor that shares the Obsidian vault as a backend. The vault structure, artifact format, and backend intelligence carry forward. Only the interaction surface changes.

---

## 10. Open Questions and Next Steps

1. **Skill definition format:** What does a skill look like as code? What configuration schema captures conversational role, artifact types, withholding rules, and vault interaction patterns?

2. **Context assembly strategy:** How to efficiently scope vault context for the LLM — which notes to include in full, which to summarize, how to handle large vaults?

3. **Orchestration trigger design:** What signals indicate a cognitive checkpoint is needed? How to detect "the user has accumulated raw material but hasn't synthesized" from file and interaction patterns?

4. **Canvas JSON manipulation:** How to reliably read, modify, and write Obsidian Canvas JSON from the backend — node creation, edge management, spatial layout?

5. **Evaluation framework:** How to measure whether the system actually protects and augments cognition, aligned with the paper's outcome typology (intermediary, cognitive, task)?

6. **Plugin development:** Technical architecture of the Obsidian plugin — event handling, sidebar rendering, communication with the backend service.
