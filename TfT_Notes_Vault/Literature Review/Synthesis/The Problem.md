---
title: The Problem
tags: [synthesis, thesis]
status: active
---

# The Problem

This note develops the argument for why cognitive offloading with GenAI is a problem worth solving — what mechanisms drive it, which cognitive functions are at stake, and why users systematically fail to notice the loss. It will become the problem-statement section of the literature review.

Cognitive processes in focus include critical thinking, learning, and creativity (tankelevitchUnderstandingProtectingAugmenting2025).

## Current Argument

### Working Thoughts

The problem is not that users fail to think carefully — it's that GenAI generates implicit metacognitive cues (processing fluency, rapid output, polished framing) that systematically corrupt the signals users rely on to know when they're thinking carefully. Tankelevitch 2024 gives this a mechanistic spine: diminishing criterion + fluency-driven confidence inflation + self-confidence-driven offloading together explain why even well-intentioned users offload without noticing. This converges with Tankelevitch 2025's workflow-shift observation (production → critical integration): the evaluative stance that offloading presupposes is exactly the stance fluency cues disrupt.

### Synthesized Position

*To be developed as more papers accumulate.*



## Paper Contributions

### [[tankelevitchUnderstandingProtectingAugmenting2025|tankelevitchUnderstandingProtectingAugmenting2025]]
- Names the higher order cognition functions GenAI affects: metacognition, critical thinking, memory, creativity
- Current AI systems automate specifically those activities whose execution help people to learn, build skills and grow expertise. The human role shifted away from those activities towards are more detached from the actual content and 'production' activities (object level thinking) to 'critical integration' (see zotero note for definition sources)
	- This shift of how people think has observable downstream consequences in Critical Thinking (Section 2.1), Learning (Sections 2.2) and Creativity (Section 2.3) as well as Other domains (Sections 2.4)
	- The chain they're building is: AI automates the processes through which people think (writing, research, etc.) → because these processes were themselves vehicles for cognition, automating them changes what kind of thinking happens and where → one observable consequence is the workflow shift from production to critical integration → this then manifests across specific cognitive domains (critical thinking, learning, creativity) and contextual factors (workflows, expertise, motivation, well-being)
	[Page 2](zotero://open-pdf/library/items/67D5M9ET?page=2&annotation=S83EEGUS)
- AI is making it's users shift their focus from active information seeking towards more passive consumption of AI generated information which is exacerbated by the tendency of GenAI systems to agree with the users opinions leading to an 'echo chamber' effect [Page 2](zotero://open-pdf/library/items/67D5M9ET?page=2&annotation=TLQUSXZS) 
- By design, current AI systems undermine the requirements for reflective thinking as proposed by Dewey: Reflective thinking requires a "state of perplexity, confusion or doubt to catalyze inquiry (forschendes Denken / Untersuchen) and during this inquiry a suspension of judgement. The fast, polished, coherent and agreeing responses minimize the time spent in these prerequisite states creating an illusion of comprehensive understanding for the user. [Page 2](zotero://open-pdf/library/items/67D5M9ET?page=2&annotation=6MTILWRF)
- In the context of learning both prompting as well as evaluating AI output (two activities that are highly metacognitively straining; see [[tankelevitchMetacognitiveDemandsOpportunities2024|tankelevitchMetacognitiveDemandsOpportunities2024]]) are skills students often lack due to insufficient expertise in domain knowledge and/or AI utilization skills.
	- Through overreliance on AI tools to solve learning tasks students hinder their development of metacognitive strategies that are necessary for actual learning [Page 2](zotero://open-pdf/library/items/67D5M9ET?page=2&annotation=79RDJKEW) [Page 3](zotero://open-pdf/library/items/67D5M9ET?page=3&annotation=MC6LW4I3)
- There seems to be a general shift away from a direct interaction with the material towards a more mediated one with an omnipresent, (opinionated and biased) middleman. [Page 3](zotero://open-pdf/library/items/67D5M9ET?page=3&annotation=MC6LW4I3)
 - Workflows, not tasks, are the minimum unit of analysis. Task-level analysis misses cognitive damage from GenAI because higher-order cognitive functions triggered during one task can be prerequisites for downstream tasks. The paper's example: GenAI introduced too early in ideation can stifle creativity by fixating attention on specific ideas, even when it appears to help the current task. [Page 3](zotero://open-pdf/library/items/67D5M9ET?page=3&annotation=9JLE9ZBY)

### [[zhang2026tools]]
- Explicitly states that learning with the help of GenAI tools is a double-sided sword directly referencing kreijkes et al for the perception-performance paradox.[Page 2](zotero://open-pdf/library/items/MQYNRQBP?page=2&annotation=XLDP7AS9)
### [[tankelevitchMetacognitiveDemandsOpportunities2024]]
- GenAI imposes high levels of metacognitive demands on users mainly across three phases: prompting, output evaluation, and automation strategy. These metacognitive demands arise from the characteristics of GenAI that sets them apart from other tools: model flexibility, generality, and origininality.
- Cognitive offloading happens when users fail to meet the demands. The chain looks like this: GenAI tool demands high level of metacognition from the user in the three different phases due to their flexibility, generality and originality-> most users (especially novices) struggle with meeting this demand -> GenAI Systems promote offloading through their characteristics (like processing fluency) nudging the user to offload -> the user offloads the object-level thinking -> the cognitive processes that happen during the task are skipped. This reframes offloading not as laziness but as a _structural_ consequence of demand exceeding capacity.
- The extensiveness of GenAI novel content output, the relative ease of novel content generation, GenAI's unintuitive failure modes and the challenge of obtaining objective quality measures for adjusting confidence in some workflows make a correct level on reliance on AI outputs difficult
- **The Diminishing criterion effect:** Through large blocks of generated content being created at once, the cognitive load to evaluate them increases, increasing the likelihood of complete outsourcing and no validation from the user. Higher cognitive effort leads to a drop in the internal confidence threshold for accepting a solution.
- **Processing fluency** is the strongest mechanistic account of why offloading persists among engaged users. Fast, fluent AI output triggers an implicit heuristic (ease → accuracy) that inflates confidence in output _and_ in own evaluation ability; inflated confidence reduces deliberate processing.
  => The processing fluency not only affects the user's confidence in the AI output. After reading the AI's fluent summary, the user's own subsequent thinking about the topic feels more fluent too — because they now have a well-structured frame in their head. The user may experience that fluency as their own competence. The contamination is happening at the level of metacognitive experience, exactly where it's hardest to detect. [Page 9](zotero://open-pdf/library/items/JMV6BSEZ?page=9&annotation=N3UXHSLY)  and also  [Page 9](zotero://open-pdf/library/items/JMV6BSEZ?page=9&annotation=6FKJPZQP) , see for more info: [[Processing Fluency]]
- It is generally hard for users to adjust their Confidence in output evaluation, because LLM generated answers often are neither right nor wrong but rather helpful / less helpful which is very subjective. Through the difficulties objectively judging AI answers, it is therefore also difficult for users to adjust the confidence in their output evaluation of the AI's answers (§3.2, page 9)
- What determines whether people rely on AI is not how much they trust AI, but how much they trust themselves: If they are confident, they rely less on AI, if they are objectively bad at the task but self confident person through the dunning-kruger effect they may still feel confident and rely less on AI. If they are uncertain about how reliable AI is, they follow the heuristic, that they trust it when it is agreeing with the user. [Page 8](zotero://open-pdf/library/items/JMV6BSEZ?page=8&annotation=S4GYEBFS)
- GenAI has **multiple non-intuitive failure modes** (subtle errors a human wouldn't make). Existing domain expertise doesn't automatically transfer to evaluation expertise — users need a new GenAI-specific evaluation competence (§3.2.1).
- Users must have self awareness of the applicability of GenAI for their workflow, and well-adjusted confidence in their ability to complete the task manually versus with GenAI. To do that the metacognitive information need to accurately represent the user's actual skill-level that demands for a well-adjusted confidence. This is not easy to achieve as the user due to attributes of GenAI systems like high processing fluency leading to miscalibration of confidence levels

### To integrate once read
test
- `colombatto2025` — confidence dynamics in advice-taking. Likely the single strongest source for the confidence-miscalibration mechanism.
- `lee2025` — survey evidence for self-reported reductions in cognitive effort among knowledge workers.
- `fan2025` — names "metacognitive laziness" as a mechanism directly aligned with the thesis framing.
- `kreijkes2025` — experimental evidence for the perception-performance paradox in secondary schools.
- `bastani2025` — field experiment showing unguarded AI can harm later independent performance.

## Related
- [[Literature Review/Bucket/The Metacognitive Framework and the User-AI Cognitive Entanglement Problem|The Metacognitive Framework and the User-AI Cognitive Entanglement Problem]]
- [[Literature Review/Synthesis/Design Strategies]]
- [[Literature Review/Synthesis/Adoption and Friction]]
- [[Literature Review/Overview Synthesis and Reading Map]]
- [[Thesis Overview]]
