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

As suggested by colombatto2025, confidence and reliance may be in a bidirectional relationship where prospective confidence determines reliance on AI systems and output evaluation influences retrospective confidence. Due to the characteristics of GenAI systems (see tanklevitch2024) , this can lead to a miscalibration cycle due to phenomena like near-verbatim copying, verification breakdown, confidence inflation from advice exposure etc. which all can lead (due to the bidirectional relationship between confidence and reliance) to overreliance and offloading
> [!info]- AI extension:
> Colombatto operationalises the perception-performance paradox for confidence: advice exposure (not reliance, not actual output quality) causally boosts retrospective self-confidence, independent of response completeness (§3.2.3, p=.129). Users infer competence from surface cues of the interaction — fluency, verbosity, polish — not from validation. Two routes, both feeding the perception side of the paradox: <b>Exposure route (design-side trigger):</b> High prospective confidence in GenAI → advice exposure → surface cues experienced as own-competence evidence → retrospective self-confidence rises regardless of outcome quality. GenAI analogue of the Fisher/Dunn/Eliseev internet-misattribution lineage.<b>Decline route (usage-side trigger):</b> Decline advice → self-confidence also rises, either via genuine capability evidence or motivated rationalisation (colombatto2025 names both, doesn't resolve). Implication for Usage Strategies: "decline advice" can produce better epistemic outcomes (more verification, more independent work) while the confidence signal validating the strategy is itself potentially distorted.

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

### [[colombattoMetacognitionConfidenceDynamics2025]]
- Confidence both in the Advisor (in this case the GenAI system) as well as in the user's own abilities both have major impact on the user's reliance on the system. 
  Therefore a accurate confidence calibration (see tanklevitchMetacognitiveDemands2024, §3.2). 
  Accurate cofidence-calibration though, is hard to achieve with GenAI systems due to the characteristics of GenAI: extensiveness of novel content, relative ease of novel content generation, GenAI's unintuitive failure modes etc. (tanklevitchMetacognitiveDemands2024, §3.2).
- Users seeking advice were very likely to copy AI output near-verbatim (§2.2.2)
	- AI:  **Behavioural face of offloading: near-verbatim copying** (§2.2.2). 53% of advice-taken responses showed >80% cosine similarity to AI output in Study 1 (5% for declined trials); 25% vs 1% in Study 2 (§3.2.1). The voluntary-vs-forced gap (53% vs 25%) is suggestive that choice-to-seek intensifies copying beyond mere exposure, but the studies differ in other ways too.
	- 
- **Verification breakdown** (§2.2.4). Advice-takers missed the deliberately removed critical step at much higher rates. Ties in directly with my finding from tanklevitch2024, where he stated that the more text the AI created at one, the lower the confidence threshold of the user in the AI output needed to be to accept the output. 
	- 15.22% vs 30.46% inclusion in Study 1; 17.92% vs 24.68% in Study 2 (§3.2.3). Held even with a $10 monetary incentive for the most complete plan.
	- 
- Advice exposure inflates retrospective self-confidence
	- (§3.2.1). Two preregistered studies (N=200, N=300) on event-planning. Study 2's random assignment isolates a causal role for advice _exposure_ (not reliance, not outcome quality) in inflating retrospective self-confidence. Response completeness uncorrelated with retrospective self-confidence (§3.2.3, p=.129).
- **Partial-misattribution qualifier** (§4 General Discussion, p38). Confidence in _both_ self and GenAI rose with advice exposure — users appropriately attributed some credit to the system. Direct evidence for the _full_ fluency-contamination chain (where users experience AI fluency as their own competence) is therefore weaker than the exposure-confidence link alone suggests. Misattribution is real but partial.
- **Lee 2025 disagreement to watch for** (§4 General Discussion, p42). Colombatto finds confidence unrelated to verification rates; lee2025 reports higher self-confidence → more critical-thinking effort. Authors attribute the discrepancy to artificial task context and varying GenAI experience in their sample. 

### [[leeImpactGenerativeAI2025]]
- Empirical evidence that cognitive-offloading patterns extend to adult knowledge work. (up until now only learning context)
-  **Mechanised convergence as motivation**: Lee cites prior work showing GenAI-assisted workflows produce a less diverse set of outcomes for the same task than non-AI workflows, interpreted as deterioration of personal, contextualised, reflective judgment. Empirical motivation alongside Tankelevitch's mechanistic account of why offloading happens. [Page 2](zotero://open-pdf/library/items/IFM766NF?page=2&annotation=FPIQTGIA)
- **Real-world complementary evidence for the production → critical integration shift**: Lee's survey provides cross-occupation, real-world evidence that knowledge workers shift from task execution to oversight under GenAI — complementing the controlled, narrow-domain studies that previously grounded this claim. Strengthens the workflow-shift argument already credited to `tankelevitchUnderstandingProtectingAugmenting2025`. [Page 2](zotero://open-pdf/library/items/IFM766NF?page=2&annotation=RRMC3S9A)
- **Confidence duality in critical-thinking enaction**: Confidence in AI leads to less perceived enaction of critical thinking and self-confidence in doing the task oneself leads to higher perceived enaction of critical thinking -> There is a tradeoff here between higher higher cognitive load and the risk of cognitive offloading (§4.2) and [Page 12](zotero://open-pdf/library/items/IFM766NF?page=12&annotation=8LL7XDDK)
	- AI bullet:
	  Task-specific confidence in GenAI negatively predicts self-reported enaction of critical thinking (β=-0.69, p<0.001); confidence in doing the task oneself positively predicts it (β=0.26, p=0.026), and confidence in evaluating AI responses also positively predicts it (β=0.31, p=0.046). Adds survey-level convergence on top of `tankelevitchMetacognitiveDemandsOpportunities2024`'s theoretical account and `colombattoMetacognitionConfidenceDynamics2025`'s behavioural results.
- **The effort–engagement paradox.** Higher AI-confidence correlates with _less_ self-reported critical thinking and with _perceived reduction_ in effort for 5/6 Bloom activities; higher self-confidence correlates with _more_ self-reported critical thinking and _greater_ perceived effort (especially Application and Evaluation). The two confidence axes pull in opposite directions on both enaction and experienced effort. _(§6.1.1, p14)_
- **Offloading explicitly tied to low self-confidence**: Lee names the mechanism: lower self-confidence leads users to rely more on AI, "diminishing their critical engagement and independent problem-solving skills... a form of cognitive offloading [Engelbart]." Direct bridge from Lee's confidence findings to Tankelevitch's offloading account. [Page 14](zotero://open-pdf/library/items/IFM766NF?page=14&annotation=ZQLBTUQF)
 
### To integrate once read
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
