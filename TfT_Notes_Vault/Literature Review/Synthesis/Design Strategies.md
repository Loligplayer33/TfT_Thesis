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

### [[Literature Review/Overview Papers/tankelevitchUnderstandingProtectingAugmenting2025|tankelevitchUnderstandingProtectingAugmenting2025]]
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
- 
### To integrate once read
- `zhangReicherts2025` — process-oriented support and forward reasoning. Likely the single strongest source for the forward-reasoning principle.
- `kazemitabaar2025` — cognitive engagement techniques in programming education.
- `singh2025` — metacognitive prompts in GenAI search.
- `sarkar2024a` — AI as provocateur ("AI Should Challenge, Not Obey").
- `sarkar2024b` — "Intention Is All You Need" — intentionality preservation as a design principle.
- `minXia2024` — feedforward design as a fundamental GenAI component.
- `liu2024` — proactive conversational agents with inner thoughts (feedforward in action).
- `gmeiner2024` — metacognitive support agents in AI-assisted design.

## Related
- [[Literature Review/Synthesis/The Problem]]
- [[Literature Review/Synthesis/AI Roles]]
- [[Literature Review/Synthesis/Usage Strategies]]
- [[Literature Review/Synthesis/Adoption and Friction]]
- [[Literature Review/Synthesis/Theoretical Foundations]]
- [[Literature Review/Overview Synthesis and Reading Map]]
- [[Thesis Overview]]
