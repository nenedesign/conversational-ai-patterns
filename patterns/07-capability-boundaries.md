# Pattern 07: Capability Boundaries

## The problem

An agent that attempts to answer everything is dangerous. Not because it will always be wrong, but because the user cannot tell when it is operating outside its competence. An agent with no visible limits produces outputs that look authoritative whether they are or not. In regulated domains, this is not a UX failure. It is a liability.

The temptation in AI product design is to hide limitations, to let the agent attempt a response rather than admit it cannot or should not proceed. This is the wrong tradeoff. Users can handle boundaries. What they cannot handle is an agent that gives them false confidence in a domain where errors have consequences.

## The pattern

**Agents explicitly signal when they have reached the boundary of their expertise or authority, and they do so without apology.**

A capability boundary is not a failure state. It is a design feature that tells the user:

- What this agent is for
- What it is not for
- What happens next when the boundary is reached

The boundary message should be:
- **Specific**: not "I can't help with that" but "Reclassification requires legal authorization, that's outside my scope"
- **Non-apologetic**: the boundary exists by design, not because the agent is broken
- **Actionable**: paired with what happens next: a handoff, an escalation, or a clear next step

**What makes it work:** Each agent has a defined domain. The domain is a design decision made at system architecture level, not an emergent property of the model. The agent knows its limits because those limits were specified, not because the model introspected them.

## Seen in practice

### Payroll Intelligence: Payroll Detective's legal boundary

When the Morales case crosses into legal classification territory, Payroll Detective does not attempt an answer. It states its boundary plainly:

"Reclassification requires legal authorization, that's a line I don't cross."

The language is deliberate. "A line I don't cross" signals intentional constraint, not inability, but appropriate scope limitation. The agent then invites the user to bring in Border Buddy, the agent qualified for this domain.

This pattern recurs at the next level: Border Buddy analyzes the Morales case in depth but ultimately escalates to a human compliance specialist. The boundary is explicit at each layer.

![Capability boundary — Payroll Detective states "that's a line I don't cross" before handing off to Border Buddy](../demos/assets/deel-agent-handoff.png)

## Research grounding

- **ADEPTS Framework (Meta FAIR, 2025)**: "scope limitation" as a core agent property: agents must have defined capability envelopes that are communicated to users. Bridges UX and engineering taxonomy for agent design. [arxiv.org/abs/2507.15885](https://arxiv.org/abs/2507.15885)

- **Woebot Health: AI Core Principles**: production example of capability boundary design: the agent does not diagnose, does not give medical advice, and uses only evidence-based CBT patterns. Crisis escalation is hardcoded. Real-world implementation of explicit constraints in a high-stakes context. [woebothealth.com/ai-core-principles](https://woebothealth.com/ai-core-principles/)

- **NIST AI Risk Management Framework 1.0**: "scope conditions" and validity: AI systems should be accurate within their defined operating conditions and clearly signal when they are being used outside those conditions. [nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)

- **EU AI Act, Article 13, Transparency**: conversational AI systems must be capable of informing users of what they can and cannot do. Capability boundary design is a compliance requirement in high-risk AI contexts. [artificialintelligenceact.eu](https://artificialintelligenceact.eu/high-level-summary/)

- **OpenAI: "Practices for Governing Agentic AI Systems"**: minimal footprint principle: agents should only operate within their defined authorization scope and escalate when at the edge. [cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf](https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf)

## Related patterns

- [Multi-agent handoff](06-multi-agent-handoff.md), boundaries trigger handoffs; these patterns are inseparable
- [Trust calibration](04-trust-calibration.md), low confidence is the precursor to a capability boundary; both communicate the limits of what the agent should do
- [Human-in-the-loop](08-human-in-the-loop.md), at the outermost boundary, the agent defers to a human rather than another agent
