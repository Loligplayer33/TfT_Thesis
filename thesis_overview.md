# Thesis Overview — Where You Stand

_A single-page map of your thesis, what's done, what's open, and how it all connects._

---

## Your Thesis in One Sentence

Find, organize, and demonstrate design and usage strategies that prevent cognitive offloading when people use Generative AI — grounded in HCI, learning science, and cognitive psychology.

---

## The Four Deliverables

Your thesis has four required outputs. They build on each other sequentially.

### 1. Systematic Literature Review

**What it is:** Survey existing design patterns and theories that support forward-reasoning and prevent cognitive offloading.

**Fields to cover:** HCI, Learning Sciences, Cognitive Psychology.

**Anchoring theories from the thesis spec:**

- Desirable Difficulties (Bjork) — making tasks harder in specific ways improves learning
- Scaffolding (Vygotsky / ZPD) — temporary support structures that are removed as competence grows
- Productive Failure (Kapur) — letting learners struggle before instruction leads to deeper understanding

**Additional sources to engage:**

- Zhang et al. CHI 2026 workshop paper (your primary framing paper)
- Source [20] — the CHI 2025 workshop synthesis (34 submissions with concrete TfT designs)
- Source [24] — Zhang & Reicherts on process-oriented support and forward-reasoning
- Sarkar (2024) — "AI Should Challenge, Not Obey" (the Provocateur role)
- Kazemitabaar et al. (2025) — cognitive engagement techniques in programming education
- Ashktorab et al. (2025) — user resistance to cognitive forcing functions

**Status:** Not started. This is your next major work item.

---

### 2. Strategy Taxonomy

**What it is:** Organize everything from the literature review into a structured classification.

**Primary axis (from the workshop paper Section 1.1):**

- **Design Strategies** — how the system is built (e.g., withhold answers, inject questions, surface contradictions)
- **Usage Strategies** — how the user interacts (e.g., using AI for explanation-seeking rather than solution-seeking, inspecting/modifying skill definitions)

**Possible sub-axes to discover during the review:**

- Mechanism type: withholding, restructuring, prompting, provoking, scaffolding
- Timing: proactive vs. reactive, continuous vs. checkpoint-based
- Cognitive function targeted: critical thinking, metacognition, sensemaking, etc.

**Status:** Not started. Depends on the literature review.

---

### 3. Conceptual Framework

**What it is:** A mapping of AI roles → strategies → cognitive functions.

**The core structure:**

- **AI Roles** (the stance): Socratic Tutor, Provocateur, Facilitator, Reflective Prompter, etc.
- **Strategies** (the concrete behaviors that realize each role): question-based scaffolding, deliberate counterargument, withholding, structured decomposition, etc.
- **Cognitive Functions** (what gets activated): critical thinking, metacognition, sensemaking, reflection, etc.

**Key insight:** The mapping is many-to-many. One strategy can serve multiple roles. One role can employ multiple strategies. The framework maps out which combinations work, when, and why.

**How this connects to the prototype:** Your skill definition schema _is_ this framework made concrete. Each skill file encodes a role, its strategies, and the cognitive function it targets.

**Status:** Partially implicit in the architecture document. Needs to be made explicit as a standalone theoretical contribution.

---

### 4. Prototypical Validation (Proof-of-Concept)

**What it is:** A working system that demonstrates how a specific strategy shifts the user from passive consumer to active thinker.

**What you're building:** An Obsidian-based TfT system where:

- Skills (markdown files) define AI roles and their strategies
- An orchestration layer enforces cognitive checkpoints
- The AI interacts through sidebar chat, inline callouts, and canvas cards
- Intermediary artifacts (notes, questions, counterarguments) are created in the vault

**Scope clarification:** You're building the _full architecture_ that can express any role-strategy-cognition chain from the framework. But you only implement and validate one or two concrete skills. The architecture argues generalizability; the skills prove it works for at least one case.

**Status:** Architecture designed (v2 document complete). No code written yet.

---

## How the Four Deliverables Connect

```
Literature Review ──→ Strategy Taxonomy ──→ Conceptual Framework ──→ Prototype
  (find patterns)      (organize them)      (map role→strategy→     (make it real,
                                             cognitive function)      test one slice)
                                                    │
                                                    ▼
                                            Skill Definition Schema
                                            (framework as code)
```

The thesis _leads_ with the framework (deliverables 1–3) and presents the prototype (deliverable 4) as evidence. Not the other way around.

---

