---
tags:
  - prototype
  - use-case
  - brainstorm
status: exploratory
---
## Possibly interesting stuff - collection
> “its impact on learning is more complex. Studies show that using LLMs for direct solutions can impair learning, whereas using them for explanation-seeking can be beneficial [8]. This can be further complicated by a perception-performance paradox, where students may perceive LLMs as more helpful than traditional study methods, such as note-taking, even when their learning outcomes are worse [6]. On the other hand, if designed and used in meaningful  ways, there is much potential for cognitive augmentation. For example, AI assistance can enhance skill development by providing high-quality, personalised examples, acting as a powerful learning aid [9].” Yellow Highlight [Page 2](zotero://open-pdf/library/items/MQYNRQBP?page=2&annotation=XLDP7AS9)

This first source could also be of particular interest regarding my note taking assistant idea and should be read. 

The second one is directly tied to how note taking and the perception-performance paradox and should definitely be read

The third one may show me possible augmentation strategies



# Note Augmentation — Use Case Exploration

_A brainstorm capture from working through the CHI 2025 TfT synthesis paper. This explores an alternative (or complementary) use case for the prototypical validation — applying the Role → Strategy → Cognitive Function framework to post-lecture note-taking and consolidation._

---

## The Use Case

A student has attended a lecture and wants to consolidate their understanding by working through the lecture material and writing study notes. These notes will become their primary study resource for exam preparation, largely replacing the original lecture slides.

The core problem: most students produce notes that are compressed, reorganized versions of the lecture material — summaries that could be interchanged with any other student's notes without much loss (like pre-made notes on platforms like Studydrive). These notes represent the *lecture's* structure, not the *student's* mental model. The cognitive work of summarizing feels productive but often stays at the level of recording rather than understanding.

The system's goal: nudge the student from producing generic summaries toward producing notes that represent their *individual mental model* — enriched with their own examples, cross-connections to other material, transfer applications, resolved confusions, and reasoning about *why* things work, not just *what* they are.

---

## Why This Use Case Fits the Thesis

The cognitive protection argument is airtight here. With knowledge synthesis for a research paper, you could argue the final written product is what matters and AI help is acceptable. With learning, the cognitive process *is the entire point* — if the student offloads understanding to AI, they've defeated the purpose completely. There is no "but the output was good" escape hatch.

This also maps cleanly to the framework:

- **AI Roles** → Connection Facilitator, Socratic Questioner, Transfer Prompter, Depth Challenger
- **Strategies** → indirect connection prompting, Feynman-style explanation requests, probing follow-up questions, example generation challenges
- **Cognitive Functions** → relational reasoning, transfer, self-explanation, retrieval practice, elaboration

The anchoring theories from the thesis spec apply directly:

- **Desirable Difficulties (Bjork)** — the system deliberately makes note-taking harder in specific ways that improve learning
- **Productive Failure (Kapur)** — the student attempts to generate examples or connections before receiving help
- **Scaffolding (Vygotsky/ZPD)** — the system adapts the difficulty of its prompts to the student's demonstrated level of understanding

---

## The Workflow

**What the student brings:** Lecture slides/notes uploaded as source material.

**Assumption:** The student works through lectures sequentially and creates note documents that correspond to sections of the lecture. This gives the system a clean context model — it always knows what the student has already worked through.

**Activity:** The student reads through a section of the lecture material and writes their own summary notes for that section. When they finish a section, they submit it to the system. The system compares their notes against the source material and responds with a small set of targeted interventions. The student engages with those, updates their notes, and moves on to the next section.

**Turn-based, not real-time:** The student controls the pace. The system intervenes only when explicitly asked to review a section. This eliminates the need for real-time editor monitoring, debouncing heuristics, and proactive timing decisions. The engineering simplifies dramatically while preserving the cognitive scaffolding value.

---

## Context Scope — Open Decision

Two options with different tradeoffs:

**Option A: Single-lecture scope.** The system only knows about the current lecture's source material and the student's notes for this lecture. Simplest to implement. The system can still ask depth and transfer questions within the lecture, but cannot surface cross-lecture connections.

**Option B: Cumulative scope.** The system has access to all previous lecture materials and the student's notes for those lectures. This enables cross-lecture connection prompts ("You're describing a speed-memory tradeoff here — have you encountered a similar tradeoff earlier in the course?"). More powerful for learning, but introduces context management complexity — the system needs to decide which prior material is relevant.

For the prototype, Option A is safer. Option B is where the real pedagogical value lies (cross-lecture connections are exactly the kind of transfer that separates surface learning from deep learning) but may require more careful engineering. This decision can be deferred until the single-lecture version is working.

---

## Three Intervention Types

Rather than many skill types, the prototype needs three core intervention types. Each directly prevents the "generic summary" failure mode:

### 1. Connection Prompt
Surfaces potential links to other concepts — *without naming the connection explicitly*. The student must search their own knowledge to find it.

- **Prevents:** Isolated concept notes with no relational structure.
- **Example:** "You're describing a speed-memory tradeoff here. Have you encountered a similar tradeoff earlier in the course?" (NOT: "This relates to the array vs. linked list discussion from Lecture 3 — you should link these.")
- **Cognitive function activated:** Relational reasoning — seeing structural similarities across contexts.
- **Key design principle:** The prompt hints that a connection exists without giving it away. If the student finds it, the resulting link represents genuine understanding. If they can't, that's a diagnostic signal.

### 2. Transfer Prompt
Asks the student to generate their own examples, analogies, or applications.

- **Prevents:** Notes that contain only lecture-provided examples (interchangeable with any other student's notes).
- **Example:** "You've described how gradient descent works using the lecture's hill analogy. Can you think of a situation from your own experience where you'd apply this kind of iterative optimization?"
- **Cognitive function activated:** Transfer, elaboration, self-explanation (Feynman technique — explain it to the agent).
- **Key design principle:** Student-generated examples are more memorable and indicate deeper understanding, but the system should probe them with follow-up questions to catch confident misunderstandings rather than validating correctness directly.

### 3. Depth Prompt
Pushes the student below surface-level descriptions into reasoning about mechanisms and edge cases.

- **Prevents:** Notes that describe *what* without explaining *why* or *when it breaks*.
- **Example:** "You wrote that hash collisions are 'handled by chaining.' What happens to lookup performance when many keys hash to the same bucket? How does this relate to the O(1) claim you wrote earlier?"
- **Cognitive function activated:** Analytical reasoning, critical evaluation of own claims.

---

## The Role of Obsidian's Graph

The graph structure should emerge from the student's linking behavior, not be enforced by the system. No rigid vault hierarchy is imposed.

**Why the graph matters:** A summary is linear — it follows the lecture's organization. A mental model is a graph — concepts connect to other concepts, examples connect to principles, questions connect to gaps. If the system encourages students to create `[[links]]` between concept notes (via connection prompts), then the vault's graph view literally *becomes a visualization of the student's mental model*. You can see clusters (well-understood areas), orphan nodes (isolated concepts), and dense cross-linking (deep understanding).

**Lecture structure should not be destroyed.** Students legitimately need lecture-sequential navigation for reference ("Where did the professor discuss hash collisions?"). The lecture's original sequence should remain navigable — but it should not be the *only* organizational structure. The graph provides a second, personal, cross-cutting view that the linear sequence cannot.

**The linking itself is a cognitive act.** Creating a link between "Hash Tables" and "Array Tradeoffs" requires the student to *recognize the structural similarity*. The system's job is to prompt the student toward this recognition without naming it.

---

## Design Strategy: Ephemeral Answer Panel

When the student is genuinely stuck and needs help, the system should not refuse — but the *form* of help matters. One idea: the system shows an explanation or answer in a viewing context that is separate from the notepad. When the student returns to their notes, the answer is no longer visible. The student must *reconstruct* the answer from their own understanding to write it into their notes.

This is a desirable difficulty implemented at the interface level. The system helps without enabling copying. The act of reconstructing something you just saw — even seconds ago — is a fundamentally different cognitive operation than copying it. That's retrieval practice built into the interaction design.

This is a transversal pattern — any skill/intervention type could use this mechanism.

---

## Open Research Areas

### Interaction Modality Beyond Chat

The current design assumes the chat sidebar is the primary channel for AI-student interaction. This may be insufficient or suboptimal. Open questions:

- Is a chat interface the right modality for cognitive interventions during note-taking, or does it create an awkward context switch between writing and conversing?
- Could interventions appear inline in the note (as callout blocks), in a companion panel, or as annotations on the source material?
- How does the interaction modality affect the student's cognitive engagement with the intervention? (A question in chat might feel like a separate task; a question that appears in the margin of their notes might feel integrated into the workflow.)
- What would a "non-chat" interaction look like? Could the system surface prompts as placeholder blocks in the note that the student fills in? Could it highlight sections of the lecture material that the student hasn't addressed?
- Reference: Zindulka et al. (2025) from the synthesis paper argue that direct manipulation can ease cognitive load and free resources for higher-level thinking. How might this apply here?

This is an important design dimension that should be explored rather than defaulted to chat.

### Real-Time Engagement Monitoring (Deferred Extension)

The current simplified design is turn-based — the student explicitly submits sections for review. A more ambitious version would monitor engagement quality in real-time:

- Detect when the student is copying verbatim from lecture slides (compare note content against source material).
- Detect prolonged pauses that might indicate confusion.
- Detect when the student is writing in their own words vs. paraphrasing closely.
- Intervene *during* the writing process rather than after section completion.

This would enable the system to nudge the student *while* they're producing generic summaries rather than only catching it after the fact. However, it introduces significant technical complexity (editor monitoring, debouncing, intervention timing) and risks disrupting writing flow.

Deferred to future work — the turn-based version validates the framework; the real-time version improves the experience.

### Student-Generated Content Validation

When students generate their own examples, those examples can be wrong in subtle ways that reinforce misconceptions. The current design handles this through Socratic follow-up questions rather than direct correctness judgments. Open question: is this sufficient, or does the system need a more explicit mechanism for catching confident misunderstandings before they're baked into study notes?

---

## How This Connects to the Thesis Deliverables

| Deliverable | How this use case serves it |
| --- | --- |
| **Literature Review** | Draws on the same sources — Desirable Difficulties, Scaffolding, Productive Failure, process-oriented support, the perception-performance paradox. Bloom's taxonomy provides an additional lens specific to learning. |
| **Strategy Taxonomy** | The three intervention types (Connection, Transfer, Depth) are design strategies. The student's choice to engage, link, or elaborate are usage strategies. |
| **Conceptual Framework** | Directly demonstrates Role → Strategy → Cognitive Function chains. Each intervention type maps to a specific role, employs a specific strategy, and targets a specific cognitive function. |
| **Prototype** | A concrete, buildable, evaluable system. The simplified turn-based workflow is achievable within thesis scope while still demonstrating the full framework. |

---

## Comparison to Source-Synthesis Use Case

| Dimension | Source Synthesis | Note Augmentation |
| --- | --- | --- |
| **Cognitive protection argument** | Strong but debatable — "the output matters too" | Airtight — the process *is* the point |
| **User population** | Researchers, analysts, knowledge workers | Students — large, accessible, relatable |
| **Evaluation** | Harder — what counts as "better synthesis"? | Cleaner — note quality, link density, exam performance are measurable |
| **Adoption tension** | High — competes with productivity pressure | Present but different — competes with time pressure, not productivity doctrine |
| **Graph relevance** | Strong — sources connect to claims connect to arguments | Strong — concepts connect to concepts, examples connect to principles |
| **Framework demonstration** | Full chain demonstrated | Full chain demonstrated |
| **Technical complexity** | Higher — vector retrieval, multi-source context | Lower in simplified version — single source, turn-based |

Both use cases are viable. They could also coexist in the thesis — the framework is domain-agnostic, and showing it works across two different use cases strengthens the generalizability claim.

---

## Related Notes

- [[Thesis Overview]]
- [[THESIS_CONTEXT.md]]
- [[Obsidian Idea/tft-architecture-overview-v2]]
