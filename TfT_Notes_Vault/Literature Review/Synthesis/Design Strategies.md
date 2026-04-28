---
title: Design Strategies
tags: [synthesis, thesis]
status: active
---

# Design Strategies

This note is the working taxonomy of system-side interventions — concrete design patterns that keep users cognitively engaged when working with GenAI. Strategies are grouped by mechanism (withholding, process-oriented support, scaffolding, provocation, transparency/explainability, customizability, intervention timing), not by paper. Intervention timing — on-demand, sequential, dynamic — is treated here as a cross-cutting design dimension that applies across strategies. When this note gets long enough that mechanism families start to crowd each other, individual families can split into their own notes.


## Current Argument

### Working Thoughts

Design strategies have to find the correct level of 'directness' to ensure that the tools are not annoying the user and still remain useful to not get abandoned completely. The design strategies might need to nudge the user towards engaging more in valuable cognitive demanding tasks. If the AI is not answering any outcome-based questions and always blatantly points out errors by f.e. playing the devil's advocate, the user will be annoyed to the point where the tool just gets deactivated. I think it is extremely important that the tool is actually useful to the user. Restricting capabilities will ultimately lead to the deactivation of the tool. This usefulness should extend the existing usefulness of a "vanilla" integrated AI tool with proactive, native support (a well-meaning expert that helps you to perform the task at hand).

This argument — _directness as dimension_ and _redirect-rather-than-refuse_ — is directly strengthened by (tankelevitchMetacognitiveDemandsOpportunities2024). Directness matters because metacognitive capacity for receiving support varies (high-directness assumes monitoring capacity that may not exist). Gu et al.'s think/reflection/exploration modes (§4.1.3) are an operationalisation of your redirect move.

Tankelevitch et al. suggest two categories of strategies to address the high cognitive load that might be valuable here (tankelevitchMetacognitiveDemandsOpportunities2024). Generally the utilization of design strategies need to be well calibrated and are probably highly dependent on both the domain and use-case.

The concept of process-oriented support is very promising. But the complete exclusion of workflow / end-to-end support (meaning support on more abstract levels requiring higher-order cognitive functions) may lead to deactivation of the tool because it is less helpful. Instead this kind of request has to be identified by the system as one requiring higher-order cognition. Once recognized, the system should not openly refuse an answer BUT BE HELPFUL INSTEAD — f.e. by summarizing or visualizing what the current status is, what are still open points, and maybe some questions that help the user determine how to continue. Maybe this can be done through nudging?

> [!note]- Thoughts from AI about this
> Your argument is good, and it addresses a real gap in how process-oriented support is typically framed. The standard presentation sets up a binary — process-oriented vs. end-to-end — and implies you should pick one. Your point is that from the user's perspective, a system that refuses to help with a complex request is just unhelpful, and unhelpful tools get abandoned. The move you're proposing is more subtle: the system recognizes the request requires higher-order cognition and redirects the form of help rather than withholding it. Summarizing the current state, surfacing open questions, visualizing what's unresolved — that's still genuinely useful output, but it keeps the cognitive work of synthesis and decision-making with the user. That's a stronger design position than "just add friction," because the user doesn't experience it as a refusal. They experience it as a different kind of help. The nudging framing fits here — the system shapes what the user does next without blocking them.

Design strategies (especially in domains where productivity in the present task is valued the most) need to demonstrate the value created through 'extra' cognitive work to build intrinsic motivation in the user to choose this tool over another (tankelevitchUnderstandingProtectingAugmenting2025, p. 5). Another even better option would be if the design strategies protecting/augmenting the user's cognition are as helpful as possible themselves.


**Open question to revisit as more papers land:** how to create and incorporate design strategies into a tool such that it provides tangible help to the user in the task at hand. Is this even possible?



### Synthesized Position

