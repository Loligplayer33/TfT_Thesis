### Research Question:

How can a GenAI enabled, domain agnostic system be designed, such that it augments the user's cognition through the deliberate activation of higher order cognitive functions?

### What my task is:

Generally speaking my Thesis consists of four sequential steps that lead to a working prototypical application showcasing how usage and design strategies can be implemented to nudge the user from seeing an LLM-enabled tool as a way to offload work in a solely outcome-focused sense, towards one that enables the user to have a tool that augments the user's cognition and find the pareto-optimal balance between adoption and friction.

The Framework and the application implementing this framework should be horizontally scalable (allow more design and usage strategies to be included later on by solely extending the framework and application) and maybe even designed in a way, such that it is use-case and/or domain agnostic°. (best case)


°*This could either mean*
- that the framework and the application itself are abstracted from specific domains and use cases (f.e. ChatGPT can be used in many in domains and many different use-cases)
- **the supported use-case itself is domain agnostic (f.e. synthesis creation based on given sources is domain agnostic - needed in many different domains)**
	**-> This seems to be the sweet spot for the prototype and maybe also for the whole thesis**
- the system is use-case agnostic within a give domain (f.e. a coding agent that can help with many different use-cases that are coding related)

### To achieve this I need to 

1. **Identify existing design patterns** that support forward reasoning in the realm of HCI that can be applied to GenAI as well as the desirable cognitive functions those strategies help to augment. (Systematic literature review)
   
2. **Organize the findings regarding the design patterns** along the two axis of design strategies (how the system is built) and usage strategies (how the user interacts with the system) creating tangible artifacts that can be used to define AI roles. (Design Strategy Taxonomy)
   
3. **Create a (domain agnostic) conceptual framework that**
	1. Defines AI roles based on subsets of the identified design- und usage strategies
	2. Map AI Roles to the cognitive functions they target (implicitly using the strategies)
	   -> The chain looks like this: **AI Roles** -> **Strategies** -> **Cognitive Functions**
   
4. **Implement a horizontally scaling application running those E2E chains in a working environment** showcasing the impact that design strategies have to shift the user from passive consumer towards active thinker (through forward reasoning)
5. (Test the prototype)

### Examples and Definitions

- Design Patterns: ?
- Design Strategies: Define how the system is intentionally structured to achieve a specific cognitive outcome (System Design Side)
- Usage Strategies: Define strategies for workflows or activities, that the user employs to augment their thinking
	- OR: Describes the behaviors, mental models and interactive choices the human employs when engaging with a system
  (User Workflow Design Side)
- Higher Order Cognitive Function: Complex, conscious mental activities that govern goal-directed behaviour, abstract thinking and adaptability (reasoning, critical thinking, sensemaking, metacognition, cognitive flexibility, single loop/double loop learning, cognitive reflection, situational awareness theorie)


### Questions: 

- should my thesis and my application be anchored around the concept of forward thinking? -> no
	- In the Workshop paper they describe forward thinking is a kind of (meta) design strategy. For me it is more a human cognitive process and design strategies can only promote / enable forward thinking
		-> We need to either define it as this kind of meta design strategy implicitly embodying other design strategies like withholding answers, injecting questions etc. which lead to a system designed for forward thinking or as a human cognitive process which we use design strategies for to promote its activation.
		-> When we define it as a normal design strategy, the scope get's quite limited
#### Administrative:
- Zeitliche Einteilung (Wie ist die Struktur der BA über die verschiedenen Phase hinweg?)
- Ablauf / Gestaltung unserer Zukünftigen Meetings
- Das Monthly meeting am 01.07 - da kann ich vielleicht nicht vor Ort sein