## What's Done

| Artifact                            | Status        | Notes                                                                                                                               |
| ----------------------------------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Architecture decision document (v2) | ✅ Complete   | 1015 lines. Covers orchestration, skills, Obsidian choice, interaction patterns, vault structure, backend stack.                    |
| Core stack decisions                | ✅ Settled    | All TypeScript. Anthropic SDK, MCP server, Obsidian plugin, skills as markdown.                                                     |
| Skill concept design                | ✅ Conceptual | Skills as conversational stances (not output types). Role, withholding rules, artifact types, transition offers, vault interaction. |
| Interaction pattern design          | ✅ Designed   | Four patterns (A–D) with implementation order. Pattern B (inline callouts) identified as highest TfT value.                         |
| Research paper analysis             | ✅ Done       | Deep understanding of Zhang et al. CHI 2026, the three themes, Rogers et al. outcome types.                                         |
| Thesis scope understanding          | ✅ Clear      | Thesis A (strategies), not Thesis B (evaluation). Four deliverables understood.                                                     |

---

## What's Not Done

| Work item                                        | Deliverable it feeds | Priority                                                 |
| ------------------------------------------------ | -------------------- | -------------------------------------------------------- |
| Literature review                                | 1                    | **Next** — everything else depends on this               |
| Strategy taxonomy                                | 2                    | After literature review                                  |
| Explicit conceptual framework                    | 3                    | After taxonomy; partially prefigured in architecture doc |
| Skill definition schema (YAML + markdown format) | 4                    | Needed before coding                                     |
| First skill implementation                       | 4                    | Likely Socratic Questioner or Devil's Advocate           |
| Obsidian plugin architecture                     | 4                    | How plugin connects to backend                           |
| MCP server tool signatures                       | 4                    | Exact vault operation interfaces                         |
| Any code                                         | 4                    | Nothing written yet                                      |

---

## Key Tensions to Keep in Mind

**Engineering ambition vs. thesis scope.** Your architecture document describes five skills, four interaction patterns, canvas manipulation, vector retrieval, and artifact lifecycle. The thesis needs one skill working well across one or two patterns. Don't let building outrun writing.

**Framework vs. prototype in the thesis narrative.** The thesis contribution is the framework (deliverables 1–3). The prototype is evidence, not the main event. Risk: writing a thesis that reads like engineering docs rather than a research contribution.

**Design strategies vs. usage strategies.** Your prototype is heavily weighted toward design strategies (how the system is built). The thesis also asks about usage strategies (how users interact). The editable skill files and user ability to dismiss/modify scaffolding are usage strategies — make that connection explicit.

**Productive friction vs. adoption.** Your cognitive checkpoints are friction by design. The literature (Ashktorab et al.) shows users resist this. Your architecture acknowledges it (dismissable checkpoints, frequency adaptation) but it remains the biggest open question: will users actually engage?

---

## The Research Grounding (Key Sources)

| Source                           | What it contributes                                 | Relevant to                 |
| -------------------------------- | --------------------------------------------------- | --------------------------- |
| Zhang et al. CHI 2026            | Primary framing: TfT strategies, outcomes, adoption | Everything                  |
| Source [20] — CHI 2025 synthesis | 34 concrete TfT design examples                     | Literature review, taxonomy |
| Source [24] — Zhang & Reicherts  | Process-oriented support, forward-reasoning         | Core design principle       |
| Sarkar (2024)                    | AI as Provocateur, "AI Should Challenge Not Obey"   | AI roles in framework       |
| Rogers et al. (2025)             | Three outcome types: intermediary, cognitive, task  | Artifact design, evaluation |
| Bjork — Desirable Difficulties   | Making tasks harder improves learning               | Strategy taxonomy           |
| Kapur — Productive Failure       | Struggle before instruction deepens understanding   | Strategy taxonomy           |
| Vygotsky — Scaffolding / ZPD     | Temporary support structures                        | Strategy taxonomy           |
| Kreijkes et al. (2025)           | Perception-performance paradox                      | Why TfT design is hard      |
| Lehmann et al. (2024)            | Solution-seeking harms, explanation-seeking helps   | Forward-reasoning principle |
| Fan et al. (2025)                | Metacognitive laziness                              | Mechanism of cognitive harm |
| Ashktorab et al. (2025)          | User resistance to cognitive forcing functions      | Adoption tension            |
| Kazemitabaar et al. (2025)       | Cognitive engagement techniques in programming      | Design strategies           |
