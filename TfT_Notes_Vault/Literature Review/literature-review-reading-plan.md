# Literature Review — Reading Plan

_A structured sequence for working through the source material, organized by what each source contributes to your thesis._

---

## How to Approach This

Your literature review needs to answer one central question: **What design and usage strategies exist (or can be derived) that prevent cognitive offloading when people use GenAI?**

To answer that, you need to understand three things in sequence:

1. **The problem** — What goes wrong cognitively when people use GenAI?
2. **The theory** — What existing frameworks from cognitive psych, learning science, and HCI explain why it goes wrong and what could work?
3. **The strategies** — What concrete design patterns and usage approaches have been proposed or tested?

The reading plan follows this sequence. Within each phase, sources are ordered by priority — read the starred (★) ones first, then fill in with the rest.

---

## Phase 1: Understand the Problem

_Goal: Build a precise picture of how GenAI erodes cognition. This is the "why we need TfT" argument._

### ★ Colombatto, Rintel & Tankelevitch (2025) — Metacognition and Confidence Dynamics in Advice Taking from GenAI
- **Domain:** Cognitive Psychology / HCI
- **What it gives you:** Empirical evidence that GenAI advice causally boosts confidence in both self and AI, while users fail to verify outputs. Shows the bidirectional confidence loop: prospective confidence shapes whether you seek advice, and advice exposure inflates retrospective confidence. The key finding for your thesis: participants who relied on advice missed critical information because they didn't check the output — even when financially incentivized to be thorough.
- **Why your supervisor gave you this:** It's the most detailed empirical account of *how* cognitive offloading actually works at the metacognitive level. Your design strategies need to interrupt exactly these dynamics.

### ★ Tankelevitch et al. (2024) — The Metacognitive Demands and Opportunities of GenAI
- **Domain:** HCI / Cognitive Science
- **Ref in workshop paper:** Referenced via Colombatto et al.; by the same Microsoft TfT group
- **What it gives you:** A comprehensive framework of metacognitive demands GenAI places on users — self-awareness, confidence calibration, metacognitive flexibility. Maps demands to each stage of a GenAI workflow (prompting, evaluating output, adapting workflow). This is the theoretical companion to Colombatto et al.
- **Note:** Not in the workshop paper references directly, but cited heavily by Colombatto et al. and by the TfT group. Essential reading.

### ★ Lee et al. (2025) — The Impact of GenAI on Critical Thinking [ref 7]
- **Domain:** HCI / Knowledge Work
- **What it gives you:** Survey of knowledge workers showing self-reported reductions in cognitive effort when using GenAI. Extends the problem from education to professional contexts. Also shows confidence effects — workers with higher confidence in GenAI reported greater reductions in critical thinking.

### ★ Fan et al. (2025) — Beware of Metacognitive Laziness [ref 4]
- **Domain:** Learning Sciences / Educational Technology
- **What it gives you:** Names the mechanism — "metacognitive laziness." GenAI use reduces motivation, metacognitive monitoring, and learning processes. Shows it's not just outcomes that suffer; the monitoring system itself degrades.

### ★ Kreijkes et al. (2025) — Effects of LLM Use and Note-Taking on Reading Comprehension [ref 6]
- **Domain:** Learning Sciences / Education
- **What it gives you:** The perception-performance paradox. Students perceived LLMs as more helpful than note-taking, but performed worse. This explains why the problem is self-concealing and why user satisfaction is a bad proxy for cognitive benefit.

### Bastani et al. (2025) — GenAI Without Guardrails Can Harm Learning [ref 3]
- **Domain:** Education / Economics
- **What it gives you:** Large-scale evidence (high school math) that unguarded GenAI access harms learning outcomes. The "damage case" — proves the problem is real and measurable at scale.

### Noy & Zhang (2023) — Experimental Evidence on Productivity Effects of GenAI [ref 10]
- **Domain:** Economics / Productivity Research
- **What it gives you:** GenAI boosts productivity in professional writing tasks. Important because it establishes what TfT is *not* optimizing for — raw productivity — while acknowledging that productivity gains are real. You need this to make the adoption tension concrete.

---

## Phase 2: Understand the Theoretical Foundations

_Goal: Learn the frameworks from cognitive psychology and learning science that your taxonomy and conceptual framework will draw on. These are the anchoring theories from your thesis spec._

