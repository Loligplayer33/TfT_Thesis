# Tools for Thought — Architecture & Decision Overview

_A living document synthesizing the full design conversation: from research foundations through architectural decisions, alternatives considered, consequences of each choice, and honest critique of our own reasoning._

---

## 1. Foundation: The Research Paper and Its Core Ideas

The CHI 2026 workshop proposal "Tools for Thought: Understanding, Protecting, and Augmenting Human Cognition with Generative AI — From Vision to Implementation" (Zhang et al.) establishes the conceptual foundation for this project. The paper's central argument is that GenAI tools should be evaluated not just on whether they help users complete tasks, but on whether they protect and augment the cognitive processes underlying human thought.

### 1.1 Key Concepts from the Paper

**Tools for Thought (TfT)** are sociotechnical systems that prioritize their impact on cognition — reasoning, memory, ideation, critical thinking — over mere productivity. The focus is on how systems affect and support higher cognitive functions, not just on the artifacts being produced.

**Process-oriented support** emerged as a key design strategy from the CHI 2025 workshop: helping users reason _forward_ to their own solution rather than _backward_ from an AI-generated one. This is the central design tension that informs every architectural decision below.

**The perception-performance paradox**: Users may perceive AI as more helpful even when their learning outcomes are worse (Kreijkes et al. 2025). This means the system cannot rely on user satisfaction as a proxy for cognitive benefit — it needs to make the quality of thinking visible.

**Intermediary artifacts**: Notes, diagrams, outlines, and other tangible outputs that emerge during thinking. AI often causes users to skip these (e.g., skipping low-fidelity prototypes because GenAI encourages jumping straight to high fidelity), but they are critical scaffolding for cognition. A TfT should ensure these artifacts are created, not bypassed.

**The adoption tension**: Design strategies that introduce productive friction can be met with resistance from both users and stakeholders. Ashktorab et al. (2025) found users reacted negatively to cognitive forcing functions. 96% of C-suite executives expect AI to boost productivity (Robinson 2024). A TfT that slows people down for cognitive benefit faces a real adoption challenge.

### 1.2 The Paper's Three Research Themes

| Theme                         | Focus                                | Core Question                                               | Maps to Architecture                   |
| ----------------------------- | ------------------------------------ | ----------------------------------------------------------- | -------------------------------------- |
| **TfT Strategies**            | Design patterns and usage strategies | How can GenAI be designed and applied as a TfT?             | Skill Layer + Orchestration Layer      |
| **TfT Outcomes**              | Defining and measuring success       | What counts as a desirable outcome beyond task performance? | Artifact Store + Evaluation Framework  |
| **TfT Experience & Adoption** | Friction vs. productivity            | How do we get users to adopt tools that may slow them down? | Interaction Design + Skill Calibration |

### 1.3 Three Outcome Types (Rogers et al. 2025)

The paper distinguishes three types of outcomes, all of which our system should support:

| Outcome Type     | Description                                                          | System Implication                                                                  |
| ---------------- | -------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Intermediary** | Tangible artifacts (notes, diagrams) that scaffold thinking          | The vault's notes and canvas objects. Must be genuinely useful, not busywork.       |
| **Cognitive**    | Changes in understanding, learning, critical thinking, metacognition | Harder to measure. Reflection prompts and thinking trails attempt to surface these. |
| **Task**         | Performance on the actual work being done                            | A TfT should support cognition without undermining task completion.                 |

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

**Consequence if chosen:** The product would feel like a guided tutoring system — effective for structured learning tasks but frustrating for open-ended creative work. Users who already think well would feel constrained. The system would be hard to extend to new domains without redesigning the workflow graph.

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

**Consequence if chosen:** The product would feel natural and flexible but would likely fail at its core mission. Without structural guardrails, the AI would helpfully produce outputs instead of scaffolding thinking, because that's what maximizes user satisfaction in the short term — exactly the perception-performance paradox the paper warns about.

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

**Consequence of this choice:** The system has two distinct engineering challenges — designing the orchestration rules (what's enforced and when) and designing the skills (how the AI engages within each phase). These must be developed together, or they'll conflict. The orchestration must be lightweight enough not to feel rigid, but firm enough to prevent the LLM from bypassing cognitive scaffolding.

### 2.3 Implications of the Hybrid Choice

The hybrid approach creates a clear separation between:

1. **Cognitive flow management** (orchestration) — when to prompt reflection, when to surface contradictions, when to transition between thinking modes
2. **Interaction execution** (skills) — how to actually engage the user within each phase

This separation directly influences how skills are designed: they become conversational stances rather than output-producing functions.

**Critical implication:** The orchestration layer must have continuous awareness of what the user is doing. It cannot trigger a reflection checkpoint or suggest a skill transition if it doesn't know whether the user is writing, reading sources, organizing a canvas, or chatting. This awareness problem is addressed in detail in Section 6.

### 2.4 Self-Critique of the Hybrid Choice

The hybrid approach sounds elegant in theory, but there's a risk of it collapsing into one of the pure approaches in practice. If the orchestration rules are too few and too soft, the system effectively becomes Option B — the LLM does whatever it wants. If the rules accumulate and harden over time (because it's tempting to add "just one more checkpoint"), the system becomes Option A — a rigid pipeline disguised as a hybrid.

The mitigation is to treat the orchestration layer as a minimal, explicit, version-controlled set of rules rather than emergent logic scattered across the codebase. If you can't list the orchestration rules on a single page, they've grown too complex.

Additionally, the hybrid approach assumes the orchestration layer can reliably detect when checkpoints are needed. In practice, signals like "the user has been writing without engaging sources" are heuristic and may misfire — interrupting flow when the user is productively deep in thought. The system needs a way for users to dismiss or defer checkpoints gracefully, and the orchestration should learn from these dismissals.

---

## 3. Redefining Skills: Conversation-Driven, Artifact-Driven

### 3.1 The Decision

Skills should not be output-driven (e.g., "summarize this document") but conversation-style-driven and artifact-driven. Each skill defines a mode of cognitive engagement, not a deliverable. The AI adapts to what the user expects, but the skills themselves steer toward cognitive engagement rather than task completion.

### 3.2 What a Skill Defines

Each skill is a configuration that includes:

| Component                     | Description                                 | Example                                                                              |
| ----------------------------- | ------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Conversational role**       | What stance the AI takes                    | Socratic tutor, devil's advocate, structured facilitator, provocateur                |
| **Artifact types**            | What intermediary artifacts it produces     | Questions, comparison tables, concept maps, annotated highlights, reflection prompts |
| **Withholding rules**         | What the AI deliberately refuses to do      | Won't give direct answers before user articulates their own position                 |
| **Transition offers**         | When it suggests moving to a different mode | Offers synthesis only when user signals readiness                                    |
| **Vault interaction pattern** | How the skill manifests in the vault        | What files it creates, how they're linked, what frontmatter it uses, where they go   |

