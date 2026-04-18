# The Task:
![[Pasted image 20260418172656.png]]


# Thesis Overview — Where You Stand

_A single-page map of your thesis, what's done, what's open, and how it all connects._

---

## Your Thesis in One Sentence

Find, organize, and demonstrate design and usage strategies that prevent cognitive offloading when people use Generative AI — grounded in HCI, learning science, and cognitive psychology.

---

## Current Entry Point: Overview First

The overview pass through the three framing papers is substantially complete (all three have Zotero notes, with some synthesis work already started on Tankelevitch 2025):

1. **Tankelevitch et al. (2025) synthesis** — best broad map of the Tools for Thought field
2. **Zhang et al. (2026) workshop paper** — best framing for the thesis structure
3. **Tankelevitch et al. (2024) metacognitive demands** — best theory-oriented explanation of the cognitive problem

The fuller reading map, phased reading plan, and concise source list live in [[Literature Review/Overview Synthesis and Reading Map]].

Current active reading layer is in [[Literature Review/Synthesis/README|Literature Review/Synthesis]] — six thematic synthesis notes where cross-paper argument develops.

---

## The Four Deliverables

The thesis has four required outputs. They build on each other sequentially.

### 1. Systematic Literature Review

**What it is:** Survey existing design patterns and theories that support forward-reasoning and prevent cognitive offloading.

**Fields to cover:** HCI, Learning Sciences, Cognitive Psychology.

**Anchoring theories from the thesis spec:**

- Desirable Difficulties (Bjork) — making tasks harder in specific ways improves learning
- Scaffolding (Vygotsky / ZPD) — temporary support structures that are removed as competence grows
- Productive Failure (Kapur) — letting learners struggle before instruction leads to deeper understanding

**Canonical source map:** [[Literature Review/Overview Synthesis and Reading Map]]

**Synthesis infrastructure in place:**

- Six thematic notes in [[Literature Review/Synthesis/README|Literature Review/Synthesis]] — cross-paper argument develops here
- Paper-level records in `Literature Review/zotero_notes/` — reading record and in-situ reactions
- Thin paper headers in `Literature Review/Overview Papers/` and `Literature Review/imports/`
- [[Literature Review/Sources by Domain]] — tracking for sources referenced across papers
- [[Glossary]] — stable definitions

**Status:** Overview pass substantially complete. Active synthesis work underway on Tankelevitch 2025. Stage 1 (problem mechanism papers — Colombatto, Lee, Fan, Kreijkes, Bastani) is the next priority.

---

### 2. Strategy Taxonomy

**What it is:** Organize findings from the literature review into a structured classification.

**Primary axis (from the CHI 2026 workshop paper, Zhang et al.):**

- **Design Strategies** — how the system is built (e.g., withhold answers, inject questions, surface contradictions, process-oriented support)
- **Usage Strategies** — how the user interacts (e.g., explanation-seeking vs. solution-seeking, mode selection, producing independent intermediate artifacts)

**Possible sub-axes to discover during the review:**

- Mechanism type: withholding, restructuring, prompting, provoking, scaffolding, feedforward
- Intervention timing: on-demand, sequential, dynamic (cross-cutting dimension)
- Directness: direct challenge, formal structure, representational transformation, motivational pathways
- Cognitive function targeted: critical thinking, metacognition, sensemaking, creativity, learning

**Status:** Not started. Depends on the literature review.

---

### 3. Conceptual Framework

**What it is:** A mapping of AI roles → strategies → cognitive functions.

**The core structure:**

- **AI Roles** (the stance): Socratic Tutor, Provocateur, Facilitator, Ignorant Co-Learner, Coach, etc.
- **Strategies** (the concrete behaviors that realize each role): question-based scaffolding, deliberate counterargument, withholding, structured decomposition, feedforward, etc.
- **Cognitive Functions** (what gets activated): critical thinking, metacognition, sensemaking, reflection, etc.

**Key insight:** The mapping is many-to-many. One strategy can serve multiple roles. One role can employ multiple strategies. The framework maps out which combinations work, when, and why.

**Status:** Not started as an explicit artifact. AI Roles synthesis note ([[Literature Review/Synthesis/AI Roles]]) will be the staging ground once enough papers have been read.

---

### 4. Prototypical Validation (Proof-of-Concept)

**What it is:** A working system that demonstrates how a specific strategy shifts the user from passive consumer to active thinker.

**Scope clarification:** The thesis contribution is the framework (deliverables 1–3). The prototype is evidence, not the main event. The goal is a working slice — one strategy realized through one role, tested against one cognitive function — not a full system.

**Form not yet committed.** An Obsidian-based architecture was explored in depth as one possibility and is documented outside this vault, but the prototype form should follow from the framework rather than the other way around. A note augmentation use case (post-lecture section-by-section review) has been explored as a potential direction, with key design decisions identified but left open.

**Open prototype questions:**
- Single-lecture vs. cumulative cross-lecture context scope
- Primary interaction modality (chat sidebar, inline callouts, canvas cards, etc.)
- Real-time monitoring as a potential deferred extension

**Status:** No code written. No prototype form committed. Decision deferred until framework has enough shape to point at a specific strategy to prototype.

---

## How the Four Deliverables Connect

