---
title: Theoretical Foundations
tags: [synthesis, thesis]
status: active
---

# Theoretical Foundations

This note connects the GenAI-specific findings from HCI research back to durable theoretical anchors — Desirable Difficulties (Bjork), Productive Failure (Kapur), Scaffolding and the Zone of Proximal Development (Vygotsky; Wood, Bruner & Ross), and the metacognitive framework (Tankelevitch et al.). The goal is to show that the strategies extracted from the literature are grounded in well-established cognitive and educational theory rather than ad hoc design patterns. Precision matters here: HCI "scaffolding" often drifts from its Vygotskian meaning, and that kind of slippage should be caught and named.

## Current Argument

### Working Thoughts
(tankelevitchMetacognitiveDemandsOpportunities2024) is the connective tissue between the learning-theory anchors (Bjork, Kapur, Vygotsky) and the HCI/GenAI papers. Desirable Difficulties justifies why friction helps; the metacognitive framework specifies _what cognitive capacities the friction is protecting and activating_. Without that middle layer, the thesis would either be learning theory applied by analogy to GenAI, or HCI design patterns without theoretical justification. The paper's framework is what makes the bridge coherent.

Fan introduces a complementary theoretical pair: Risko & Gilbert (2016) cognitive offloading and Alter et al. (2007) disfluency-System 2. The Alter frame is the dual-process complement to processing fluency from `tankelevitch2024` — AI fluency removes the disfluency cue that would otherwise trigger analytical thinking. Worth citing alongside Tankelevitch whenever the laziness mechanism is introduced. SRL theory (Zimmerman) appears in Fan as measurement scaffolding, not as architectural frame; not a candidate for the thesis's primary cognitive frame.

### Synthesized Position
//to fill later on

## Paper Contributions

