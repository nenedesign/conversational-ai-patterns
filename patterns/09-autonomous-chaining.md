# Pattern 09: Autonomous Chaining

## The problem

An agent that completes one task and then stops is only marginally better than a search bar. The user approved an action, "yes, rebook me", and now the agent is done, leaving them to figure out the next step. But they are still disrupted. They need a hotel. They need an expense claim. They need to know what happens next.

The alternative, asking the user's permission before every micro-step, is exhausting. "Should I search for hotels now?" "Should I book the one you selected?" "Should I file the expense claim?" Every confirmation interrupts the flow and puts cognitive load back on the user that the agent could be carrying.

The design challenge is knowing which steps can be chained autonomously and which require a pause. Not every step is the same.

## The pattern

**After an initial user confirmation, the agent chains related sub-tasks autonomously, completing each in sequence, reporting progress, and only pausing at genuine decision points.**

Autonomous chaining works within a bounded scope. The user approves the intent ("yes, handle my disruption") and the agent executes the sub-tasks that intent implies, without requiring re-confirmation for each one. The chain is:

1. **Intent confirmed**: user approves the first action
2. **Chain executes**: agent completes related sub-tasks in sequence, reporting each step as it completes
3. **Decision point**: agent pauses when it reaches a genuine choice (hotel options, not just "shall I book a hotel?")
4. **Chain resumes**: after the decision, the agent continues to completion

**What makes it work:** The scope of the chain is defined by the original intent. "Handle my disruption" implies rebooking, hotel, and expense claim, these are the natural sub-tasks. The agent does not expand beyond that scope or make novel decisions mid-chain without checking.

**The risk to manage:** Chains must have defined boundaries. An agent that keeps chaining indefinitely, or that expands scope mid-task without asking, has crossed from helpful to overreaching. This is LLM06 (Excessive Agency) in the OWASP LLM Top 10. The minimal footprint principle applies: do what the intent requires, nothing more.

## Seen in practice

### Travel Disruption: rebook, hotel, expense claim

Joe Chen approves one action: rebook on UA238. From that confirmation, the agent chains three sub-tasks without requiring re-initiation:

1. **Rebook confirmed**: UA238, 7:00 AM Tuesday, seat 24C, ref DA-FEZK9P. Covered by Disruption Assistance.
2. **Hotel options surfaced**: agent identifies overnight accommodation need and pulls covered options near the terminal. Pauses for a real choice: which hotel?
3. **Expense claim filed**: after hotel selection, agent files the DOT expense claim automatically. Reports the claim reference and eligibility window.

Three consequential actions. One user-initiated confirmation. The agent carries the load between decision points.

<!-- Screenshot: Dreamer, three-step chain: rebook → hotel options → expense claim filed -->
*[Screenshot: HTS Assist, autonomous chain: flight rebooked, hotel options surfaced, expense claim filed in one session]*

## Research grounding

- **Anthropic: "Building Effective Agents"**: prompt chaining and orchestrator-worker patterns: sequential task completion with defined handoff points between steps. Emphasizes simplicity and explicit planning as the key to coherent chains. [anthropic.com/engineering/building-effective-agents](https://www.anthropic.com/engineering/building-effective-agents)

- **OpenAI: "Practices for Governing Agentic AI Systems"**: minimal footprint: agents should complete only what is authorized and avoid side-effects or scope expansion beyond the original intent. [cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf](https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf)

- **OWASP LLM Top 10: LLM06, Excessive Agency**: the primary risk in autonomous chaining is scope creep: agents taking actions beyond what was authorized. Design must enforce minimal footprint at the system level. [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

- **Zhu et al. (2026), "Design Principles for Human-Agent Interaction"**: covers long-horizon task completion and when agents should pause for human input versus continue autonomously. [arxiv.org/abs/2606.20630](https://arxiv.org/abs/2606.20630)

## Related patterns

- [Action-first framing](03-action-first-framing.md), the chain begins with an action-first offer; the user's confirmation is what triggers the chain
- [Human-in-the-loop](08-human-in-the-loop.md), chains pause at genuine decision points; the HITL gate determines where "autonomous" ends
- [Resolution confirmation](10-resolution-confirmation.md), the chain ends with a clear signal that all sub-tasks are complete
