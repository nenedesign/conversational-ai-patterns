# Pattern 02: Context Awareness

## The problem

A conversational AI that asks the user to explain their situation is a conversational AI that has failed before it started. If the agent has access to the user's data, their bookings, their payroll cycle, their account status, their current page, it should use it. Every question the agent asks that it could have answered itself is friction, and friction erodes trust.

The inverse failure is also real: an agent that knows nothing about the user's context produces generic responses. Generic responses from an AI assistant are less useful than a search engine.

## The pattern

**The agent enters every conversation already knowing the relevant context, and makes that knowledge visible to the user.**

Context awareness has two components:

1. **Loaded context**: the agent has already retrieved and parsed the user's relevant data before the conversation begins (booking details, account state, active records, current page)
2. **Demonstrated context**: the agent signals this knowledge early in the conversation, establishing that it is operating on the user's specific situation, not in the abstract

Making context visible is not just a UX courtesy. It is a trust signal. When the agent says "I can see your flight UA234 to JFK has been cancelled" rather than "What flight are you asking about?", it demonstrates that it is connected to real data and operating with authority.

**What makes it work:** Context is loaded at session start, not retrieved in response to questions. The agent's opening message already reflects what it knows.

## Seen in practice

### Travel Disruption: pre-loaded booking and coverage context

When Joe Chen opens the HTS Assist chat, the agent's first message references his specific flight (UA234 to JFK), the reason for cancellation (crew shortage), and his coverage type (Disruption Assistance), before he has typed a single word. The agent is not demonstrating intelligence; it is demonstrating connection to his actual data.

The same pattern applies across all three personas. Sarah Kim opens the chat to a message that references her specific booking number and CFAR coverage status. Alex Morgan sees his flight status and Platinum eligibility confirmed upfront.

<!-- Screenshot: Dreamer, agent opening message with pre-loaded context per persona -->
*[Screenshot: HTS Assist opening messages, each persona receives context-specific first response]*

### Payroll Intelligence: cycle and workforce context

The Payroll Detective agent knows the Argentina payroll cycle details, the submission deadline, the number of contractors affected, and the relevant regulatory context (Argentina Law 20.744) before the HR manager asks. This allows the conversation to move directly to resolution rather than spending turns establishing what the problem is.

<!-- Screenshot: Deel, Payroll Detective references specific cycle data in opening message -->
*[Screenshot: Payroll Detective, agent opens with Argentina cycle context already loaded]*

## Research grounding

- **Microsoft HAX Toolkit, Guidelines G8-G9**: "remember recent interactions" and "learn from user behavior over time": agents should use available context to reduce repetition and demonstrate continuity. [microsoft.com/en-us/haxtoolkit](https://www.microsoft.com/en-us/haxtoolkit/ai-guidelines/)

- **Amershi et al. (2019), "Guidelines for Human-AI Interaction"**: Guideline 8 specifically addresses remembering context within and across sessions to reduce user burden. *CHI 2019.* [dl.acm.org/doi/10.1145/3290605.3300233](https://dl.acm.org/doi/10.1145/3290605.3300233)

- **Zhu et al. (2026), "Design Principles for Human-Agent Interaction"** (Carnegie Mellon), covers context loading and long-term memory as foundational to coherent agent interaction. [arxiv.org/abs/2606.20630](https://arxiv.org/abs/2606.20630)

## Related patterns

- [Proactive alerts](01-proactive-alerts.md), alerts are only relevant if grounded in the user's specific context
- [Action-first framing](03-action-first-framing.md), demonstrating context enables leading with action
- [Knowledge grounding](11-knowledge-grounding.md), context about the user's situation must be paired with grounded policy knowledge