*To be developed as more papers accumulate. Candidate threads from Working Thoughts that are already showing up in multiple sources:*
- *Directness as an organizing dimension for design strategies (has tankelevitchUnderstandingProtectingAugmenting2025; needs corroboration).*
- *The redirect-rather-than-refuse move as a resolution to the process-oriented / end-to-end tension (currently one paper + your argument; watch for whether gmeiner2024, zhangReicherts2025, or kazemitabaar2025 support it).*

## Paper Contributions

### [[tankelevitchUnderstandingProtectingAugmenting2025|tankelevitchUnderstandingProtectingAugmenting2025]]
- It is not only about protecting, but also about augmenting cognition. (Those are two different dimensions though and might require different types of design strategies)
- 'directness' by which AI systems are designed to augment the user's cognition is identified as one key dimension so classify different types of design strategies. Directness describes how explicit the design strategy follows the goal to augment the user's cognition and how obvious it is to the user. Solutions range from direct challenging through provocations over providing formal structure and scaffolding to emotional and motivational pathways [Page 4](zotero://open-pdf/library/items/67D5M9ET?page=4&annotation=9CHQB34R)
- Process-oriented support as a way for AI to assist users in taking the right steps and gather the right information to solve a problem themselves by reasoning forward towards their own solution [Page 4](zotero://open-pdf/library/items/67D5M9ET?page=4&annotation=DDTKP6FY) 
- Khurana & Chilana's conditions for when process-oriented support is appropriate: when users are less familiar with a task, when the task involves complex decision-making or creativity (rather than routine steps), or when users have learning goals rather than solely performance goals. Qualifies process-oriented support as non-universal. [Page 4](zotero://open-pdf/library/items/67D5M9ET?page=4&annotation=J6UDESA7) 
- Surfaces specific strategy patterns: metacognitive support agents asking reflective questions tied to structuring activities (Gmeiner et al.). **Reflective questioning needs to be linked to structuring activities** [Page 5](zotero://open-pdf/library/items/67D5M9ET?page=5&annotation=R4T2KAKY) -> also see source 44 there for the full paper
- the system's usefulness cannot be reduced noticeably, especially not, if the user cannot directly "feel" the benefit it gains from the reduction because this reduction got traded in against another tangible benefit [Page 5](zotero://open-pdf/library/items/67D5M9ET?page=5&annotation=V769FUXI)
- A combination of genuinely helpful scaffolding with provocation strategies such that the user interacts enough with the material to utilize higher order cognitive functions, while relying on scaffolding for productivity gains [Page 5](zotero://open-pdf/library/items/67D5M9ET?page=5&annotation=XYMG23S9)
- Transformation of content across modalities can augment cognitive workflows (related to the obsidian canvas?) [Page 5](zotero://open-pdf/library/items/67D5M9ET?page=5&annotation=L5B2PSV3)
- Discusses different types of interaction types possible: From traditional turn-based conversations to feed-forward prompting to feedforward information [Page 6](zotero://open-pdf/library/items/67D5M9ET?page=6&annotation=9Y78FDY5)
- Raises UI differentiation (provenance marking of AI vs. human content) as a design question with implications for metacognition [Page 7](zotero://open-pdf/library/items/67D5M9ET?page=7&annotation=D92QGMV6)

### [[zhang2026tools]] 
- The design of the TfT should focus on how it shapes, supports or extends thinking by capturing results of thought intensive activities. The outcomes should therefore be more focussed on the reshaping of the thinking (in a positive way) than the sole productivity gain [Page 3](zotero://open-pdf/library/items/MQYNRQBP?page=3&annotation=LD9CX95C)
  (Outcomes are separate from design strategies - may need to put them in an own synthesis file)

### [[tankelevitchMetacognitiveDemandsOpportunities2024]]
- Tanklevitch argues that metacognitive demands are one of the main reasons why cognitive offloading happens. Thereby, through the reduction of metacognitive demands offloading could be minimized [Page ](zotero://open-pdf/library/items/JMV6BSEZ?page=1&annotation=W9NR7UPB)
- (§2.5) provides the theoretical justification for design strategies like seamful design and deliberate disfluency. 
- **The Diminishing criterion effect:** Through large blocks of generated content being created at once, the cognitive load to evaluate them increases, increasing the likelihood of complete outsourcing and no validation from the user. Higher cognitive effort leads to a drop in the internal confidence threshold for accepting a solution.
  A System Requirement can be derived from this: The way large blocks of novel content is presented to the user has to be in smaller fragments [Page 9](zotero://open-pdf/library/items/JMV6BSEZ?page=9&annotation=YZD7P57D) 
- Proposes two complementary directions to address the cognitive demands of GenAI systems:
  1. improve user's metacognition via support strategies
  2. Reduce metacognitive demand via explainability and customizability
- Three metacognitive support strategies: **planning** (goals, task decomposition; supported by prompt chaining, feedforward), **self-evaluation** (reflective prompts, uncertainty probing, "not sure" options, think-aloud), **self-management** (context-aware timing, state detection, flow/exploration adaptation) (§4.1.1–4.1.3).
- **Feedforward design** (distinct from feedback): system invites an action and communicates what to expect. Addresses fuzzy abstraction matching by externalising tacit user intentions (§4.1.1).
- Well-timed reflective prompts improve self-awareness and confidence calibration during cognitively demanding tasks (§4.1.2)
- Context-aware AI systems self-determine the correct intervention time and format based on user actions and other variables. This intervention timing is a cross-cutting design dimension, not a strategy. Support can be on-demand, sequential, or dynamic/continuous. Same reflective-question strategy has very different cognitive and adoption consequences depending on timing (§4.1.3, §4.3) [Page 15](zotero://open-pdf/library/items/JMV6BSEZ?page=15&annotation=VLCAT2YG)
  => Interesting but extremely difficult to implement correctly
- Explainability - the degree of enablement provided for user's to understand whether the AI can achieve their goals. Explainability can help the users to adjust their confidence levels in the AI (§4.2.1)
- **Seamful design** as legitimate friction (§4.3): "some potential effort introduced by metacognitive support strategies may be justified, so long as these are well-designed and act in the service of improved metacognition and productivity." Warrant for the Working-Thoughts position that _friction is not the problem; ineffective friction is_.
- **Seamful design** as legitimate friction (§4.3): "some potential effort introduced by metacognitive support strategies may be justified, so long as these are well-designed and act in the service of improved metacognition and productivity." Warrant for the Working-Thoughts position that _friction is not the problem; ineffective friction is_.

### [[colombattoMetacognitionConfidenceDynamics2025]]
- Both self- and system confidence influence reliance on AI systems in opposite ways and are NOT correlated with one another. Design strategies targeting one axis may be combinable orthogonally with strategies targeting the other. The paper does not test this design-implication directly (§2.2.2)
- **Verbosity-verification tradeoff is a design variable** (§4 General Discussion, p42). Detail/length of AI output and user verification trade off when output may contain inaccuracies. Implication: the _form_ of output is a design choice with cognitive consequences, not just its presence/absence. Note: the paper observes this as an emergent property of ChatGPT's default verbosity, not as a manipulated variable, so the strength of the design claim depends on extension to systems with controllable verbosity.
	- <b>The verbosity-verification tradeoff is named explicitly in the paper.</b> Your notes have both halves (verbose copying, missed verification) but don't name it as a tradeoff. p42: the paper says output detail (furnished by verbosity of many GenAI systems) and response verification trade off against each other when outputs may contain inaccuracies. This is highly citable and connects directly to your Design Strategies Working Thoughts argument about redirect-rather-than-refuse — verbosity is a design choice with measurable cognitive consequences. [Page 42](zotero://open-pdf/library/items/47Q4FLQL?page=42&annotation=F8EPUA4N)
- People that voluntarily seek AI advice are much more likely to cognitively offload the whole task to AI than those where the AI advice was forced upon them [Page 41](zotero://open-pdf/library/items/47Q4FLQL?page=41&annotation=SBGTPNNB)=> This finding seems kind of obvious does not necessarily allow a conclusion to be made regarding a design strategy. Obviously people that seek advice are more likely to offload the tasks (otherwise they wouldn't have sought help in the first place)
- Names design strategies in the form of interventions that might help with better calibrated self- and system confidence:
	- In AI: providing background information on AI systems, uncertainty expressions in natural language, uncertainty highlighting / disclaimers
	- Self-confidence calibration has been underexplored
	[Page 42](zotero://open-pdf/library/items/47Q4FLQL?page=42&annotation=M3FCNYYX)

### [[leeImpactGenerativeAI2025]]
- **Three intervention levers: awareness, motivation, ability.** Lee et al. propose interventions that (1) raise awareness of critical-thinking opportunities (proactive interrupts vs. reactive on-request assistance), (2) raise motivation by framing CT as skill-development rather than per-task co-auditing, and (3) raise ability via features supporting inspection, refinement, and argument-analysis. The levers mirror the three inhibitor types from §4.3.2. _(§6.1.2, pp14–15)_
- **Explicit user controls over the extent of AI assistance.** Lee et al. recommend surfacing controls that let users regulate AI involvement based on their confidence in themselves and in the AI. Reinforces the customizability-as-both-design-and-usage-strategy pattern from `tankelevitchMetacognitiveDemandsOpportunities2024` (§4.2.2); the finding that the two confidence axes pull in opposite directions gives that customizability argument empirical grounding. _(§6.1.1, p14)_
- **AI explanations as questions rather than statements**: Lee cites prior work (ref [24]) showing that presenting AI explanations as questions improves logical discernment. Concrete pattern that operationalises the Socratic / forward-reasoning move and supports the redirect-rather-than-refuse argument in Working Thoughts. _(§2 Related Work)_ [Page 3](zotero://open-pdf/library/items/IFM766NF?page=3&annotation=5ILQQP8T)
- **Feedback mechanisms aligned with explainable AI**: Lee's design recommendation pairs explicit user controls (already integrated above) with feedback mechanisms that help users gauge AI output reliability — when to trust AI vs. apply own critical thinking — explicitly aligned with explainable AI goals. The accountability framing matters: even with such mechanisms, the user must remain responsible for the outcome. Connects to `tankelevitchMetacognitiveDemandsOpportunities2024` §4.2.1 on explainability as a metacognitive-demand-reducing strategy. _(§6.1.1, p14)_ [Page 14](zotero://open-pdf/library/items/IFM766NF?page=14&annotation=7Q5EJB7Y)

### To integrate once read
- `zhangReicherts2025` — process-oriented support and forward reasoning. Likely the single strongest source for the forward-reasoning principle.
- `kazemitabaar2025` — cognitive engagement techniques in programming education.
- `singh2025` — metacognitive prompts in GenAI search.
- `sarkar2024a` — AI as provocateur ("AI Should Challenge, Not Obey").
- `sarkar2024b` — "Intention Is All You Need" — intentionality preservation as a design principle.
- `minXia2024` — feedforward design as a fundamental GenAI component.
- `liu2024` — proactive conversational agents with inner thoughts (feedforward in action).
- `gmeinerExploringPotentialMetacognitive2025` — metacognitive support agents in AI-assisted design.

## Related
- [[Literature Review/Synthesis/The Problem]]
- [[Literature Review/Synthesis/AI Roles]]
- [[Literature Review/Synthesis/Usage Strategies]]
- [[Literature Review/Synthesis/Adoption and Friction]]
- [[Theoretical Foundations]]
- [[Literature Review/Overview Synthesis and Reading Map]]
- [[Thesis Overview]]
