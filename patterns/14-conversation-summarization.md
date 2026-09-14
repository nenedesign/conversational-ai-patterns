# Pattern 14: Conversation Summarization

## The problem

Long conversations accumulate context that is expensive to re-read. Before a handoff, the receiving agent or human needs to get up to speed fast. After a complex resolution, the user needs confirmation of what was decided. When a conversation resumes after a break, someone has to reload the context without starting over.

The transcript is the wrong tool for all of these. It is chronological and unstructured. Finding the relevant facts requires re-reading everything. In a handoff scenario, that re-read falls on the person least able to spare the time.

In regulated contexts, the problem is worse. A summary that misrepresents what was agreed to creates liability. A summary that omits a key decision creates an audit gap.

## The pattern

**The agent generates a structured summary at natural transition points: before a handoff, at resolution, and when a complex segment concludes. The summary captures intent, actions taken, decisions made, and outstanding items.**

A conversation summary has four properties:

1. **Triggered at transitions**: the agent generates summaries at natural break points, not continuously. Handoffs, escalations, resolutions, and session pauses are the right moments.
2. **Structured, not narrative**: a useful summary is organized by category, not written as prose. Intent, actions, decisions, and open items are separate fields, not buried in a paragraph.
3. **Carried forward**: the summary travels with the conversation to the next agent, session, or human reviewer. The conversation ending does not discard it.
4. **Accurate and conservative**: the summary reflects what was actually said and agreed to. It does not infer intent or embellish. In regulated contexts, the summary becomes part of the interaction record.

**What makes it work:** The agent treats the summary as a first-class output, not a byproduct, and generates it with the same care as any other response. The structure is defined. Downstream consumers can rely on it.

## Seen in practice

*Demonstrated in: [Payroll Intelligence](../demos/payroll-intelligence.md)*

### Payroll Intelligence: summary before the HITL gate

When Border Buddy completes the Morales analysis and the human decision is required, the HITL card does not just present two buttons. It presents a structured summary: the issue identified (contractor misclassification risk), the risk assessed (Law 20.744 exposure), and the two resolution options with their consequences. That summary is what makes the human decision meaningful.

Without it, the compliance officer would need to re-read the conversation to understand what they are being asked to decide. With it, the decision is immediate and informed.

The summary is the mechanism that makes HITL actionable. It is also the beginning of an audit trail.

![Conversation summarization: HITL card presents structured summary of findings and options before human decision](../demos/assets/deel-hitl-card.png)

## Research grounding

- **Google Conversational Insights, LLM Summarization Module**: production implementation of LLM-generated conversation summaries for contact center interactions. Summaries capture resolution status, sentiment, key topics, and agent actions. Exportable to BigQuery for analysis and audit. [cloud.google.com/agent-assist/docs/conversation-summarization](https://cloud.google.com/agent-assist/docs/conversation-summarization)

- **Anthropic: "Building Effective Agents"**: context management in long-running agentic tasks. Agents should periodically summarize completed work and maintain a running record of decisions made, to avoid context window exhaustion and to support handoffs. [anthropic.com/engineering/building-effective-agents](https://www.anthropic.com/engineering/building-effective-agents)

- **OpenAI: "Practices for Governing Agentic AI Systems"**: agentic systems should maintain records of actions taken and decisions made, particularly for consequential or irreversible actions. Summaries support auditability and human oversight. [cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf](https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf)

- **ISO/IEC 42001:2023, AI Management Systems**: organizations must maintain records of AI-assisted decisions, including the context in which they were made. Structured conversation summaries are an implementation mechanism for this requirement. [iso.org/standard/42001](https://www.iso.org/standard/42001)

## Related patterns

- [Multi-agent handoff](06-multi-agent-handoff.md), the summary is the context package passed at handoff; the two patterns are tightly coupled
- [Human-in-the-loop](08-human-in-the-loop.md), the summary presented before a HITL gate determines whether the human has enough information to decide
- [Resolution confirmation](10-resolution-confirmation.md), the resolution confirmation is a user-facing summary; this pattern covers the operational and audit-facing summary
