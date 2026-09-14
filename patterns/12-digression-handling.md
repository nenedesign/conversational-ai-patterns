# Pattern 12: Digression Handling

## The problem

Users don't follow scripts. A traveler mid-way through rebooking a disrupted flight stops to ask about baggage allowance. A payroll manager reviewing an anomaly pauses to check an exchange rate. These detours are not mistakes. They are how people actually think: non-linearly, associatively, driven by whatever becomes relevant in the moment.

A conversational agent that can't handle digressions forces users back to the main flow (frustrating), loses the thread entirely (confusing), or answers the side question but forgets where the conversation was going (broken). The result in every case is friction that undermines trust.

In agentic systems, the stakes are higher. The primary flow represents real state: a rebooking in progress, a payroll action queued for approval. Losing that state mid-conversation is not just a UX failure. It is a trust failure.

## The pattern

**The agent holds the primary conversational context while the user explores a digression, answers within that context, and returns the user to exactly where they were.**

A digression handler has four properties:

1. **Context preservation**: the agent tracks the primary intent and state of the conversation throughout the detour. The main task is suspended, not abandoned.
2. **Contextual answers**: the digression is answered relative to the active conversation. "Your checked baggage limit is 23kg" is less useful than "For the YYZ–LAX flight you're rebooking, checked baggage is 23kg on the 6:45 PM departure."
3. **Graceful re-entry**: after the digression resolves, the agent explicitly returns: "Back to your rebooking, the 6:45 PM departure still has business class availability." The user is not dropped at the start of the flow or left to find their own way back.
4. **Stack awareness**: if a user takes a detour from a detour, the agent tracks the nesting and unwinds in order. It does not lose the thread two levels deep.

**What makes it work:** The agent treats the conversation as a stack, not a linear script. Digressions push to the stack; resolution pops back. The user is always returned to the right depth, with the right context, at the right moment.

## Seen in practice

*Demonstrated in: [Travel Disruption](../demos/travel-disruption.md)*

### Dreamer: mid-rebooking baggage question

Joe Chen is mid-way through rebooking his disrupted YYZ–LAX flight when he asks about checked baggage on the new departure. Rather than redirecting him back to the flow or answering generically, the agent answers in context. It pulls baggage rules for the specific flight being considered. Once the question is resolved, the agent picks up the rebooking at exactly the next step, seat selection, without asking Joe to re-establish context.

The digression is transparent (Joe sees the agent pivot to answer), contextual (the answer references his specific flight), and seamless (he never needs to restate what he was doing).

![Digression handling: agent answers mid-flow baggage question in context, then returns to rebooking](../demos/assets/dreamer-digression.png)

## Research grounding

- **Google PAIR People + AI Guidebook, "Handle errors and unexpected inputs"**: recommends designing explicitly for off-script user behavior, including topic shifts mid-conversation. Emphasizes graceful recovery and re-anchoring to the primary task without requiring the user to restart. [pair.withgoogle.com/guidebook](https://pair.withgoogle.com/guidebook)

- **Microsoft HAX Toolkit, G18: "Tell users what the system can and cannot do"**: guidelines for handling unexpected inputs in conversational AI, including disambiguation strategies, graceful topic transitions, and maintaining coherent state across off-topic exchanges. [microsoft.com/en-us/haxtoolkit](https://www.microsoft.com/en-us/haxtoolkit)

- **Jurafsky & Martin, "Speech and Language Processing" (3rd ed.), Chapter 15: Dialogue Systems and Chatbots**: covers dialogue state tracking, frame-based dialogue management, and handling of clarification and repair sub-dialogues. The theoretical foundation for digression handling in agentic systems. [web.stanford.edu/~jurafsky/slp3](https://web.stanford.edu/~jurafsky/slp3/)

- **Google Conversational Agents, Contextual Intents**: platform-level implementation of context-sensitive route groups. The same question receives different answers depending on where the user is in the flow, with session parameter routing that returns users to the correct point after a digression is resolved. [cloud.google.com/dialogflow/cx/docs/concept/handler](https://cloud.google.com/dialogflow/cx/docs/concept/handler)

## Related patterns

- [Context awareness](02-context-awareness.md), digression handling depends on continuous context tracking; the two patterns are inseparable
- [Capability boundaries](07-capability-boundaries.md), some digressions cross a capability boundary and should trigger a handoff rather than an inline answer
- [Resolution confirmation](10-resolution-confirmation.md), after returning from a digression, the agent should confirm the current state before proceeding
