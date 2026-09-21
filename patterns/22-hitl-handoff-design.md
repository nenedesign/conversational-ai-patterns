# Pattern 22: HITL Handoff Design

## The problem

When an agentic system escalates to a human, the default behavior is to dump state. Raw logs, intermediate results, error messages. The handoff is treated as a technical event: fire the alert, assign the ticket, stop the agent. The human receives the output of a machine handoff, not the input to a human decision.

This fails the human. They do not know what the agent ran, why it stopped, what it is uncertain about, or what their available choices actually mean. They receive the appearance of oversight without the substance of it. The human is not completing a decision. They are cleaning up after an incomplete process.

This distinction matters especially in consequential contexts: compliance escalations, fraud reviews, clinical recommendations, payroll holds. In each case, the user needs enough context to make a defensible decision, not just a button to click.

## The pattern

**The escalation from agent to human is a design surface. The handoff must give the human everything they need to make a real decision: what the agent did, why it stopped, what it is uncertain about, and what each available choice means for downstream outcomes.**

A well-designed handoff has five properties:

1. **What ran:** a human-readable summary of the agent's actions before escalation, not a log dump
2. **Why it stopped:** the specific condition that triggered escalation (confidence below threshold, ambiguous input, policy boundary reached)
3. **What the agent is uncertain about:** the precise question the human is being asked to resolve
4. **What each choice means:** downstream consequences of each option, not a binary confirm/reject
5. **Override history preserved:** if the human overrides the agent, that decision is logged with rationale

**What makes it work:** The handoff is not designed as a fallback. It is designed as a first-class interaction. The human is not cleaning up after the agent. They are completing the decision the agent was not authorized to make alone.

## Seen in practice

Customer support escalation queues (Intercom, Zendesk), clinical decision support (Epic, Cerner), fraud review workflows (Stripe Radar, Featurespace), compliance escalation (Workday, ServiceNow).

*Demonstrated in: [Payroll Intelligence](../demos/payroll-intelligence.md)* (Pattern 08 covers the gate; this pattern covers the structure of what is inside it)

## Research grounding

- **Microsoft Research: Magentic-UI (2025):** six HITL interaction mechanisms for agentic systems, including action guards and co-pilot mode (structured human-agent collaboration on decision tasks). Direct reference for handoff design. [microsoft.com/en-us/research/blog/magentic-ui](https://www.microsoft.com/en-us/research/blog/magentic-ui-an-experimental-human-centered-web-agent/) · [arxiv.org/abs/2507.22358](https://arxiv.org/abs/2507.22358)

- **EU AI Act Article 14 (2024):** human oversight requirements for high-risk AI systems, including the ability to understand outputs sufficiently to detect and correct malfunctions. Handoffs that obscure agent reasoning fail this standard. [eur-lex.europa.eu](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32024R1689)

- **NIST AI RMF 1.0, Govern 4.2 (2023):** effectiveness of human oversight as a system requirement, not an afterthought. Oversight is only meaningful if the human has sufficient context to act. [doi.org/10.6028/NIST.AI.100-1](https://doi.org/10.6028/NIST.AI.100-1)

- **OpenAI: "Practices for Governing Agentic AI Systems":** agents should verify with users before consequential or irreversible actions, providing enough context for informed human decisions. [cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf](https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf)

- **Shneiderman, B. (2022) Human-Centered AI:** human control over consequential AI decisions requires legible, actionable interfaces, not just technical override capability. Oxford University Press.

## Related patterns

- [Human-in-the-loop](08-human-in-the-loop.md): Pattern 08 defines when to gate; this pattern defines what the gate contains
- [Trust calibration](04-trust-calibration.md): low confidence triggers the handoff; this pattern defines what the human receives when it fires
- [Auditable AI output](18-auditable-ai-output.md): the handoff record is part of the audit trail