### 3.3 Skills as Conversational Protocols

A skill is essentially a _conversational protocol_ — a persistent set of behaviors, questioning patterns, and artifact-generation strategies. It's not a function that returns a result; it's a stance that shapes interaction across multiple turns.

This has an important implication for the orchestration layer: if skills define conversational stances rather than operations, the orchestration doesn't need to manage a rigid state machine. Instead, it manages _skill selection and transitions_ — determining when to suggest shifting from an exploratory stance to a synthesis stance, or when the user's behavior suggests a different mode of engagement would be beneficial.

### 3.4 Skills as Editable Files in the Vault

A key design decision (discussed in detail in Section 8): skills can be stored as markdown files in a `/skills/` folder within the vault itself. Each skill file defines the conversational stance, the available tools, and the behavioral rules in a human-readable format.

**Consequence:** The user can inspect how any skill works, modify its behavior, and create custom skills. This makes the system's cognitive scaffolding transparent, which directly addresses the paper's emphasis on user agency and the adoption challenge. If the user can see and modify the rules, the friction feels collaborative rather than imposed.

**Self-critique:** Making skills editable is powerful but risky. A user might weaken the cognitive safeguards (removing the "don't give direct answers" rule from the Socratic skill) because they want faster results — which is exactly the short-term thinking the system is supposed to protect against. Consider having "core rules" that are flagged as important with clear explanations of why they exist, while allowing modification of style, tone, and secondary behaviors.

### 3.5 Implications

- Skills persist across conversation turns — they shape ongoing engagement, not single responses
- The orchestration layer manages skill selection and transitions rather than rigid workflow steps
- The skill library becomes the primary way design strategies are encoded
- Users can explicitly select skills or accept AI-suggested ones
- New skills can be added without changing the orchestration logic
- The skill format doubles as documentation — explaining _why_ the system behaves as it does

---

## 4. The Canvas Concept

### 4.1 The Decision

Build a shared workspace where users upload materials and interact with AI through artifacts on a spatial canvas, rather than through pure chat. The AI operates _on and within_ the canvas, offering provocations, questions, and structural scaffolds rather than direct solutions.

### 4.2 Canvas Implementation Options Considered (Custom-Built)

These options were evaluated before the decision to use Obsidian (Section 5). They remain relevant as reference for future Path B/C development.

#### Option 1: Node-Graph Canvas (React Flow / xyflow)

A spatial graph of typed content nodes connected by edges.

**Strengths:** Rich spatial interaction; graphs serialize to JSON the LLM can reason about; spatial clustering gives signal about user's mental model; closest to the "thinking is spatial" insight.

**Weaknesses:** Complex to build; serialized state grows large; steep learning curve for some users.

**Consequence for final product:** A powerful research tool, but potentially intimidating for casual users. Best suited for complex sensemaking and analysis tasks.

#### Option 2: Block-Based Structured Canvas (BlockNote / TipTap)

A structured document made of typed blocks — text, callouts, queries, collapsible sections.

**Strengths:** More predictable for LLM interaction; block operations are simple; familiar document-editing paradigm; each block is a discrete, referenceable artifact.

**Weaknesses:** Less spatial freedom; more linear than truly canvas-like; may not support the paper's emphasis on non-linear thinking.

**Consequence for final product:** A comfortable writing environment with structured AI intervention points. Good for writing-centric workflows but less suited for open exploration.

#### Option 3: Hybrid Whiteboard (Excalidraw / TLDraw)

Freeform visual canvas with a semantic data model underneath. LLM works with JSON semantic layer; TLDraw renders visually.

**Strengths:** Richest visual interaction; excellent programmatic API (TLDraw); supports freeform spatial arrangement and visual grouping.

**Weaknesses:** Most complex engineering (bidirectional bridge between visual and semantic state); artifacts less naturally persistent and searchable; LLM cannot "see" the canvas visually.

**Consequence for final product:** Maximum creative freedom but highest engineering cost. Risk of the semantic-visual bridge becoming a maintenance burden.

#### Option 4: Card-Based / Column-Based Workspace

Kanban-style interface with typed cards in categorized zones (e.g., "raw material," "questions," "insights," "contradictions," "synthesis").

**Strengths:** Natural mapping to cognitive process stages; clean, manageable serialized state; intuitive for users; easy for LLM to manipulate.

**Weaknesses:** More constrained than freeform canvas; structure may feel imposed rather than emergent.

**Consequence for final product:** Most immediately usable. The zone structure itself teaches users about the cognitive process. But may limit users who think non-linearly.

### 4.3 Alternative Canvas Approaches: Existing Tools

Rather than building custom, we explored using existing tools as the canvas layer:

| Tool                              | Approach                                                 | Strengths                                                                                              | Weaknesses                                                   |
| --------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------ |
| **Obsidian**                      | Local markdown vault + Canvas feature + plugin ecosystem | Persistence free, composability built-in, graph view, spatial canvas, philosophical alignment with TfT | Interactivity ceiling, coupling to Obsidian conventions      |
| **Logseq**                        | Outliner-oriented, local files, plugin API               | Hierarchical structure natural for reasoning chains                                                    | Less spatial freedom than Obsidian Canvas, smaller ecosystem |
| **Tana**                          | Supertag system — typed, queryable entities              | Natural mapping to typed intermediary artifacts                                                        | Cloud-based, less open, limited API                          |
| **TLDraw (self-hosted)**          | Open-source freeform canvas + programmatic API           | Maximum visual freedom, excellent API                                                                  | Must build persistence, search, linking from scratch         |
| **Jupyter Notebooks**             | Interleaved code, text, and output cells                 | Good for technical users, programmatic manipulation easy                                               | Not suited for non-technical cognitive workflows             |
| **Headless CMS (Strapi/Payload)** | Maximum control over artifact schema                     | Full schema control, custom frontend                                                                   | Building from scratch, no spatial canvas built-in            |

---

## 5. The Obsidian Decision

### 5.1 The Decision

Use Obsidian as the UI/canvas layer and focus engineering effort on the backend intelligence. This was chosen as the starting point (Path A) with a migration path to a custom editor (Path B) if needed.

### 5.2 Obsidian Core Concepts

For reference, since Obsidian is new territory:

**Vault**: A plain folder on disk containing `.md` files. No proprietary format, no database. Fully portable. Everything is files you own.

**Internal links**: `[[note name]]` syntax creates connections between notes. Foundation of the knowledge graph. If the target doesn't exist, clicking creates it.

**Graph view**: Interactive network visualization of all notes and their links. Reveals clusters, orphans, structural patterns. Updates in real time as you work.

**Tags and frontmatter**: YAML metadata at the top of each note (e.g., `type: question`, `status: unresolved`, `skill: socratic`). Makes notes queryable and filterable without rigid folder hierarchies.

**Canvas**: `.canvas` files stored as JSON. Contain nodes (text cards, embedded notes, images, links) and edges (connections with labels). Spatially arranged on an infinite workspace. Nodes have position coordinates, dimensions, and colors. This is the spatial thinking surface.