### [[tankelevitchUnderstandingProtectingAugmenting2025|tankelevitchUnderstandingProtectingAugmenting2025]] 
- Makes a direct connection back to (tankelevitchMetacognitiveDemandsOpportunities2024) by arguing that the decision process of offloading to GenAI in itself is an emerging kind of meta-expertise. One that requires a lot of metacognitive effort (as argued by tanklevitch in the paper above) [Page 4](zotero://open-pdf/library/items/67D5M9ET?page=4&annotation=ZKBU9BUT)
- Lists the theories the field is drawing on but not yet systematically integrating: Bloom's Taxonomy, Dewey's reflective thinking, Schön's reflection model, Sawyer's creativity model, Hammond's Cognitive Continuum Theory, dual-process theories, metacognition theory, pragmatism [Page 8](zotero://open-pdf/library/items/67D5M9ET?page=8&annotation=QSEARWP2)
- Flags Dewey's traceability property as a potential lens for characterizing thinking-with-AI
- Flags Dervin's sense-making theory (cognitive gaps and bridges) as an underused frame

### [[tankelevitchMetacognitiveDemandsOpportunities2024]]
- Differentiation between object-level and meta-level cognition. The first one describing those activities involved with the specific task execution like perceiving, remembering, classifying, deciding etc and the latter describing those cognitive activities that monitor the object-level activities assessing their functioning and allocating cognitive resources accordingly. [Page 2](zotero://open-pdf/library/items/JMV6BSEZ?page=2&annotation=7AIQEPS3)
- Provides the descriptive metacognitive framework my thesis will lean on consisting of the two sources of metacognitive information for understanding one's own cognition (metacognitive knowledge and -experience) as well as two metacognitive abilities for assessing and guiding one's own cognition (metacognitive monitoring and -control).
	- The metacognitive information and Metacognitive abilities are interconnected [picture](obsidian://open?vault=TfT_Notes_Vault&file=Literature%20Review%2Fzotero_notes%2FtankelevitchMetacognitiveDemandsOpportunities2024-zotero-notes-assets%2Fannotation-4-x50-y444.png)
	=> See glossary for definitions
- Confidence has two formally independent aspects: **calibration** (overall level matches overall accuracy) and **resolution** (discriminates correct from incorrect). Both can fail independently (§2.2).  Strategies may fix one without the other.
- Human Heuristics that determine how much metacognition is necessary for completing a task is primeable. This mean, by triggering those heuristics through TfT (design) strategies, metacognition can be provoked. (f.e. processing fluency is a heuristic that can be triggered by a degraded font) (§2.5)
- Metacognition is teachable and improvable (§2.6) - since metacognition is a precondition for all other types of valuable cognition, TfT strategies that act on metacognition are very promising.
- Metacognitive demand != cognitive load. But metacognitive demand substantially contributes to overall cognitive load.
- The three main activities imposing high levels of cognitive demand and therefore cognitive load on the user are: Prompting GenAI systems (§3.1), Evaluating and relying on generative AI output (§3.2),  Automation strategy and generative AI workflows (§3.3)

### [[colombattoMetacognitionConfidenceDynamics2025]]
- operationalization of confidence into prospective and retrospective confidence (see Glossary)
- Argues for a bidirectional relationship between confidence and reliance: prospective confidence determines reliance on the output, and output evaluation influences retrospective confidence. (See problems though: verification breakdown and near verbatim copying as well as confidence inflation from advice exposure)
- Confidence doesn't just gate whether users request advice — it continuously shapes how much of it they actually incorporate once requested. The two confidence axes (self, GenAI) push in opposite directions on reliance and operate independently (no interaction). (§2.2.2)
- **Key finding:** decisions to request and rely on GenAI advice were associated with higher prospective confidence in the GenAI, and lower confidence in participants’ own abilities” [Page 22](zotero://open-pdf/library/items/47Q4FLQL?page=22&annotation=3VWL93H4) 
- Changes in confidence from prospective to retrospective measures suggest that completing a task boosts users’ own confidence in their ability, while receiving support from a GenAI might boost confidence in the capabilities of the GenAI instead.” - A key result from study 1 [Page 23](zotero://open-pdf/library/items/47Q4FLQL?page=23&annotation=54XQ3AKW)
- Key finding of study 2: Exposure to GenAI advice leads to increases confidence in the GenAI - no matter if they sought advice or not. => This finding may also be caused by the fact that people just structurally underestimated the capabilities of GenAI in 2024 when this study was conducted and does not implicate a general behavior that usage of GenAI always increases the confidence in it.[Page 28](zotero://open-pdf/library/items/47Q4FLQL?page=28&annotation=DN4X65H6)
- The increased self-confidence and confidence in the system gained through genAI advice exposure did NOT carry over to other occasions (§3.2.2)

### [[leeImpactGenerativeAI2025]]
- **Risko & Gilbert (2016) cognitive offloading as theoretical anchor.** Reliance on external resources reduces internal cognitive engagement, leading to a habitual reduction in monitoring and self-regulation. Fan adopts this as one of the two foundational frameworks for metacognitive laziness. (§1, p4; §5.2, p17)
- **Alter et al. (2007) disfluency-System 2 as the dual-process complement.** Metacognitive experiences of difficulty or disfluency activate analytical (System 2) reasoning. AI's fluency removes the disfluency cue that would otherwise trigger analytical thinking — the dual-process counterpart to processing fluency in `tankelevitch2024`. Cite Alter alongside Tankelevitch when introducing the laziness mechanism. (§1, p4; §5.2, p17)



### To integrate once read
- Bjork — Desirable Difficulties. The canonical source for why strategic difficulty improves learning.
- Kapur — Productive Failure. Struggle-before-instruction as a learning mechanism.
- Vygotsky / Wood, Bruner & Ross — Scaffolding and the ZPD. The original theoretical frame that HCI borrows from, often loosely.

## Related
- [[Literature Review/Synthesis/Design Strategies]]
- [[Literature Review/Synthesis/AI Roles]]
- [[Literature Review/Bucket/The Metacognitive Framework and the User-AI Cognitive Entanglement Problem|The Metacognitive Framework and the User-AI Cognitive Entanglement Problem]]
- [[Literature Review/Overview Synthesis and Reading Map]]
- [[Thesis Overview]]
