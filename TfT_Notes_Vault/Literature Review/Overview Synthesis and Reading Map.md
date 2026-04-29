---
title: Overview Synthesis and Reading Map
tags:
  - literature-review
  - overview
  - reading-plan
  - thesis
aliases:
  - Literature Overview Synthesis
  - Overview Reading Map
status: active
---

# Overview Synthesis and Reading Map

This note is the canonical cross-paper orientation for the literature review. It consolidates the reading plan, source map, and the synthesis workflow the vault uses.

## What This Note Is For

- Give a high-quality first map of the field before deep reading.
- Normalize the source list into a clearer structure: problem, theory, strategies, adoption, and thesis anchors.
- Preserve the distinction between a provisional reading map and the final claims of the literature review.
- Point at the synthesis infrastructure where cross-paper argument develops.

## The Synthesis Workflow

Reading is structured across three layers:

- **Zotero notes** (`Literature Review/zotero_notes/`) — full reading record, highlights, in-situ reactions. Cite with page-specific links here.
- **Paper headers** (`Literature Review/imports/` and `Literature Review/Papers/`) — new imports land in `imports`; existing curated paper headers may be organized under `Papers` by paper type.
- **Synthesis notes** ([[Literature Review/Synthesis/README|Literature Review/Synthesis]]) — seven thematic notes where cross-paper argument develops. This is where the literature review is drafted in rough form.

The seven synthesis notes:

- [[Literature Review/Synthesis/The Problem]] — mechanisms of cognitive offloading, which cognitive functions are at stake
- [[Theoretical Foundations]] — Bjork, Kapur, Vygotsky, metacognitive framework
- [[Literature Review/Synthesis/Design Strategies]] — system-side interventions
- [[Literature Review/Synthesis/Usage Strategies]] — user-side strategies
- [[Literature Review/Synthesis/AI Roles]] — Socratic Tutor, Provocateur, Facilitator, etc.
- [[Literature Review/Synthesis/Adoption and Friction]] — the cross-cutting tension
- [[Literature Review/Synthesis/Outcomes]] — the three-type outcomes typology (intermediary, cognitive, task) the framework chain ends in

After each paper, update the 1–3 synthesis notes it touches. Add bullets under an H3 wikilinked to the paper note or Zotero note. If the paper shifts your thinking, edit the **Working Thoughts** section of Current Argument. Once multiple papers back a claim, promote it into **Synthesized Position** with inline citekeys.

Supporting notes:

- [[Literature Review/Sources by Domain]] — tracking for sources referenced across papers but not yet read
- [[Glossary]] — stable term definitions and open research questions
- [[Literature Review/README]] — full workflow guide

## Short Answer: Where To Start

The overview pass through these three sources is substantially complete — all three have Zotero notes and synthesis contributions. Treat them as re-read anchors rather than first-time priorities.