**Plugins**: TypeScript/JavaScript packages with access to the Obsidian API. Can read/modify files, add UI panels (sidebars, modals), respond to events (file changes, cursor movements, editor changes), add commands. This is the primary integration point for our system.

**Live reload**: Obsidian watches the filesystem. External file modifications appear instantly. The backend can write files and the user sees them in real time.

**Dataview (community plugin)**: Query engine for vault metadata. Enables dynamic views across notes based on frontmatter tags. Useful for surfacing "all open questions" or "all unresolved contradictions."

### 5.3 Why Obsidian

| Benefit                     | Description                                                                                                 |
| --------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Local-first persistence** | Artifacts are files the user owns permanently. No export step. No database.                                 |
| **Built-in Canvas**         | Spatial node-graph workspace stored as JSON — directly manipulable by the backend.                          |
| **Graph view**              | Automatic network visualization of all linked notes — "thinking structure" becomes visible.                 |
| **Metadata system**         | YAML frontmatter + tags make notes queryable without rigid hierarchies.                                     |
| **Plugin ecosystem**        | TypeScript plugins can add UI panels, respond to events, modify files. Our integration point.               |
| **Live reload**             | External file changes appear instantly. Backend writes → user sees immediately.                             |
| **Philosophical alignment** | Community built around "tools for thought" (Zettelkasten, PKM). Users already value cognitive augmentation. |
| **Scope reduction**         | No frontend to build. Engineering focuses on the intelligence layer.                                        |

### 5.4 Obsidian CLI vs. Direct File Manipulation

#### Obsidian CLI

A community tool for interacting with vaults from the command line. Sends commands to the running Obsidian instance via URI protocol.

**Appropriate for:**

- Triggering UI actions: opening a specific note, scrolling to a section, executing a plugin command
- Guiding user attention: "here's a new reflection prompt, let me open it for you"
- Quick scripting and testing during development

**Not appropriate for (and why):**

- Content operations (creating, modifying, searching files) — the CLI requires Obsidian to be running, adds latency, has a limited operation set, and cannot do fine-grained manipulation of frontmatter, canvas JSON, or file content
- High-frequency operations — it's designed for human command-line use, not programmatic API calls
- Backend-driven vault manipulation — adds an unnecessary dependency layer

#### Direct File Manipulation ✅ (Primary backend interface)

The backend reads and writes files directly in the vault directory.

**Appropriate for:**

- All content operations: creating notes, modifying frontmatter, updating canvas JSON, managing folder structure, link management
- Works whether or not Obsidian is running (can pre-generate content)
- Fast, testable, no external dependencies
- Canvas `.canvas` files are plain JSON — trivially parseable and modifiable

**Limitation:** Cannot trigger Obsidian UI actions (opening a note, scrolling, etc.) or read Obsidian's current UI state (which note is open, cursor position).

#### Recommended Approach ✅

**Direct file manipulation for all content operations.** This is the backend's primary interface to the canvas/vault layer. Simple, fast, testable.

**Obsidian CLI/URI protocol for occasional UI guidance.** When the backend creates a reflection prompt or a new artifact and wants the user to see it, it can trigger Obsidian to open that note. These are supplementary, not core.

**The Obsidian plugin bridges the gap** for UI-state awareness. The plugin knows which note is open, detects editor changes, and reports this to the backend. So the backend gets UI awareness through the plugin, not through the CLI.

### 5.5 Consequences of the Obsidian Choice

**Positive consequences:**

- Persistence is free — every artifact is a file the user owns
- Composability comes from Obsidian's features — links, embeds, Dataview, graph view
- LLM interface simplifies — read/write files instead of complex serialized state
- User agency is preserved — users can edit, reorganize, delete anything
- Scope reduction — no frontend engineering, focus entirely on intelligence
- Community alignment — Obsidian users already think in terms of knowledge management

**Negative consequences / risks:**

- **Interactivity ceiling** — proactive, in-context AI intervention (see Section 6) is harder than with a custom editor
- **Coupling** — if Obsidian's conventions can't support a needed pattern, migration is costly
- **Canvas JSON complexity** — large canvases may produce noisy state for the LLM
- **Plugin API limitations** — undocumented behaviors, potential breaking changes in Obsidian updates

**Self-critique of this decision:** We may be over-indexing on "reduce engineering effort" at the expense of interaction quality. The paper's central argument is about cognitive augmentation — if the interaction model is too passive (sidebar + companion note), the system might not be different enough from "just having ChatGPT open next to your notes." The proactive intervention patterns (Pattern B: inline callouts, Pattern C: canvas cards) are what make this a genuine TfT rather than a chatbot with file access. If Obsidian's plugin API makes these patterns too awkward, we should recognize that early and move to Path B rather than compromising the cognitive scaffolding.

However, the counterargument is strong: building a perfect custom editor that nobody uses is worse than building an imperfect Obsidian integration that validates whether the TfT concepts work at all. Path A is a learning investment, not the final product.

---

## 6. The Awareness Problem: How the Backend Knows What You're Doing

### 6.1 Why This Matters

The orchestration layer cannot function without continuous situational awareness. It cannot trigger a reflection checkpoint if it doesn't know the user has been writing for 20 minutes without engaging sources. It cannot suggest a skill transition if it doesn't know the user has shifted from drafting to source analysis. It cannot surface contradictions if it doesn't know what the user is currently claiming.

The user works across multiple surfaces within Obsidian — writing in notes, arranging things on a canvas, chatting in the sidebar. Each surface emits different signals, and the backend must synthesize them into a coherent picture.

### 6.2 The Three Interaction Mediums

Each medium serves a different purpose and provides different signals to the backend:

#### The Chat Sidebar — Command Channel

The primary explicit interaction channel. The user directly addresses the AI: asking questions, giving instructions, requesting skill changes ("switch to devil's advocate mode"), responding to prompts, having back-and-forth dialogue.

**Signals to backend:** Explicit intent, questions, topic focus, engagement level, satisfaction/frustration.

**AI responds through:** Text messages in the sidebar. May also trigger vault operations (creating artifacts, modifying canvas) as a side effect of the conversation.

#### The Editor — Work Channel

The user's primary workspace. They're writing, not talking to the AI. But the AI is observing (through the plugin) and can respond through various channels depending on the active skill.

**Signals to backend:** Content being written, editing patterns (long sustained writing vs. frequent revisions), source references being added, pauses in activity, which note is active, when notes are switched.

**AI responds through:** Sidebar messages, inline callout injection (if implemented), companion note updates, new artifact creation in the vault.

#### The Canvas — Collaboration Channel

A shared spatial workspace. Both the user and the AI make structural moves — placing cards, drawing connections, grouping ideas. This is the closest thing to a truly collaborative surface.

