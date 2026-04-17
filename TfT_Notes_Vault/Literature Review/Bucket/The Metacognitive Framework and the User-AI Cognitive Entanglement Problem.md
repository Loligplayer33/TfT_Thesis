
## Context

This note captures a discussion about whether and how the metacognition framework from Tankelevitch et al. (2024), *The Metacognitive Demands and Opportunities of Generative AI*, needs to be extended to account for the cognitive entanglement between users and AI systems. The framework (Figure 1 in the paper) describes metacognition as operating on the user's own cognition. The question is whether this boundary holds when GenAI fundamentally shapes the user's thinking.

**Source paper:** Tankelevitch et al. (2024), [arXiv:2312.10893](https://arxiv.org/abs/2312.10893)

---

## The Framework As Stated

Tankelevitch et al. present a simplified descriptive framework for metacognition with four components:

- **Metacognitive knowledge** (explicit): what you consciously know about your own abilities, strategies, and beliefs.
- **Metacognitive experiences** (implicit): feelings like familiarity, processing fluency, gut-level cues about cognitive processes.
- **Metacognitive monitoring** (ability): assessing your own thinking — self-awareness, confidence calibration.
- **Metacognitive control** (ability): directing your own thinking — task decomposition, metacognitive flexibility.

The architecture flows: knowledge and experiences feed into monitoring, monitoring informs control, and control acts upon **object-level cognition** — the user's task-specific cognitive work.

The paper argues that GenAI places unusually high **demands** on these metacognitive capacities. The user needs more self-awareness, better confidence calibration, greater flexibility, and stronger task decomposition to work effectively with GenAI.

---

## The Initial Observation: Extending to the User-AI System

The framework scopes metacognition to the user's own cognition. But when someone works with GenAI, the effective cognitive system producing outcomes is a **user-AI composite**. This suggests the framework may need extension in at least two directions:

### 1. Metacognitive Information About the AI

The user needs metacognitive knowledge and experiences that cover the AI, not just themselves:

- **Metacognitive knowledge about the AI:** Knowing the AI's capabilities, limitations, failure modes, biases. If the user lacks this knowledge, their metacognitive monitoring of the composite system is degraded — they can't accurately assess the quality of thinking that incorporates AI contributions.
- **Metacognitive experiences about the AI:** Something like a gut-level "this feels fishy" signal about AI output — analogous to the feeling of familiarity or processing fluency, but directed at an external system's output that has been partially incorporated into one's own reasoning. The framework doesn't have a clean place for this kind of experience because it's not about one's own cognition in the traditional sense.

### 2. Metacognitive Monitoring of the Composite System

If the user extends their thoughts through AI-generated content, monitoring only the user's own cognition while the actual system performing the task is a user-AI symbiosis leads to inaccurate self-assessment. Confidence calibration, for instance, becomes confidence in the joint system's output, not purely in one's own judgment.

---

## The Counterargument: Why the Framework Draws the Boundary Where It Does

Metacognition, as defined in the psychological literature this paper draws on (Nelson & Narens, Flavell, Ackerman & Thompson), means specifically **cognition about one's own cognition**. That's not an arbitrary scope restriction — it's the definition.

When you assess whether an AI answer might be hallucinated, that's closer to **evaluation of an external source** than to metacognitive monitoring in the technical sense. The paper flags this boundary explicitly in §3.2: confidence in the system's abilities is important and interacts with self-confidence, but the paper deliberately scopes to self-confidence because that's the metacognitive concept.

### The Extended Mind Thesis as a Possible Bridge

There is a theoretical path that would make the extension coherent: the **extended mind thesis** (Clark & Chalmers, 1998 — cited in the CHI 2025 TfT workshop synthesis). If the AI is genuinely part of the user's cognitive system — not just a tool but an extension of their mind — then monitoring AI outputs *is* monitoring one's own cognition, because the boundary of "one's own cognition" has expanded.

Under that framing:

- Metacognitive knowledge includes knowing the AI's capabilities because the AI is part of you.
- Metacognitive experiences include "this feels off" about AI output because that output is part of your extended cognitive process.

**The problem with this move:** It's a strong philosophical commitment, and it's contested. Most people using GenAI are not in an extended-mind relationship with it — the extended mind thesis typically requires conditions like trust, reliability, and tight integration that current GenAI doesn't consistently meet.

---

## Why the Boundary Actually Cannot Hold: The Entanglement Argument

The counterargument above defends the framework's boundary by saying: the AI is external, and assessing it is source evaluation, not metacognition. But this defense fails under realistic conditions of sustained GenAI use. Here is why.

### The Contamination Problem

The framework assumes a clean architecture: metacognitive monitoring and control sit at the meta-level and operate on object-level cognition that is **the user's**. The "task-specific, cognitive demands (object level)" box in Figure 1 is implicitly the user's cognitive work on the task.

But GenAI contaminates that object level. When someone reads an AI-generated summary, their subsequent thinking incorporates it — the framing, the emphasis, the omissions. Over time, through repeated interaction, the user genuinely **cannot perform the attribution** you'd need to apply the framework cleanly.

This is not a matter of laziness or insufficient effort. Influence on thought doesn't work that way. You cannot introspect your way back to which premise came from you versus the AI, any more than you can trace which ideas in a long conversation came from which participant. The influence is absorbed, integrated, and experienced as one's own thinking.

### What This Means for the Framework

When the framework says "metacognitive monitoring: assess your own thinking," what thinking is being assessed? A **hybrid product** that the user experiences as their own but that was substantially shaped by an external system with its own biases, gaps, and confident-sounding errors.

- **Confidence calibration** is now calibrating against a signal that's already been distorted by the AI's influence on the user's reasoning.
- **Self-awareness** is awareness of a cognitive state that is not purely one's own.
- **Processing fluency** cues from the AI's polished output don't just affect evaluation of the AI's output — they seep into the user's experienced fluency of their own subsequent thinking.

The monitoring is still happening — it's still the user's metacognitive ability — but it is **operating on corrupted input**. The user's object-level cognition is no longer a clean signal about the user's own reasoning.

### The Conclusion Is Not That the Framework Is Useless

The framework correctly describes the cognitive machinery. What it underestimates is the severity of the problem it's facing. The paper treats the challenge as one of **demand** — the user needs to do more metacognitive work. The entanglement argument shows that even if the user does that work perfectly, they are monitoring a system they can no longer fully observe.

It is not just that metacognition is hard with GenAI. It is that the **conditions under which metacognition works** — having access to your own cognitive states and being able to assess them — are partially undermined by the entanglement of user and AI contributions.

---

## Design Implications for the Thesis

This shifts the design logic in a concrete way.

### If You Accept Only the Tankelevitch Framing

The solution is to **support users' metacognition** — help them monitor and control better through planning support, self-evaluation prompts, and self-management strategies.

### If You Accept the Entanglement Extension

There is an additional design requirement: **make the hybrid nature of the cognition visible and traceable** so that metacognitive monitoring has something clean to operate on. This means:

1. **Provenance marking:** Visually separating AI-generated content from user-generated content in the interface so the user can track what came from where.
2. **Requiring independent intermediate artifacts:** Making the user produce their own reasoning *before* seeing AI output, so their independent thinking is preserved as a reference point.
3. **Preserving cognitive baselines:** Structuring workflows so the user's pre-AI thinking is recorded alongside the AI-influenced thinking, enabling comparison.
4. **Forward reasoning as a precondition for metacognition:** Process-oriented support (Zhang & Reicherts, 2025) asks users to reason forward to their own solution rather than backward from an AI-generated one. This isn't just a pedagogical choice — given the entanglement problem, it's a **precondition** for metacognition to function at all in a GenAI context, because it produces a clean cognitive object (the user's own reasoning) before the AI's influence enters.

### Connection to Existing Notes

- The question of whether the UI should differentiate between user- and AI-generated content (flagged in the Tankelevitch 2025 synthesis annotations) connects directly here — it's not just a design nicety but a requirement for metacognitive monitoring to work.
- The friction–scaffolding tension (from the same annotations) gains a new justification: scaffolding that preserves the user's independent reasoning isn't just better for learning — it's necessary for the user's metacognition to have a clean signal.
- The design principle of "redirecting help rather than refusing it" (from the 2025 synthesis notes) can incorporate this: when the system redirects, it should do so in a way that makes the user's own current state of thinking visible (summaries, open questions, status visualizations) rather than blending AI contributions invisibly into the user's reasoning.

---

## Recommended Position for the Thesis

Note the entanglement problem as a **genuine limitation of the Tankelevitch metacognitive framework** when applied to sustained GenAI use. Use it to motivate design strategies that preserve **cognitive traceability** — the user's ability to distinguish their own reasoning from AI-influenced reasoning. Connect it to the forward-reasoning principle (Zhang & Reicherts, 2025) as the strongest existing design response to this problem.

Do not attempt to build the extended framework — that's a theoretical contribution beyond thesis scope. Instead:

1. Name the gap in the literature review.
2. Show that your strategies address it.
3. Position cognitive traceability as a design requirement that emerges from taking the metacognitive framework seriously in a GenAI context.

---

## Related Notes

- [[Literature Review/zotero_notes/tankelevitchMetacognitiveDemandsOpportunities2024-zotero-notes|Tankelevitch et al. (2024) Zotero Notes]]
- [[Literature Review/zotero_notes/tankelevitchUnderstandingProtectingAugmenting2025-zotero-notes|Tankelevitch et al. (2025) Synthesis Zotero Notes]]
- [[Literature Review/Overview Synthesis and Reading Map]]