1. [Lev Tankelevitch et al. (2025), *Understanding, Protecting, and Augmenting Human Cognition with Generative AI: A Synthesis of the CHI 2025 Tools for Thought Workshop*](https://arxiv.org/abs/2508.21036)
   - Best single landscape overview.
   - Use it to understand the breadth of the field, the kinds of systems people are building, and the open research space.
2. [Zelun Tony Zhang et al. (2026), *Tools for Thought: Understanding, Protecting, and Augmenting Human Cognition with Generative AI - From Vision to Implementation*](https://www.microsoft.com/en-us/research/publication/tools-for-thought-understanding-protecting-and-augmenting-human-cognition-with-generative-ai-from-vision-to-implementation/)
   - Best thesis-framing overview.
   - Use it to structure the literature around three recurring questions: strategies, outcomes, and adoption.
3. [Lev Tankelevitch et al. (2024), *The Metacognitive Demands and Opportunities of Generative AI*](https://arxiv.org/abs/2312.10893)
   - Best conceptual overview of the underlying problem.
   - Use it to understand why GenAI creates cognitive risk even when outputs are useful.

Compressed into one line:

- 2025 synthesis = broadest map
- 2026 workshop paper = best thesis framing
- 2024 metacognition paper = best underlying theory

## Cross-Source Synthesis

Across the current source set, five points already look structurally important for the thesis:

1. **Tools for Thought reframes the design target.**
   GenAI should not be evaluated only by speed, convenience, or output quality. The TfT literature treats cognition itself as the design object and evaluation target.
2. **The core risk is not just wrong answers but distorted self-regulation.**
   Several sources converge on a stronger claim than simple inaccuracy: GenAI can change confidence, verification behavior, attention, and willingness to do cognitive work.
3. **The strongest design direction is process-oriented support.**
   The most promising interventions do not simply improve the final answer. They help the user reason forward, decompose tasks, inspect intermediate steps, and stay mentally active.
4. **Augmentation is possible, but not by default.**
   The literature does not support a blanket anti-AI position. It supports a conditional position: AI can help learning and thinking when it scaffolds cognition rather than replacing it.
5. **Adoption is the biggest practical tension.**
   Many of the most cognitively protective strategies add friction. That makes the literature on workload, resistance, and perceived usefulness central rather than peripheral.

## Important Normalization Note

Some current vault notes use shorthand labels, workshop reference numbers, or slightly different title variants. In this note sources are normalized to the most clearly verified titles confirmable from primary or author-hosted pages. Where a source was harder to access directly, claims are kept modest and the uncertainty is stated explicitly.

## Source Map

### 1. Overview And Framing Cluster

| Source                                                                                                                                                                                                                                                                                                                                     | What it is about                                                                             | Why it matters now                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| [Tankelevitch et al. (2025), *Understanding, Protecting, and Augmenting Human Cognition with Generative AI: A Synthesis of the CHI 2025 Tools for Thought Workshop*](https://arxiv.org/abs/2508.21036)                                                                                                                                     | A synthesis of the CHI 2025 TfT workshop and its submission landscape.                       | Best broad map of the field before deeper reading.          |
| [Zhang et al. (2026), *Tools for Thought: Understanding, Protecting, and Augmenting Human Cognition with Generative AI - From Vision to Implementation*](https://www.microsoft.com/en-us/research/publication/tools-for-thought-understanding-protecting-and-augmenting-human-cognition-with-generative-ai-from-vision-to-implementation/) | A workshop framing paper that organizes the field around strategies, outcomes, and adoption. | Best structural backbone for the thesis framing.            |
| [Tankelevitch et al. (2024), *The Metacognitive Demands and Opportunities of Generative AI*](https://arxiv.org/abs/2312.10893)                                                                                                                                                                                                             | A conceptual paper on the metacognitive demands GenAI places on users.                       | Best theory-oriented overview of why cognitive risk arises. |

### 2. Problem And Mechanism Evidence

| Source                                                                                                                                                                                                                   | What it is about                                                                        | Why it matters now                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| [Colombatto, Rintel, and Tankelevitch (2025), *Metacognition and Confidence Dynamics in Advice Taking from Generative AI*](https://arxiv.org/abs/2510.26508)                                                             | Advice-taking, confidence, and verification behavior when people use GenAI.             | Best mechanism paper for understanding confidence-driven offloading. **Listed by supervisor as important.**               |
| [Lee et al. (2025), *The Impact of Generative AI on Critical Thinking: Self-Reported Reductions in Cognitive Effort and Confidence Effects From a Survey of Knowledge Workers*](https://doi.org/10.1145/3706598.3713778) | Survey evidence about GenAI, cognitive effort, and critical thinking in knowledge work. | Extends the problem beyond school contexts.                                                                               |
| [Fan et al. (2025), *Beware of Metacognitive Laziness: Effects of Generative Artificial Intelligence on Learning Motivation, Processes, and Performance*](https://doi.org/10.1111/bjet.13544)                            | Learning motivation, learning processes, and metacognitive laziness under GenAI use.    | Names a mechanism that fits the thesis directly.                                                                          |
| [Kreijkes et al. (2025), *Effects of LLM Use and Note-Taking on Reading Comprehension and Memory: A Randomised Experiment in Secondary Schools*](https://doi.org/10.2139/ssrn.5095149)                                   | LLM use versus note-taking for reading comprehension and memory.                        | Strong source for the perception-performance paradox.                                                                     |
| [Bastani et al. (2025), *Generative AI without Guardrails Can Harm Learning: Evidence from High School Mathematics*](https://doi.org/10.1073/pnas.2422633122)                                                            | A field experiment on math learning with unguarded versus more structured AI support.   | Strong evidence that answer-first AI can hurt later independent performance.                                              |
| [Noy and Zhang (2023), *Experimental Evidence on the Productivity Effects of Generative Artificial Intelligence*](https://doi.org/10.1126/science.adh2586)                                                               | Productivity gains from GenAI in a writing task.                                        | Useful contrast so the thesis does not ignore why people adopt AI in the first place.                                     |

### 3. Design Principles And Positive Intervention Cases

| Source | What it is about | Why it matters now |
| --- | --- | --- |
| [Lehmann, Cornelius, and Sting (2024), *AI Meets the Classroom: When Does ChatGPT Harm Learning?*](https://arxiv.org/abs/2409.09047) | When AI support helps versus harms learning in classroom-like settings. | Strong source for explanation-seeking versus solution-seeking. |
| [Zhang and Reicherts (2025), *Augmenting Human Cognition With Generative AI: Lessons From AI-Assisted Decision-Making*](https://arxiv.org/abs/2504.03207) | A design-principle paper about process-oriented support in AI-assisted decision-making. | Best source for the forward-reasoning principle. |
| [Rogers, Reicherts, Zhang, and Hassib (2025), *Augmenting Human Cognition Through Generative AI*](https://doi.org/10.13140/RG.2.2.14568.12801) | Springer Handbook of Human-AI Collaboration chapter (4.1). Consolidates the process-oriented-support research program across AI-assisted decision-making and GenAI co-creation (writing, programming, scientific discovery), and introduces the three-type outcomes typology (intermediary / cognitive / task) that Zhang 2026 builds on. | Structural source — outcomes framework + extended handbook version of the Zhang & Reicherts 2025 argument. Read as a pair with Zhang & Reicherts 2025. |
| [Lira et al. (2025), *Learning Not Cheating: AI Assistance Can Enhance Rather than Hinder Skill Development*](https://arxiv.org/abs/2502.02880) | A positive case showing that AI help can support later skill development. | Important counterweight to purely negative accounts of offloading. |
| [Kazemitabaar et al. (2025), *Exploring the Design Space of Cognitive Engagement Techniques with AI-Generated Code for Enhanced Learning*](https://arxiv.org/abs/2410.08922) | Concrete techniques for keeping learners cognitively engaged while using AI-generated code. | One of the best strategy papers for extraction. |
| [Ashktorab et al. (2025), *Emerging Reliance Behaviors in Human-AI Content Grounded Data Generation: The Role of Cognitive Forcing Functions and Hallucinations*](https://research.ibm.com/publications/emerging-reliance-behaviors-in-human-ai-content-grounded-data-generation-the-role-of-cognitive-forcing-functions-and-hallucinations) | Reliance behavior, forcing functions, and user reactions to added friction. | Important for the adoption tension around protective friction. |
| [Singh, Guan, and Rieh (2025), *Enhancing Critical Thinking in Generative AI Search with Metacognitive Prompts*](https://arxiv.org/abs/2505.24014) | Metacognitive prompts in GenAI-supported search. | A good direct source for reflective prompting strategies. |
| [Sarkar (2024), *AI Should Challenge, Not Obey*](https://cacm.acm.org/opinion/ai-should-challenge-not-obey/) | A short provocation about AI as challenger rather than obedient assistant. | Good source for the provocateur role. |
| [Sarkar (2024), *Intention Is All You Need*](https://arxiv.org/abs/2410.18851) | A position on protecting user intentionality in AI-supported work. | Useful for the autonomy and intentionality framing. |
| [Sarkar et al. (2024), *When Copilot Becomes Autopilot: Generative AI's Critical Risk to Knowledge Work and a Critical Solution*](https://arxiv.org/abs/2412.15030) | The risk of AI shifting from assistance to autopilot in knowledge work. | Strong framing source for the broader problem statement. |
| [Gmeiner et al. (2025), *Exploring the Potential of Metacognitive Support Agents for Human-AI Co-Creation*](http://arxiv.org/abs/2506.12879) | Metacognitive support agents that combine reflective questioning with structuring activities. | Direct evidence for the Role → Strategy → Cognitive Function chain. |

### 4. Strategy Landscape, Roles, And Adoption Context

| Source                                                                                                                                                                                                                   | What it is about                                                             | Why it matters now                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| [Tankelevitch et al. (2025) synthesis](https://arxiv.org/abs/2508.21036)                                                                                                                                                 | A field map of current TfT work and examples.<br>- DONE                      | Best source for scanning the broader landscape of strategy ideas.           |
| [Zhang et al. (2026) workshop framing](https://www.microsoft.com/en-us/research/publication/tools-for-thought-understanding-protecting-and-augmenting-human-cognition-with-generative-ai-from-vision-to-implementation/) | An implementation-oriented framing for the next phase of TfT work.<br>- DONE | Best source for structuring the literature review chapters.                 |
| [Zheng et al. (2023), *Competent but Rigid*](https://arxiv.org/abs/2302.08807)                                                                                                                                           | AI as an equal participant in group decision-making.                         | Useful for the facilitator role and its limits.                             |
| [Terzimehić, Bühler, and Kasneci (2025), *Conversational AI as a Catalyst for Informal Learning*](https://arxiv.org/abs/2506.11789)                                                                                      | Everyday informal learning with conversational AI.                           | Good source for user-generated usage strategies outside formal TfT systems. |
| [Robinson (2024), *Study Finds 77% of Employees Report AI Has Increased Their Workload*](https://www.forbes.com/sites/bryanrobinson/2024/07/23/employees-report-ai-increased-workload/)                                  | A business context piece on AI and workload.                                 | Context for why friction-heavy designs may face resistance.                 |
| [EY Americas (2023), *New EY research reveals the majority of US employees feel AI anxiety amid explosive adoption*](https://www.ey.com/en_us/newsroom/2023/12/ey-research-shows-most-us-employees-feel-ai-anxiety)      | A survey-style context source on employee AI anxiety.                        | Context for competitive pressure and adoption anxiety.                      |

### 5. Foundational Theory Anchors From The Thesis Spec

| Source | What it is about | Why it matters now |
| --- | --- | --- |
| Bjork on **Desirable Difficulties** | Learning can improve when effort is added in the right way. | Helps justify productive friction without making it arbitrary. |
| Kapur on **Productive Failure** | Early struggle before instruction can improve later understanding. | Important for withholding-first and attempt-first strategies. |
| Wood, Bruner, and Ross on **Scaffolding** | Support should meet the learner where they are and then recede. | Important for adaptive support rather than pure challenge. |

## Reading Order

### Stage 0: Overview First (substantially complete)

Zotero notes exist for all three. Some synthesis work started on Tankelevitch 2025.

1. Tankelevitch et al. (2025) synthesis
2. Zhang et al. (2026) workshop framing
3. Tankelevitch et al. (2024) metacognitive demands

Goal: get the field map, the thesis framing, and the underlying cognitive theory in one pass.

### Stage 1: Understand The Problem (initial synthesis pass complete for core five)

The core problem-mechanism set below now has main notes, Zotero notes, and initial synthesis contributions in [[Literature Review/Synthesis/The Problem]]. Noy and Zhang remains useful as the productivity/adoption counterweight.

1. Colombatto et al. (2025)
2. Lee et al. (2025)
3. Fan et al. (2025)
4. Kreijkes et al. (2025)
5. Bastani et al. (2025)
6. Noy and Zhang (2023) — contrast source still to read/integrate

Goal: identify the strongest evidence for cognitive offloading, confidence distortion, reduced critical thinking, and the perception-performance gap. Feed findings into [[Literature Review/Synthesis/The Problem]].

### Stage 2: Extract Core Design Principles (current next priority)

1. Zhang and Reicherts (2025)
2. Rogers et al. (2025)
3. Gmeiner et al. (2025) — main note shell exists under `Literature Review/Papers/Design Papers/`; finish integration
4. Lehmann et al. (2024)
5. Lira et al. (2025)
6. Kazemitabaar et al. (2025)
7. Ashktorab et al. (2025)
8. Singh et al. (2025)
9. Sarkar (2024), *AI Should Challenge, Not Obey*
10. Sarkar (2024), *Intention Is All You Need*
11. Sarkar et al. (2024), *When Copilot Becomes Autopilot*

Goal: derive the actual intervention logic for the taxonomy: forward reasoning, scaffolding, strategic friction, challenge, prompting, and intentionality preservation — and ground the outcomes typology the framework evaluates against. Read Zhang & Reicherts 2025 and Rogers et al. 2025 as a pair: same research program, workshop paper + extended handbook chapter respectively. Feed findings into [[Literature Review/Synthesis/Design Strategies]], [[Literature Review/Synthesis/Usage Strategies]], [[Literature Review/Synthesis/AI Roles]], and [[Literature Review/Synthesis/Outcomes]].

### Stage 3: Map The Broader Strategy Landscape

1. Revisit Tankelevitch et al. (2025) with extraction in mind
2. Revisit Zhang et al. (2026) with chapter structure in mind
3. Zheng et al. (2023)
4. Terzimehić et al. (2025)

Goal: identify AI roles, outcome categories, and strategy families that can support the taxonomy and conceptual framework.

### Stage 4: Ground The Framework In Learning Theory

1. Bjork
2. Kapur
3. Wood, Bruner, and Ross

Goal: connect the HCI and GenAI literature to durable educational and cognitive theory. Feed findings into [[Theoretical Foundations]].

## Minimum Viable Must-Read Set

If time becomes tight, do not skip these:

- Tankelevitch et al. (2025) synthesis
- Zhang et al. (2026) workshop framing
- Tankelevitch et al. (2024) metacognitive demands
- Colombatto et al. (2025)
- Lee et al. (2025)
- Zhang and Reicherts (2025)
- Rogers et al. (2025)
- Gmeiner et al. (2025)
- Lehmann et al. (2024)
- Kazemitabaar et al. (2025)
- Bastani et al. (2025)
- One foundational theory source each from Bjork, Kapur, and scaffolding

## What To Extract From Each Paper

For each paper, capture these points across the Zotero note and the relevant synthesis notes:

1. What cognitive problem or opportunity the paper identifies → [[Literature Review/Synthesis/The Problem]]
2. What mechanism explains it → [[Literature Review/Synthesis/The Problem]]
3. What strategy is proposed, tested, or implied → [[Literature Review/Synthesis/Design Strategies]] or [[Literature Review/Synthesis/Usage Strategies]]
4. Whether the strategy is mainly a design strategy or a usage strategy
5. What AI role is suggested, if any → [[Literature Review/Synthesis/AI Roles]]
6. What cognitive function is being protected or augmented (tagging dimension across strategies)
7. What kind of evidence supports the claim
8. What tension or trade-off remains open → often [[Literature Review/Synthesis/Adoption and Friction]]
9. What outcome type(s) the strategy produces or targets (intermediary artifact, cognitive change, task performance) → [[Literature Review/Synthesis/Outcomes]]

## Current Working Takeaways For The Thesis

- The thesis should not frame TfT as anti-productivity; it should frame productivity-only evaluation as insufficient.
- The strongest recurring design principle is support for forward reasoning and intermediate cognition, not answer delivery.
- Design strategies and usage strategies should remain distinct, but many papers imply both at once. The literature is noticeably thicker on design strategies — that asymmetry is itself a finding.
- Confidence calibration, verification behavior, and willingness to inspect intermediate steps look central enough to become recurring variables in the literature review.
- Adoption should be treated as a core review dimension rather than a small limitations subsection.
- Workflows, not tasks, are the minimum unit of analysis — higher-order cognitive functions triggered during one task can be prerequisites for downstream tasks (tankelevitchUnderstandingProtectingAugmenting2025).

## Related Notes

- [[Thesis Overview]]
- [[Literature Review/README]]
- [[Literature Review/Synthesis/README|Literature Review/Synthesis]]
- [[Literature Review/Sources by Domain]]
- [[Glossary]]
