# Pattern 06: Multi-Agent Handoff

## The problem

As AI systems become more capable, the instinct is to build one agent that does everything. In practice, a single generalist agent either becomes too broad to be trustworthy or too complex to maintain. The alternative — specialized agents that collaborate — introduces a new design problem: how does the user experience a handoff between agents without losing the thread of the conversation?

Done poorly, a handoff feels like a dropped call. The user has to re-explain their situation. Context is lost. Trust is broken. Done well, a handoff is transparent, purposeful, and seamless — the user understands why a new agent is joining and what it brings.

## The pattern

**Agents hand off to specialists when they reach the boundary of their expertise — and the handoff is explicit, purposeful, and carries context.**

A well-designed handoff has four properties:

1. **Explicit trigger** — the handing-off agent states why it is bringing in a specialist. Not as an excuse, but as a design: "This crosses into cross-border classification. I'm bringing in Border Buddy."
2. **Identity announcement** — the receiving agent introduces itself with its specific expertise, not as a generic "AI assistant"
3. **Context continuity** — the receiving agent demonstrates it already knows what has been discussed. The user does not repeat themselves.
4. **Clear ownership** — it is always clear which agent the user is currently talking to, and what that agent's scope is

**What makes it work:** Each agent has a defined domain. The handoff triggers at the boundary of that domain — not when the first agent gives up, but when a more specialized one is genuinely better equipped. The boundary is a feature, not a limitation.

## Seen in practice

### Payroll Intelligence — Payroll Detective to Border Buddy

The Argentina Morales case crosses into cross-border contractor classification — outside Payroll Detective's domain. Rather than attempting an answer it is not qualified to give, Payroll Detective asks permission to bring in a specialist:

"Reclassification requires legal authorization — that's a line I don't cross. Can I bring in Border Buddy for the cross-border piece?"

The user confirms. Border Buddy joins and immediately demonstrates context continuity: it references the Morales case, the Law 20.744 risk, and the payment timeline — without being re-briefed. The active agent chip in the UI updates to show Border Buddy is now the primary agent.

The handoff is transparent (the user sees it happening), justified (the reason is stated), and seamless (no context is lost).

<!-- Screenshot: Deel — Payroll Detective capability boundary message + Border Buddy joining with context -->
*[Screenshot: Multi-agent handoff — Payroll Detective acknowledges its boundary; Border Buddy joins with full context]*

## Research grounding

- **"One Agent Too Many: User Perspectives on Approaches to Multi-Agent Conversational AI"** — empirical user study on multi-agent handoff friction, agent identity transparency, and preference for explicit vs. seamless transitions. Finds users prefer knowing when and why handoffs occur. [arxiv.org/pdf/2401.07123](https://arxiv.org/pdf/2401.07123)

- **"From Conversation to Orchestration: HCI Challenges in Interactive Multi-Agentic Systems"** — research agenda for multi-agent design: the central challenge is maintaining coherent context across agent boundaries. *HAI 2025.* [dl.acm.org/doi/10.1145/3765766.3765795](https://dl.acm.org/doi/10.1145/3765766.3765795)

- **"Designing Algorithmic Delegates: The Role of Indistinguishability in Human-AI Handoff"** — study of explicit vs. implicit handoff design. Finds that transparent transitions reduce user confusion and increase appropriate trust. [arxiv.org/pdf/2506.03102](https://arxiv.org/pdf/2506.03102)

- **Anthropic: "Building Effective Agents"** — orchestrator-workers pattern: subagents with defined scopes, coordinated by an orchestrator, with clear delegation and context passing. [anthropic.com/engineering/building-effective-agents](https://www.anthropic.com/engineering/building-effective-agents)

## Related patterns

- [Capability boundaries](07-capability-boundaries.md) — handoff triggers at the capability boundary; the two patterns are tightly coupled
- [Context awareness](02-context-awareness.md) — the receiving agent must demonstrate context continuity immediately
- [Trust calibration](04-trust-calibration.md) — each agent's confidence level determines whether it handles a task or hands off
