---
tags:
  - literature-review
  - design-strategies
  - metacognition
type: source
status: in-progress
---
# Those notes are AI generated for now
# Exploring the Potential of Metacognitive Support Agents for Human-AI Co-Creation

## Zotero

- Citekey: `gmeinerExploringPotentialMetacognitive2025`
- [Open in Zotero](zotero://select/library/items/LXST6CGF)
- [Source URL](http://arxiv.org/abs/2506.12879)
- [[Literature Review/zotero_notes/gmeinerExploringPotentialMetacognitive2025-zotero-notes|Open imported Zotero notes]]

## What This Paper Helps Me See

- Metacognitive support for GenAI-assisted tasks is not a single strategy but a *family* of strategies with different cognitive mechanisms and different effectiveness profiles.
- Reflective questioning alone has limits — it fails to break through solidified incorrect assumptions. Combining questioning with structuring activities (planning, sketching, visualizing) is more robust.
- Voice-based agents can reduce the cognitive load of metacognitive support by not competing with the visual-spatial modality of the primary task (in this case, 3D CAD design).

## Key Concepts

- **Metacognitive support agents** — AI systems designed not to solve the task but to scaffold the user's *thinking about* the task (reflection, planning, intent formulation, evaluation).
- **Three design probes tested via Wizard-of-Oz:**
	1. **SocratAIs** — asks reflective questions to prompt reflection-in-action (Socratic questioning approach).
	2. **HephAIstus** — prompts task planning and diagramming, supported by suggestions for design strategies and software operation (structuring approach).
	3. **Expert wizards** — external Autodesk design experts providing freeform metacognitive support (human baseline).
- **Intent formulation** — the challenge of specifying all design criteria as distinct parameters upfront; metacognitive support helps users discover and articulate their actual intent iteratively.
- **SocraBot** — the implemented system combining reflective prompts with diagram sketching support (voice-based, multimodal).
- **Intent Tags** — a separate GUI-based interaction technique for micro-prompting: granular, adaptive UI elements that let users articulate and refine intent without turn-based chat. Users reported feeling more in control than with chat-based GenAI.

## Useful Distinctions or Categories

- **Questioning vs. structuring** as two distinct metacognitive support mechanisms — the paper tests them separately and finds they have different impacts.
- **Provoking vs. scaffolding** — SocratAIs provokes reflection through questions; HephAIstus scaffolds through planning and visualization. The most effective support may combine both.
- **Voice vs. GUI modality** for metacognitive support — voice works well when the primary task is visual-spatial (avoids modality competition); Intent Tags show GUI can also work when designed as micro-interactions rather than full chat.

## Important Tensions

- **Questioning alone fails against solidified incorrect assumptions.** When users had already committed to a wrong mental model, reflective questions were less effective at dislodging those assumptions. This is a real limit of the pure Socratic/provocateur approach.
- **Metacognitive support can itself cause overreliance.** Some agent support led to additional overreliance — the user defers to the support agent's framing rather than developing their own. This means even well-intentioned cognitive augmentation can backfire.
- **User preference vs. cognitive effectiveness.** The paper notes trade-offs and differences in user preferences for metacognitive support — what users *want* from a support agent may not be what actually helps their cognition most.

## What Seems Most Relevant For My Thesis

- **Direct evidence for the Role → Strategy → Cognitive Function chain.** The paper maps AI roles (Socratic questioner, planning facilitator, expert coach) to concrete strategies (reflective questions, prompted sketching, planning support) to cognitive outcomes (intent formulation, problem exploration, outcome evaluation). This is almost exactly my framework structure.
- **The finding that questioning alone is insufficient** supports my argument that systems should not simply refuse to help or add friction — they need to provide genuinely useful redirected support (status summaries, visualizations, open-point surfacing) rather than just asking questions.
- **Intent Tags as a usage strategy.** The micro-prompting approach shifts some cognitive augmentation to the *interaction design* level rather than the *AI behavior* level. This is relevant for the design strategy vs. usage strategy distinction — Intent Tags are a design strategy that enables a particular usage pattern.
- **Evidence that agent-supported users produced more feasible designs.** This is concrete outcome evidence that metacognitive support during GenAI-assisted work improves task outcomes, not just subjective experience.

## What This Changes In My Thinking

- Strengthens the case that my framework's AI roles should not be pure archetypes (e.g., only Socratic Tutor, only Provocateur) but should be able to *combine* questioning with structuring — the most effective metacognitive support is hybrid.
- The overreliance-on-support-agent finding is a risk I need to account for. Even a well-designed TfT system can create a new form of offloading — the user offloads metacognitive regulation to the support agent instead of the task-completion AI. My framework needs to address this.

## What To Follow Up On

- The companion workshop paper [45]: Gmeiner, Martelaro & Holstein (2025), "Designing Metacognitive Support Interactions to Augment People's Thinking in Complex (Co-)Creative Tasks" — shorter version with the multi-year research program overview.
- Intent Tags paper [3]: Gmeiner et al. (2025), "Intent Tagging: Exploring Micro-Prompting Interactions for Supporting Granular Human-GenAI Co-Creation Workflows" (CHI 2025) — the GUI-based alternative to voice-based metacognitive support.
- The earlier formative study [4]: Gmeiner et al. (2023), "Exploring Challenges and Opportunities to Support Designers in Learning to Co-create with AI-based Manufacturing Design Tools" (CHI 2023) — identifies the concrete challenges that motivated the metacognitive support approach.

## One-Sentence Takeaway

- Metacognitive support agents that combine reflective questioning with structuring activities (planning, sketching) improve design outcomes during GenAI-assisted work, but questioning alone fails against solidified assumptions, and support itself can create new forms of overreliance.