```
Literature Review ──→ Strategy Taxonomy ──→ Conceptual Framework ──→ Prototype
  (find patterns)      (organize them)      (map role→strategy→     (demonstrate
                                             cognitive function)      one slice)
```

The thesis _leads_ with the framework (deliverables 1–3) and presents the prototype (deliverable 4) as evidence. Not the other way around.

---

## What's Not Done

| Work item                                             | Deliverable it feeds | Priority                                                                                             |
| ----------------------------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------- |
| Stage 1 reading (problem mechanism papers)            | 1                    | **Next** — Colombatto, Lee, Fan, Kreijkes, Bastani                                                   |
| Stage 2 reading (design principles)                   | 1                    | After Stage 1 — Zhang & Reicherts, Lehmann, Lira, Kazemitabaar, Ashktorab, Singh, Sarkar             |
| Stage 3 reading (strategy landscape, adoption)        | 1                    | After Stage 2 — Zheng, Terzimehić, Rogers                                                            |
| Stage 4 reading (theoretical anchors)                 | 1                    | After Stage 3 — Bjork, Kapur, Vygotsky / Wood, Bruner & Ross                                         |
| Strategy taxonomy (as explicit artifact)              | 2                    | After sufficient literature; the Synthesis notes accumulate the raw material                         |
| Explicit conceptual framework                         | 3                    | After taxonomy                                                                                       |
| Prototype form decision                               | 4                    | After framework has enough shape to point at a specific strategy                                     |
| Any prototype code                                    | 4                    | Nothing written yet                                                                                  |

---

## Key Tensions to Keep in Mind

**Engineering ambition vs. thesis scope.** Earlier prototype exploration described multiple skills, interaction patterns, and architecture detail. The thesis needs one working slice. Keep prototype work scoped to evidence, not system-building.

**Framework vs. prototype in the thesis narrative.** The contribution is the framework (deliverables 1–3). The prototype is evidence. Risk: writing a thesis that reads like engineering docs rather than a research contribution.

**Design strategies vs. usage strategies.** The literature is noticeably thicker on design strategies than on usage strategies. That asymmetry is itself worth naming in the thesis. Watch for usage strategies as you read — they're often implicit in design discussions.

**Productive friction vs. adoption.** Cognitively protective strategies add friction, and users resist friction (Ashktorab et al.). This is the central adoption tension and a recurring theme in [[Literature Review/Synthesis/Adoption and Friction]]. It cannot be treated as a limitations footnote.

**Cognition protection vs. cognitive entanglement.** The metacognitive framework (Tankelevitch et al. 2024) assumes the object-level cognition being monitored is the user's own. Under sustained GenAI use this weakens — see [[Literature Review/Bucket/The Metacognitive Framework and the User-AI Cognitive Entanglement Problem]]. This raises the stakes of the problem and shapes design requirements around cognitive traceability.

---

## The Research Grounding (Key Sources)

The current detailed source map and reading order is [[Literature Review/Overview Synthesis and Reading Map]]. The table below is the shorter thesis-level grounding view.

| Source                                           | What it contributes                                 | Relevant to                 |
| ------------------------------------------------ | --------------------------------------------------- | --------------------------- |
| Zhang et al. CHI 2026                            | Primary framing: TfT strategies, outcomes, adoption | Everything                  |
| Tankelevitch et al. 2025 (CHI 2025 synthesis)    | 34 concrete TfT design examples; field landscape    | Literature review, taxonomy |
| Tankelevitch et al. 2024 (metacognitive demands) | Core mechanism account for why cognitive risk arises | Problem, Theory             |
| Zhang & Reicherts 2025                           | Process-oriented support, forward-reasoning         | Core design principle       |
| Sarkar 2024 (AI Should Challenge, Not Obey)      | AI as Provocateur                                   | AI roles in framework       |
| Rogers et al. 2025                               | Three outcome types: intermediary, cognitive, task  | Artifact design, evaluation |
| Bjork — Desirable Difficulties                   | Making tasks harder improves learning               | Strategy taxonomy, theory   |
| Kapur — Productive Failure                       | Struggle before instruction deepens understanding   | Strategy taxonomy, theory   |
| Vygotsky / Wood, Bruner & Ross — Scaffolding     | Temporary support structures                        | Strategy taxonomy, theory   |
| Kreijkes et al. 2025                             | Perception-performance paradox                      | Why TfT design is hard      |
| Lehmann et al. 2024                              | Solution-seeking harms, explanation-seeking helps   | Forward-reasoning, usage    |
| Fan et al. 2025                                  | Metacognitive laziness                              | Mechanism of cognitive harm |
| Ashktorab et al. 2025                            | User resistance to cognitive forcing functions      | Adoption tension            |
| Kazemitabaar et al. 2025                         | Cognitive engagement techniques in programming      | Design strategies           |
| Colombatto, Rintel & Tankelevitch 2025           | Confidence dynamics in advice-taking                | Problem mechanism           |

---

## Related

- [[Literature Review/Overview Synthesis and Reading Map]]
- [[Literature Review/README]]
- [[Literature Review/Synthesis/README|Literature Review/Synthesis]]
- [[THESIS_CONTEXT]]
- [[Glossary]]