### ★ Lehmann, Cornelius & Sting (2024) — AI Meets the Classroom: When Does ChatGPT Harm Learning? [ref 8]
- **Domain:** Learning Sciences / Education
- **What it gives you:** The directionality finding — using ChatGPT for direct solutions harms learning, but using it for explanation-seeking helps. This is the empirical anchor for the "forward-reasoning" design principle that runs through your entire thesis.

### ★ Zhang & Reicherts (2025) — Augmenting Human Cognition with GenAI: Lessons from AI-Assisted Decision-Making [ref 24]
- **Domain:** HCI / Decision Science
- **What it gives you:** Process-oriented support as a design strategy — helping users reason forward to their own solution rather than backward from an AI-generated one. This is the single most important design principle for your framework. Read this early and carefully.

### ★ Lira et al. (2025) — Learning Not Cheating: AI Assistance Can Enhance Rather than Hinder Skill Development [ref 9]
- **Domain:** Learning Sciences / Cognitive Psychology
- **What it gives you:** The positive counter-case. AI assistance *can* enhance skill development through high-quality personalized examples. Important for your framework because it shows augmentation is possible — the question is *how* the AI is designed and used.

### Kazemitabaar et al. (2025) — Exploring the Design Space of Cognitive Engagement Techniques [ref 5]
- **Domain:** HCI / Computing Education
- **What it gives you:** Systematically explores cognitive engagement techniques for AI-generated code in programming education. Directly addresses the balance between performance and cognitive engagement — the friction-vs-productivity tension. Likely contains concrete design patterns you can extract for your taxonomy.

### Ashktorab et al. (2025) — Emerging Reliance Behaviors: The Role of Cognitive Forcing Functions [ref 2]
- **Domain:** HCI / AI-Assisted Work
- **What it gives you:** Users had negative impressions of cognitive forcing functions that created extra work. This is the key adoption-tension reference. Your system's checkpoints are cognitive forcing functions — this paper tells you what happens when they're poorly designed.

### Rogers, Reicherts, Zhang & Hassib (2025) — Augmenting Human Cognition Through GenAI [ref 13]
- **Domain:** HCI / Cognitive Science
- **What it gives you:** The three outcome types framework — intermediary, cognitive, task. This is the evaluation lens the workshop paper adopts. Your intermediary artifacts (vault notes, questions, counterarguments) map directly to this framework.

### Singh, Guan & Rieh (2025) — Enhancing Critical Thinking with Metacognitive Prompts [ref 17]
- **Domain:** Information Science / Metacognition
- **What it gives you:** Metacognitive prompts in generative AI search can enhance critical thinking. A concrete design strategy — prompting users to reflect on their own thinking. Relevant to your Reflective Prompter skill.

### Sarkar (2024) — AI Should Challenge, Not Obey [ref 14]
- **Domain:** HCI / AI Design
- **What it gives you:** The Provocateur framing — AI as challenger rather than assistant. One of the AI roles in your conceptual framework. A short, influential piece (CACM cover story).

### Sarkar (2024) — Intention Is All You Need [ref 15]
- **Domain:** HCI / Programming Psychology
- **What it gives you:** Argues that maintaining user intentionality is the key design goal for GenAI tools. Relevant to your orchestration layer — the system should support the user's intentions, not override them.

### Sarkar, Xu, Toronto, Drosos & Poelitz (2024) — When Copilot Becomes Autopilot [ref 16]
- **Domain:** HCI / Knowledge Work
- **What it gives you:** Diagnoses the risk of GenAI shifting from co-pilot to auto-pilot in knowledge work. Proposes critical solutions. Directly relevant to your thesis problem statement.

---

## Phase 3: Map the Landscape of Strategies

_Goal: Collect concrete design examples and strategy patterns from the TfT community and adjacent work._

### ★ Tankelevitch, Glassman, He et al. (2025) — CHI 2025 Tools for Thought Workshop Synthesis [ref 20]
- **Domain:** HCI (Workshop Synthesis)
- **What it gives you:** The most important single source for your taxonomy. Synthesizes 34 workshop submissions into themes and patterns. Contains the concrete design examples that the 2026 workshop paper says need to be systematized. This is where your taxonomy starts.

### ★ Zhang et al. (2026) — Tools for Thought: From Vision to Implementation [your framing paper, ref 19 context]
- **Domain:** HCI (Workshop Proposal)
- **What it gives you:** You've already read this deeply. Use it as the structural backbone — the three themes (strategies, outcomes, adoption) organize your literature review.