**Signals to backend:** Spatial arrangement (what's placed near what), connections drawn, groups created, which cards have content vs. are empty placeholders, what sources are present on the canvas.

**AI responds through:** Adding nodes (question cards, challenge cards, suggestion cards), creating edges (connecting related or contradictory ideas), placing content near the relevant context.

### 6.3 The Session Context Mechanism

The Obsidian plugin maintains a lightweight **session context** that it continuously updates and sends to the backend:

```
Session Context (sent to backend on meaningful events):
- active_file: path and type (note or canvas)
- active_content: current content or recent diff
- visible_files: other files in split panes
- recent_activity: [file_switch, save, pause, chat_message]
- chat_messages: recent explicit messages from user
- time_since_last_interaction: seconds since last meaningful event
```

The plugin sends this context on meaningful events — file switch, save, pause in typing (debounced, e.g., 30 seconds of inactivity), explicit chat message — not on every keystroke.

### 6.4 Backend Working Memory

The backend maintains a **working memory** per session that accumulates context over time:

```
Working Memory (maintained by backend):
- current_skill: which skill is active
- turns_since_checkpoint: counter for orchestration
- recent_files_touched: list of files accessed in this session
- current_focus: inferred topic/task based on recent activity
- source_engagement: how much the user has interacted with source material
- artifact_history: what the AI has created and user's response to it
- canvas_state_summary: high-level description of the active canvas
```

The orchestration layer reads this working memory to make decisions: is a checkpoint due? Should a skill transition be suggested? Has the user been ignoring source material?

### 6.5 Self-Critique of the Awareness Approach

The session context mechanism is inherently heuristic. "Time since last interaction" is a poor proxy for "the user is stuck" — they might be deep in thought, or they might have gone to make coffee. "Low source engagement" might mean the user already knows the material well, not that they're ignoring evidence. The orchestration layer will make mistakes, and those mistakes will feel intrusive.

Mitigation: every checkpoint or intervention should be dismissable with zero friction (a single click or "not now" in chat). The orchestration should track dismissals and reduce frequency for users who consistently dismiss. The system should err on the side of too little intervention rather than too much — it's easier to add friction than to recover trust after annoying a user.

Additionally, canvas awareness is technically challenging. The canvas JSON can be large and changes to spatial arrangement are semantically meaningful but hard to interpret programmatically. "The user moved card A closer to card B" has meaning, but detecting that from JSON diffs requires spatial reasoning that may be noisy. Start with simple heuristics (which nodes are on the canvas, what edges exist) and add spatial interpretation only if it proves valuable.

---

## 7. Canvas Interaction: How the AI Reads and Modifies the Canvas

### 7.1 Obsidian Canvas JSON Structure

The Canvas format is a JSON file with a well-defined structure:

```json
{
  "nodes": [
    {
      "id": "node1",
      "type": "text",
      "x": 0,
      "y": 0,
      "width": 400,
      "height": 200,
      "text": "Markdown content in the card",
      "color": "1"
    },
    {
      "id": "node2",
      "type": "file",
      "x": 500,
      "y": 0,
      "width": 400,
      "height": 300,
      "file": "sources/research-paper.md"
    }
  ],
  "edges": [
    {
      "id": "edge1",
      "fromNode": "node1",
      "toNode": "node2",
      "fromSide": "right",
      "toSide": "left",
      "label": "contradicts"
    }
  ]
}
```

Node types: `text` (containing markdown), `file` (embedding a vault note), `link` (URL), `group` (visual container for other nodes).

Edges connect nodes and can have labels. All elements have spatial coordinates and dimensions.

### 7.2 How the AI Reads the Canvas

The context assembly layer serializes the canvas intelligently for the LLM:

- **Full content** for nodes the user is currently interacting with or recently modified
- **Summaries or titles only** for distant or stable nodes
- **Edge structure** always included to preserve relationship information
- **Spatial clustering** detected from node positions — groups of nearby nodes treated as related

This "zoom in on active area, zoom out on the rest" approach manages context window usage while preserving the structural information the LLM needs to reason about the canvas.

### 7.3 How the AI Modifies the Canvas

The backend modifies the canvas by writing to the `.canvas` JSON file. Obsidian live-reloads the changes.

Operations the AI can perform:

- **Add text nodes** — question cards, challenge cards, suggestion cards
- **Add file nodes** — embedding relevant source notes onto the canvas
- **Create edges** — connecting related or contradictory ideas, labeling relationships
- **Create groups** — clustering related nodes into visual containers

**Spatial placement heuristic:** When adding nodes, find the bounding box of existing content and place new nodes in nearby open space, adjacent to the most relevant existing node. Not perfect (user will rearrange), but better than random placement or overlap.

### 7.4 Self-Critique of Canvas Interaction

Modifying the canvas JSON while the user is actively working on it creates a potential race condition: the user moves a node, the backend writes a new node, the user's change gets overwritten or the layout jumps unexpectedly. Obsidian's live-reload may handle this gracefully, or it may not — this needs testing.

A safer pattern might be: the AI _proposes_ canvas modifications in the chat sidebar ("I'd like to add a question card challenging your argument about X — shall I add it to the canvas?") and only writes to the canvas on confirmation. This is less fluid but avoids surprising the user with unexpected canvas changes. Over time, if users develop trust, they can enable "auto-add to canvas" for specific skills.

---

## 8. Reference Document Management

### 8.1 The Problem

Users upload documents (PDFs, articles, datasets) that the AI should use as a basis for challenging, guiding, or enriching the user's thinking. The system needs to: get these documents into Obsidian, make them readable by the LLM, let the user control which documents are active, and let different skills use documents in different ways.

### 8.2 Vault Structure for Sources

```
vault/
├── projects/
│   └── my-analysis/
│       ├── draft.md              ← user's working note
│       ├── canvas.canvas         ← project canvas
│       └── ...
├── sources/
│   ├── research-paper.pdf        ← original file
│   ├── research-paper.md         ← extracted companion note
│   ├── dataset-report.pdf
│   ├── dataset-report.md
│   └── ...
├── artifacts/
│   ├── questions/
│   ├── reflections/
│   ├── syntheses/
│   └── ...
├── skills/
│   ├── socratic-questioner.md
│   ├── devils-advocate.md
│   └── ...
└── .tft/
    └── config.md                 ← system configuration
```

### 8.3 Document Processing Pipeline

When a document is placed in the `sources/` folder:

1. **File watcher detects** the new file
2. **Text extraction** runs (PyMuPDF/pdfplumber for PDFs, direct read for markdown/text)
3. **Companion note created** — `source-paper.md` with:
   - Extracted text content
   - YAML frontmatter: `type: source`, `original: source-paper.pdf`, `date-added: ...`, `status: active`
   - Link back to original file
4. **Vector store updated** — companion note content is chunked and indexed for semantic search
5. **Obsidian displays** the new companion note (live reload)

### 8.4 How the LLM Knows Which Documents to Use

Three complementary mechanisms, from most to least explicit:

**Explicit linking (highest priority):** The user references sources with internal links in their working note or in chat: "I'm working with `[[research-paper]]` and `[[dataset-report]]`." The context assembly layer sees these links and includes those notes in the LLM context.

**Canvas proximity (medium priority):** If source documents appear as nodes on the active canvas, they're treated as relevant context. Anything on the canvas is part of the working set.

**Project structure (lowest priority):** Sources in the same project folder, or tagged with the same project tag, are included if context window allows. Frontmatter can reinforce this: `project: my-analysis`, `role: active-source`.

**Semantic retrieval (on-demand):** When the active skill needs to reference source material (e.g., the devil's advocate looking for contradictions), it queries the vector store for passages relevant to the user's current claims. This handles the case where the relevant passage is buried in a long document the user linked but hasn't fully engaged with.

### 8.5 How Different Skills Use Sources

| Skill                      | Source Usage Pattern                                                                          |
| -------------------------- | --------------------------------------------------------------------------------------------- |
| **Socratic Questioner**    | Pulls specific claims from sources to formulate questions the user must reason about          |
| **Devil's Advocate**       | Finds contradictions between the user's draft and source material; surfaces opposing evidence |
| **Synthesis Helper**       | Identifies themes, agreements, and tensions across multiple sources                           |
| **Structured Facilitator** | Uses sources to suggest organizational frameworks for the user's thinking                     |
| **Reflective Prompter**    | References sources the user hasn't engaged with, asking why they were included or excluded    |

### 8.6 Self-Critique of Document Management

The companion-note approach creates duplication — the PDF and its extracted markdown. If the original is updated, the companion note becomes stale. A watcher for file modifications (not just creation) is needed, or a clear convention that companion notes are regenerated on demand.

The vector store adds operational complexity (indexing, chunking strategy, embedding model choice). For a first version, it might be simpler to rely on explicit linking and canvas proximity alone, and only add semantic retrieval when the user's source library grows large enough that manual linking becomes burdensome. Start simple, add sophistication when the need is demonstrated.

Additionally, the current design assumes the user places documents in a specific folder. Some users won't do this — they'll dump files anywhere or link to external URLs. The system should be flexible about source location and offer a convention, not enforce one.

---

## 9. Backend Architecture: Build vs. Compose

### 9.1 The Decision

Should we build a custom agent harness from scratch, or compose existing frameworks and services?

### 9.2 What the Backend Actually Needs to Do

Stripped of terminology, the backend does four things:

1. **Receives signals** from the Obsidian plugin (user typed, switched notes, sent a message)
2. **Decides how to respond** (which skill is active, is a checkpoint needed, what context to include)
3. **Calls an LLM** with the right prompt and tools
4. **Writes back** to the vault and the chat

### 9.3 Options Considered

#### Option 1: Claude API with Tool Use + Simple Server

The minimalist approach. No agent framework at all.

**How it maps to our architecture:**

- **Skills** → System prompt templates. Each skill is a system prompt defining the conversational stance. Skill switching = swapping the system prompt on the next LLM call.
- **Vault interactions** → Tool definitions. Tools like `create_note`, `read_note`, `modify_canvas`, `search_vault`, `add_callout`. Claude calls them; the backend executes against the filesystem.
- **Orchestration** → Conversation state + pre-processing logic. A simple state machine checks conditions before each LLM call and injects instructions or switches skills as needed.
- **Stack:** FastAPI or Express server, Anthropic SDK, system prompt templates, tool handler functions, a lightweight state object per session.

**Strengths:** Simplest possible architecture. No framework lock-in. Full control. Easy to understand and debug. Can start building immediately.

**Weaknesses:** State management and skill-switching logic are handwritten. As orchestration grows complex (multi-step tool chains, conditional branching), you're reimplementing what frameworks provide.

**Consequence for final product:** Clean and understandable, but may accumulate accidental complexity as the system grows. Good for prototyping; may need refactoring for production.

#### Option 2: MCP (Model Context Protocol) ✅

Anthropic's protocol for connecting AI models to external data and tools. An MCP server exposes tools and resources that Claude can use.

**How it maps to our architecture:**

- **Vault interactions** → MCP server tools: `read_note`, `create_note`, `search_vault`, `read_canvas`, `modify_canvas`, `list_sources`, `get_project_context`.
- **Source documents** → MCP resources: vault contents exposed as readable context. Active note, canvas state, and source documents are resources that update dynamically.
- **Skills + Orchestration** → Live in the client layer as system prompts and conversation management (not in the MCP server).
- Existing community filesystem MCP servers can be used as a starting point and extended.

**Strengths:** Clean separation between vault logic and AI logic. Reusable across different clients. Aligns with Anthropic's ecosystem direction. Good composability if other MCP servers are added later (web search, databases).

**Weaknesses:** MCP is still relatively early-stage. Doesn't solve orchestration or skill management — those still need a client-side implementation. Adds an architectural layer (plugin → client → MCP server → vault). Learning curve for the protocol.

**Consequence for final product:** Well-separated concerns, but the orchestration and skill logic still need to be built somewhere. MCP handles the "how do I talk to the vault" problem elegantly but doesn't address the "how do I manage cognitive flow" problem.

#### Option 3: LangGraph

Python framework for graph-based agent orchestration. Nodes are processing steps, edges are conditional transitions.

**How it maps to our architecture:**

- **Orchestration** → LangGraph's core strength. The cognitive checkpoint logic maps naturally to graph nodes and conditional edges.
- **Skills** → Could be implemented as node configurations within the graph.
- **Multi-step reasoning** → If the AI needs to read multiple sources, compare them, and then produce a structured challenge, LangGraph handles that chain well.

**Strengths:** Excellent orchestration primitives. Good for complex multi-step reasoning flows. Built-in persistence and checkpointing. Active development and community.

**Weaknesses:** Python-only (Obsidian plugin is TypeScript — language mismatch). Heavier than needed for simple state management. Framework lock-in. If most AI turns are single-shot (receive context, respond), LangGraph is overhead.

**Consequence for final product:** Powerful if orchestration logic becomes genuinely complex (multi-step agentic flows with branching). Overkill if orchestration is mostly "check a few conditions, select a skill, occasionally inject a checkpoint." The Python/TypeScript split adds deployment complexity.

#### Option 4: Vercel AI SDK or Mastra (TypeScript ecosystem)

TypeScript-native frameworks for AI application development.

**Vercel AI SDK:** Streaming, tool use, conversation management. Thin — doesn't impose orchestration structure.

**Mastra:** More full-featured. Built-in concepts for tools, workflows, and memory. Closer to a complete agent harness.

**Strengths:** TypeScript throughout (matches Obsidian plugin). Vercel gives flexibility; Mastra gives more structure. Active communities.

**Weaknesses:** Less mature than Python ecosystem for agent tooling. Mastra is relatively new and may have instability or breaking changes.

**Consequence for final product:** Keeps the codebase in a single language, which reduces friction. Mastra's workflow concept could map to the orchestration layer. But betting on a young framework carries risk.

### 9.4 The Recommended Stack ✅

After evaluating all options, the recommended approach is a **composition of specific, well-scoped tools** rather than a single framework:

| Component            | Implementation                  | Rationale                                                                                                                      |
| -------------------- | ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **LLM Interface**    | Anthropic SDK (TypeScript)      | Direct, no wrapper overhead. Claude's native tool use is the skill execution mechanism.                                        |
| **Vault Operations** | MCP Server (TypeScript)         | Clean encapsulation of all Obsidian interaction. Start from community filesystem MCP server, extend with vault-specific tools. |
| **Skills**           | Markdown files in the vault     | Human-readable, user-editable. Backend reads the active skill file and constructs the system prompt.                           |
| **Orchestration**    | Simple TypeScript state machine | Tracks current skill, turn count, activity patterns, checkpoint triggers. No framework — a single class with explicit rules.   |
| **Source Retrieval** | Local vector store (LanceDB)    | TypeScript client. Indexes extracted source content. Queried when skills need to reference source material.                    |
| **Plugin**           | Obsidian TypeScript plugin      | Sidebar chat, event monitoring, context relay to backend. Optional: callout injection.                                         |
| **Server**           | Express or Fastify              | Receives plugin events, coordinates orchestration/skills/LLM/vault operations.                                                 |

**Why this composition:**

- **All TypeScript** — single language for plugin, server, MCP server, skills processing
- **No heavy frameworks** — each piece is small, well-scoped, replaceable
- **MCP for vault ops** — clean separation, reusable, extensible
- **Skills as files** — transparent, editable, versionable
- **Orchestration as a class** — simple, explicit, testable (if it fits on one page, it's right-sized)
- **Vector store only when needed** — defer until source library size demands it

### 9.5 Self-Critique of the Recommended Stack

**On avoiding frameworks:** The "no framework" philosophy is principled but may lead to reinventing wheels. As the system grows, the handwritten state machine may need persistence (surviving server restarts), concurrency handling (multiple files changing at once), and error recovery. These are exactly the features frameworks like LangGraph provide. Monitor for the moment when the handwritten approach becomes a liability and be willing to adopt a framework then — don't let "we don't need a framework" become dogma.

**On MCP:** Recommending MCP creates a dependency on a protocol that's still evolving. If Anthropic changes MCP significantly, or if you later want to use a non-Anthropic model, the MCP server may need reworking. Mitigate by keeping the MCP server thin — it should expose vault operations, not contain business logic. The vault manipulation functions underneath should be callable directly as well as through MCP.

**On skills as markdown files:** This is elegant but creates a prompt engineering challenge. Each skill needs to be written carefully enough that the LLM consistently follows it, which requires iteration. Poor skill definitions will produce inconsistent behavior. Consider a testing framework for skills — feed a skill a known scenario and verify the LLM's response follows the skill's rules.

**On LanceDB:** A local vector store is operationally simpler than hosted alternatives, but embedding quality depends on the model used for embedding. If embeddings are poor, semantic retrieval will return irrelevant passages, and the AI will make bad challenges based on bad context. Test retrieval quality early with real documents.

---

## 10. Interactivity Within Obsidian: Achievable Patterns

### 10.1 The Core Concern

The envisioned interaction — AI proactively asking questions, challenging arguments, surfacing contradictions while the user writes — requires real-time, editor-integrated, proactive engagement. This is the hardest pattern to achieve within Obsidian.

### 10.2 Achievable Patterns (ordered by implementation difficulty)

#### Pattern A: Sidebar Chat Panel (Low difficulty)

Plugin adds a chat sidebar. As the user writes, the plugin monitors changes (debounced) and sends context to backend. AI responses appear in the sidebar.

**Experience:** A thinking partner sitting beside you. Glance over, engage, continue.

**Limitation:** AI reacts in a separate panel, not in the writing flow. Pull-adjacent rather than push.

#### Pattern D: Companion Note (Low difficulty)

AI maintains a separate note that updates as the user writes. Contains running questions, observations, challenges. User opens it in a split pane.

**Experience:** AI's thinking visible in its own space. User consults when they want.

**Limitation:** Less integrated. User might ignore it.

#### Pattern B: Inline Callout Injection (Medium difficulty)

Plugin inserts Obsidian callout blocks directly into the user's note:

```markdown
> [!question] Challenge from AI
> You claim X, but [[source-doc]] suggests Y.
> How do you reconcile this?
```

**Experience:** Closest to proactive pop-up vision. Challenges appear in writing context.

**Limitation:** Insertion timing must be calibrated to avoid disrupting flow. Needs debouncing and user-configurable triggers.

#### Pattern C: Canvas-Based Interaction (Medium difficulty)

User works on Canvas. AI adds question/challenge cards connected to draft sections.

**Experience:** Spatially interactive. Thinking landscape evolves collaboratively.

**Limitation:** Writing inside canvas cards is more constrained than the full editor.

### 10.3 Recommended Implementation Order

1. **Start with Pattern A + D** — sidebar chat + companion note. Easiest to build, validates concept.
2. **Add Pattern B** — inline callouts. Once user behavior is understood (when they want intervention, what triggers are useful).
3. **Use Pattern C** — canvas interaction. For specific phases (exploration, organization, synthesis), not as the primary writing environment.

### 10.4 Consequence for the Final Product

The initial product will feel more like "a thoughtful companion that maintains running dialogue" than "an AI that intervenes in real time as you type." This is not necessarily worse — it respects focus and flow while keeping scaffolding available. The paper's adoption theme warns that too much friction causes rejection. A companion that's available but doesn't interrupt may be more adoptable than one that constantly challenges.

However, Pattern B (inline callouts) is likely where the real TfT value lives — the AI surfacing a contradiction _in context_ while you're making the argument is qualitatively different from seeing it in a sidebar. Prioritize getting to Pattern B quickly.

---

## 11. Complete Architecture (Synthesized)

### 11.1 System Diagram

```
┌──────────────────────────────────────────────────────────────┐
│  OBSIDIAN (User-Facing Layer)                                │
│                                                              │
│  ┌──────────┐  ┌──────────┐  ┌──────────────────────┐       │
│  │  Editor   │  │  Canvas   │  │  Graph View          │       │
│  │  (notes)  │  │  (spatial)│  │  (structure visible)  │       │
│  └────┬─────┘  └────┬─────┘  └──────────────────────┘       │
│       │              │                                        │
│  ┌────┴──────────────┴──────────────────────────────┐        │
│  │  OBSIDIAN PLUGIN (Bridge Layer)                   │        │
│  │                                                   │        │
│  │  • Sidebar chat panel (command channel)            │        │
│  │  • Editor event monitoring (work channel signals)  │        │
│  │  • Canvas state relay (collaboration channel)      │        │
│  │  • Session context assembly & transmission         │        │
│  │  • Optional: inline callout injection              │        │
│  │  • Optional: companion note management             │        │
│  └────────────────────┬─────────────────────────────┘        │
└───────────────────────┼──────────────────────────────────────┘
                        │ HTTP/WebSocket
                        ▼
┌───────────────────────────────────────────────────────────────┐
│  BACKEND SERVER (Express/Fastify — TypeScript)                │
│                                                               │
│  ┌─────────────────────────────────────────────────────┐      │
│  │  Working Memory (per session)                       │      │
│  │  current_skill, turns_since_checkpoint,             │      │
│  │  recent_files, focus_topic, source_engagement,      │      │
│  │  artifact_history, canvas_summary                   │      │
│  └──────────────────────┬──────────────────────────────┘      │
│                         │                                     │
│  ┌──────────────────────▼──────────────────────────────┐      │
│  │  Orchestration Layer (lightweight state machine)     │      │
│  │  • Evaluates: checkpoint due? skill transition?      │      │
│  │  • Reads: working memory + session context           │      │
│  │  • Outputs: skill selection, checkpoint injection,   │      │
│  │    transition suggestion                             │      │
│  │  • Rules fit on one page or they're too complex      │      │
│  └──────────────────────┬──────────────────────────────┘      │
│                         │                                     │
│  ┌──────────────────────▼──────────────────────────────┐      │
│  │  Skill Layer                                        │      │
│  │  • Reads active skill file from vault /skills/      │      │
│  │  • Constructs system prompt from skill definition    │      │
│  │  • Defines available tools for this skill            │      │
│  │  • Shapes LLM behavior: role, withholding, artifacts │      │
│  └──────────────────────┬──────────────────────────────┘      │
│                         │                                     │
│  ┌──────────────────────▼──────────────────────────────┐      │
│  │  LLM Call (Anthropic SDK — Claude with tool use)    │      │
│  │  • System prompt from active skill                   │      │
│  │  • Context from context assembly                     │      │
│  │  • Tools from MCP server                             │      │
│  │  • Orchestration instructions (if checkpoint due)    │      │
│  └──────────────────────┬──────────────────────────────┘      │
│                         │                                     │
│  ┌──────────────────────▼──────────────────────────────┐      │
│  │  Response Router                                    │      │
│  │  • Chat text → sidebar via plugin                    │      │
│  │  • Tool calls → MCP server (vault operations)        │      │
│  │  • Artifact metadata → artifact store                │      │
│  └─────────────────────────────────────────────────────┘      │
│                                                               │
├───────────────────────────────────────────────────────────────┤
│  MCP SERVER (Vault Operations — TypeScript)                   │
│                                                               │
│  Tools:                    Resources:                         │
│  • create_note             • active_note (dynamic)            │
│  • read_note               • canvas_state (dynamic)           │
│  • modify_note             • source_documents (dynamic)       │
│  • search_vault            • project_context (dynamic)        │
│  • read_canvas                                                │
│  • modify_canvas                                              │
│  • add_callout                                                │
│  • list_sources                                               │
│  • get_project_context                                        │
│                                                               │
│  All operations execute against the vault filesystem.         │
│  Functions are callable both through MCP and directly.        │
├───────────────────────────────────────────────────────────────┤
│  VECTOR STORE (LanceDB — deferred until needed)               │
│                                                               │
│  • Indexes extracted source document content                  │
│  • Queried by skills that need specific source passages       │
│  • Updated when new sources are added to the vault            │
│  • TypeScript client                                          │
├───────────────────────────────────────────────────────────────┤
│  ARTIFACT STORE (lightweight — JSON or SQLite)                │
│                                                               │
│  • Logs all AI-generated artifacts                            │
│  • Tracks: content, creation context, producing skill,        │
│    relationships, position in thinking trail                  │
│  • Feeds back into context assembly for continuity            │
│  • Enables "thinking trail" reconstruction                    │
└───────────────────────────────────────────────────────────────┘
```

### 11.2 Data Flow (Detailed)

1. **User acts** in Obsidian — writes in editor, arranges canvas, sends chat message.
2. **Plugin captures** the event and updates the session context (active file, content/diff, activity type).
3. **Plugin sends** session context to the backend server (HTTP/WebSocket).
4. **Backend updates working memory** — accumulates activity patterns, updates counters.
5. **Orchestration evaluates** — checks: is a cognitive checkpoint due? Should a skill transition be suggested? Any rules triggered by the current working memory state?
6. **Skill layer activates** — reads the current skill file from the vault's `/skills/` folder. Constructs the system prompt and available tool set.
7. **Context assembly** — reads the active note content (from the session context), queries the MCP server for linked notes/canvas state/source documents, optionally queries the vector store for relevant source passages. Constructs the LLM-ready context payload.
8. **LLM call** — Anthropic SDK sends: system prompt (from skill), user context (from assembly), tool definitions (from MCP server), optional orchestration injection ("it's time for a reflection checkpoint").
9. **LLM responds** — returns text (for the chat) and/or tool calls (for vault operations).
10. **Response router distributes** — chat text goes back to the plugin for sidebar display. Tool calls go to the MCP server for execution (creating notes, modifying canvas, injecting callouts). Artifact metadata goes to the artifact store.
11. **MCP server executes** vault operations — writes files, modifies canvas JSON, updates frontmatter.
12. **Obsidian live-reloads** — user sees new artifacts, canvas changes, callouts appear.
13. **Artifact store logs** what was created, by which skill, in what context. This feeds back into future context assembly.

### 11.3 Vault Interaction Patterns by Skill

| Skill                      | Chat Behavior                                                                             | Vault Behavior                                                            | Source Usage                                               |
| -------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ---------------------------------------------------------- |
| **Socratic Questioner**    | Asks probing questions. Never gives direct answers until user articulates their position. | Creates `type: question` notes linked to user's working note.             | Pulls specific claims from sources to formulate questions. |
| **Devil's Advocate**       | Challenges assertions. Surfaces contradictions.                                           | Creates `type: counterargument` notes. Injects challenge callouts inline. | Finds contradictions between draft and source material.    |
| **Structured Facilitator** | Suggests organizational frameworks. Offers structure.                                     | Creates outline notes. May scaffold a canvas with zones.                  | Uses sources to suggest relevant frameworks.               |
| **Synthesis Helper**       | Helps weave together multiple threads.                                                    | Creates `type: synthesis` notes referencing multiple sources.             | Identifies themes, agreements, tensions across sources.    |
| **Reflective Prompter**    | Asks user to step back and assess their own thinking.                                     | Creates `type: reflection` notes at checkpoints.                          | References sources user hasn't engaged with.               |

---

## 12. Intermediary Artifact Design

### 12.1 Properties of Good Intermediary Artifacts

Drawing from the paper's framework (Rogers et al. 2025), intermediary artifacts should be:

| Property                 | What It Means                                           | How Obsidian Enables It                                    |
| ------------------------ | ------------------------------------------------------- | ---------------------------------------------------------- |
| **Composable**           | Can be combined, merged, fed into later thinking stages | Internal links, note embedding, Dataview queries           |
| **Exportable**           | Can be pulled out as standalone deliverables            | Already markdown files — portable by nature                |
| **Referenceable**        | AI can point back to them in later conversation         | Internal links + frontmatter metadata                      |
| **Visible**              | User can see the structure of their thinking            | Graph view, canvas spatial layout                          |
| **Owned**                | User controls, edits, reorganizes freely                | Local files — no proprietary lock-in                       |
| **Useful in themselves** | Not busywork — genuinely help the user                  | Must be well-written, well-linked, containing real insight |

### 12.2 Artifact Types and Their Vault Representation

| Artifact Type     | Vault Representation                             | Frontmatter Tags                                                    |
| ----------------- | ------------------------------------------------ | ------------------------------------------------------------------- |
| Question          | Markdown note with the question and context      | `type: question`, `status: open/resolved`, `source-skill: socratic` |
| Counterargument   | Note linked to the claim it challenges           | `type: counterargument`, `challenges: [[claim-note]]`               |
| Comparison table  | Markdown table or canvas with side-by-side cards | `type: comparison`, `items: [A, B, C]`                              |
| Reflection prompt | Note with questions for the user to fill in      | `type: reflection`, `checkpoint: true`, `phase: exploration`        |
| Concept map       | Canvas file with linked concept nodes            | `type: concept-map`, `topic: X`                                     |
| Synthesis         | Note that weaves together multiple sources       | `type: synthesis`, `sources: [[note1]], [[note2]]`                  |
| Thinking trail    | Auto-generated log of the cognitive journey      | `type: trail`, `session: YYYY-MM-DD`                                |

### 12.3 Self-Critique of Artifact Design

There's a risk of **artifact pollution** — the AI creates so many notes, questions, and reflections that the vault becomes cluttered and the user stops engaging with them. Each artifact that goes unread undermines the system's value and trains the user to ignore future artifacts.

Mitigation: artifacts should be few and high-quality. The skill definition should specify not just _what_ artifacts to create but _how many_ and _when_. A Socratic skill that generates five questions after every paragraph will be ignored. One well-timed, incisive question after a significant writing milestone is powerful.

Also consider **artifact lifecycle**: questions that get resolved should be marked as such (frontmatter `status: resolved`). Artifacts that the user never engages with should eventually be surfaced as a meta-reflection: "I created several questions you haven't addressed — are they relevant, or should we move on?"

---

## 13. Development Paths and Migration Strategy

### Path A: Obsidian-Native ✅ (Chosen starting point)

Build an Obsidian plugin + backend service. Accept sidebar-plus-callouts interaction model.

**Scope:** Plugin (sidebar chat, file monitoring, callout injection), backend (context assembly, orchestration, skills, vault writer via MCP server).

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

Start with Path A. Learn what works. Graduate to Path B by building a custom editor that shares the Obsidian vault as a backend. The vault structure, artifact format, skill definitions, MCP server, backend intelligence — all carry forward. Only the interaction surface changes.

**What carries forward across paths:** Vault structure and conventions, skill definitions (markdown files), MCP server and vault operations, backend orchestration logic, artifact store and metadata, vector store indexes.

**What changes:** The plugin/editor component and how it relays context to the backend.

---

## 14. Honest Assessment: Risks and Unknowns

### 14.1 Technical Risks

| Risk                                                                             | Likelihood | Impact                                    | Mitigation                                                                                           |
| -------------------------------------------------------------------------------- | ---------- | ----------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Obsidian Canvas JSON race conditions when both user and AI modify simultaneously | Medium     | Medium — layout jumps, lost changes       | AI proposes changes in chat, writes on confirmation; or write during detected pauses                 |
| Context window overflow with large vaults/many sources                           | High       | High — degraded AI reasoning              | Aggressive context scoping, summarization of distant content, vector retrieval for specific passages |
| Skills producing inconsistent LLM behavior                                       | Medium     | Medium — unreliable cognitive scaffolding | Skill testing framework, iteration on prompt wording, evaluation suite                               |
| Obsidian plugin API breaking changes                                             | Low-Medium | High — integration breaks                 | Pin Obsidian version, minimize API surface usage, keep plugin thin                                   |
| MCP protocol changes                                                             | Low        | Medium — refactoring needed               | Keep MCP server thin, maintain direct-callable functions underneath                                  |

### 14.2 Conceptual Risks

| Risk                                           | Description                                                                    | Mitigation                                                                                                                               |
| ---------------------------------------------- | ------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Users disable the friction**                 | Users weaken skills or skip checkpoints because they want faster outputs       | Core rules in skills with explanations of why they exist; track cognitive outcomes to show value                                         |
| **The companion model isn't different enough** | Without rich inline intervention, this feels like "ChatGPT in a sidebar"       | Prioritize getting to Pattern B (inline callouts) quickly; the vault integration and artifact creation must provide visible unique value |
| **Artifact pollution**                         | Too many AI-generated notes clutter the vault                                  | Few, high-quality artifacts with lifecycle management                                                                                    |
| **Over-engineering before validation**         | Building sophisticated orchestration before knowing if the basic concept works | Start with one skill, one interaction pattern. Add complexity only when validated.                                                       |

### 14.3 The Biggest Unknown

Whether the fundamental premise works in practice: will users actually engage with cognitive scaffolding in a real workflow, or will they route around it to get outputs faster? The paper identifies this as the core adoption challenge, and no amount of architecture can answer it — only building and testing will. This is the strongest argument for Path A: get something in front of users as quickly as possible and learn.

---

## 15. Open Questions and Next Steps

### Immediate (for Path A implementation)

1. **Skill definition schema:** What does a skill file look like? What fields does the YAML frontmatter need? How is the behavioral prompt structured in the markdown body?

2. **Plugin architecture:** How does the Obsidian plugin connect to the backend? WebSocket for real-time context relay, or HTTP polling? How is the sidebar chat rendered?

3. **MCP server design:** What are the exact tool signatures for vault operations? How is canvas JSON manipulation handled?

4. **First skill to build:** Which skill provides the most value for the least complexity? (Likely: Socratic Questioner or Devil's Advocate — both create high-value interventions with relatively simple behavioral rules.)

### Deferred (for after initial validation)

5. **Context assembly optimization:** Efficient vault context scoping, summarization strategies, vector store integration.

6. **Orchestration refinement:** What checkpoint rules actually work? This requires user data.

7. **Evaluation framework:** How to measure whether the system protects/augments cognition. Aligned with the paper's three outcome types.

8. **Canvas interaction sophistication:** Spatial placement algorithms, canvas-as-collaboration-surface patterns.

9. **Multi-user / team scenarios:** The paper discusses organizational adoption. Does the system support shared vaults?
