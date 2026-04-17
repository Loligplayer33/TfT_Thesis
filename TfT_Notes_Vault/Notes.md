

Claude.md / Agent.md file um die Usage strategies besser abzubilden?

![[assets/Pasted image 20260404100215.png]]

⇒ There is a second thesis offer, focussing on the evaluation of cognitive augmentation. Meaning it has the goal to measure the outcomes of using a TfT. This is therefore NOT part of my thesis.

My goal is to find, systemize and apply design and usage strategies that prevent cognitive offloading. (Point 1.1 of the Workshop paper)

To do that I need to perform

1. a systematic literature review of existing design patterns and theories that support forward reasoning (through process oriented support (source 24 from the chi workshop paper))
2. Sort the findings along the two axis of Design stategies and usage strategies (with potential sub-axis like whether a strategy works by _withholding_ information, _restructuring_ a task, _prompting_ reflection, etc.)
3. Map AI Roles (like tutor, socratic thinker, devils advocate etc.) to the cognitive functions they target (sensemaking, metacognition, critical-thinking) using the strategies to realize the AI roles.
    - Example - IMPORTANT:
        
        The roles describe _what the AI is being_ — the stance it takes. The strategies describe _what it concretely does_ to inhabit that role. A Socratic Tutor isn't a Socratic Tutor because you label it that way — it becomes one by employing specific strategies like withholding answers, asking probing questions, surfacing contradictions.
        
        Say the AI role is **Socratic Tutor** and the cognitive function you want to augment is **critical thinking**.
        
        The strategy is the _concrete mechanism_ that connects those two. In this case it might be **question-based scaffolding** — instead of giving the user an answer, the system responds with a targeted question that forces them to examine their own reasoning.
        
        So the chain looks like:
        
        **Socratic Tutor** (role) → **asks probing questions instead of providing answers** (strategy) → **user has to evaluate their own assumptions** (critical thinking activated)
        
        Another example: the role is **Provocateur** (from Sarkar's "AI Should Challenge, Not Obey"), the target is **metacognition**, and the strategy might be **deliberate counterargument** — the system generates a plausible opposing position to whatever the user just wrote. The user then has to monitor their own reasoning to decide whether their original position holds up.
        
        **Provocateur** → **generates counterarguments** → **user monitors and re-evaluates their own thinking** (metacognition)
        
        Without the strategy in the middle, you just have a vague claim like "a Socratic Tutor supports critical thinking." The strategy answers _how_ — what does the system actually _do_ that creates the cognitive effect? That's what makes your framework actionable rather than just a label taxonomy.
        
        **In regards to the obsidian idea:**
        
        ⇒ In your prototype, each skill definition is essentially encoding one of these chains. The skill says: here's the role I'm playing, here's the concrete behavior I exhibit, and here's the cognitive function that behavior is meant to engage.
        
        Your skills _are_ the roles made concrete.
        
        Each skill file in your vault is essentially one of these role definitions — it specifies a conversational stance (Socratic Tutor, Provocateur, Facilitator, whatever). But a skill file doesn't just say "be a Socratic Tutor." It has to encode the _strategies_ that make that role real — the actual behaviors the system performs. Things like: when the user writes a claim, respond with a question rather than validation. Or: when the user asks for a summary, generate a partial one with gaps they have to fill.
        
        So the skill definition schema you haven't designed yet? That's where the framework literally becomes code. Each skill needs to specify:
        
        - **The role** it's playing (the stance)
        - **The strategies** it employs (the concrete behaviors — what it does and doesn't do)
        - **The cognitive function** it's targeting (what kind of thinking it's trying to activate)
        
        Your cognitive checkpoints in the orchestration layer are also strategies — they're the "desirable difficulties" from the thesis spec, moments where the system deliberately introduces friction to force the user back into active reasoning.
        
        And your two interaction patterns map here too. The chat sidebar is where the role is most visible — that's the explicit conversational stance. But Pattern B, the inline callout injection, is where strategies get delivered _into the user's workspace_ without them having to initiate a conversation. That's arguably where the more interesting strategies live, because they intervene at the moment of thinking rather than in a separate dialogue about thinking.
        
        So the short version: your framework (role → strategy → cognitive function) is the theory, and your Obsidian architecture (skill files → behaviors → checkpoints) is that theory instantiated as a system.