### Zheng et al. (2023) — Competent but Rigid: AI in Group Decision-Making [ref 25]
- **Domain:** HCI / CSCW
- **What it gives you:** AI as facilitator in group decision-making. Explores what happens when AI participates as an equal rather than a tool. Relevant to your Facilitator role.

### Terzimehić, Bühler & Kasneci (2025) — Conversational AI as Catalyst for Informal Learning [ref 21]
- **Domain:** Learning Sciences / HCI
- **What it gives you:** Even when GenAI isn't designed as a TfT, users find learning-enhancing usage strategies — generating quizzes, adapting content, discussing ideas. This is the "usage strategies" side of your taxonomy.

### Robinson (2024) — Employees Report AI Increased Workload [ref 12]
- **Domain:** Business / Popular Press
- **What it gives you:** 96% of C-suite executives expect AI to boost productivity. Context for the adoption tension — your system swims against this current.

### EY Americas (2023) — AI Anxiety Survey [ref 1]
- **Domain:** Business / Industry Report
- **What it gives you:** 66% of employees concerned about falling behind without AI. Additional adoption tension context.

---

## Phase 4: Deepen the Theoretical Anchors (from your thesis spec, not in workshop paper)

_These are the foundational learning science and cognitive psychology theories your thesis spec names. You'll need to find and read key papers for each._

### Bjork — Desirable Difficulties
- **Domain:** Cognitive Psychology
- **Key idea:** Making learning tasks harder in specific ways (spacing, interleaving, generation effect) improves long-term retention and transfer. Your cognitive checkpoints are desirable difficulties.
- **Start with:** Bjork, R.A. (1994). "Memory and metamemory considerations in the training of human beings." Also: Bjork & Bjork (2011). "Making things hard on yourself, but in a good way."

### Kapur — Productive Failure
- **Domain:** Learning Sciences
- **Key idea:** Letting learners struggle and fail before receiving instruction leads to deeper conceptual understanding than direct instruction first. Your system's withholding rules (don't give answers before the user articulates their position) are productive failure.
- **Start with:** Kapur, M. (2008). "Productive failure." Cognition and Instruction, 26(3). Also: Kapur, M. (2016). "Examining productive failure, productive success, and instructional analogies."

### Vygotsky — Scaffolding / Zone of Proximal Development
- **Domain:** Educational Psychology
- **Key idea:** Learners benefit most from support that targets the gap between what they can do alone and what they can do with help. The support should be temporary and gradually removed. Your skills are scaffolds; the orchestration layer manages their intensity.
- **Start with:** Wood, Bruner & Ross (1976). "The role of tutoring in problem solving." (This is where "scaffolding" as a concept was formalized, building on Vygotsky.)

---

## Suggested Reading Sequence

| Week | Focus | Sources |
|------|-------|---------|
| 1 | The problem | Colombatto et al. ★, Lee et al. ★, Fan et al. ★, Kreijkes et al. ★ |
| 2 | Core design principles | Zhang & Reicherts ★, Lehmann et al. ★, Sarkar (2024) ★, Lira et al. ★ |
| 3 | Strategy landscape | Tankelevitch et al. synthesis [20] ★, Kazemitabaar et al., Ashktorab et al. |
| 4 | Theoretical anchors | Bjork (Desirable Difficulties), Kapur (Productive Failure), Wood/Bruner/Ross (Scaffolding) |
| 5 | Framework sources | Rogers et al., Singh et al., Sarkar (Intention), Sarkar (Copilot→Autopilot) |
| 6 | Adoption & context | Zheng et al., Terzimehić et al., Tankelevitch (2024) metacognitive demands |

Note: This is roughly 20-25 papers across 6 weeks. Adjust based on your timeline. The ★ sources are non-negotiable — everything else can be skimmed or deferred if time is tight.

---

## What to Extract from Each Paper

As you read, track these for your taxonomy:

1. **Problem identified** — What cognitive harm or risk does this paper document?
2. **Mechanism** — Why does the harm occur? (metacognitive laziness, confidence inflation, skipping intermediary steps, etc.)
3. **Strategy proposed or implied** — What design or usage approach does the paper suggest or test?
4. **Strategy type** — Design strategy (system-level) or usage strategy (user-level)?
5. **AI role implied** — Does this suggest a specific AI stance? (tutor, provocateur, facilitator, etc.)
6. **Cognitive function targeted** — What higher-order cognition is being protected or augmented?
7. **Evidence quality** — Empirical study? Theoretical argument? Design exploration? How strong is the evidence?
