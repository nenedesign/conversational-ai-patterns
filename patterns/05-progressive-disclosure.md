# Pattern 05: Progressive Disclosure

## The problem

Conversational AI has a tendency to front-load. Ask about a payroll issue and the agent returns a wall of text: every finding, every risk, every caveat, every next step, all at once. The user is overwhelmed before they have decided whether they care.

This is not helpfulness, it is a failure of conversation design. A good conversation reveals information in layers. You establish the headline, confirm the user is engaged, then go deeper. Dumping everything at once is the AI equivalent of handing someone a 40-page report when they asked a yes/no question.

## The pattern

**The agent surfaces complexity in layers, leading with what matters most, going deeper only when the user engages.**

Progressive disclosure in conversational AI follows a consistent structure:

1. **The headline**: the most important finding, simply stated. One or two sentences.
2. **The first layer**: the highest-confidence, most actionable items. Enough for the user to begin making decisions.
3. **The second layer**: complexity, edge cases, or items requiring deeper analysis. Only revealed when the user asks or confirms they want to continue.
4. **Further depth**: additional context, historical data, regulatory detail. Available on request, never assumed necessary.

Each layer is a conversation turn. The agent checks in between layers. The user stays in control of how deep they go.

**What makes it work:** The agent has already done the full analysis. The layering is a presentation decision, not a limitation. The agent knows about the Morales case when it mentions the CUIT issues, it chooses to sequence correctly.

## Seen in practice

### Payroll Intelligence: three issues revealed in layers

The Argentina payroll cycle has three issues. The Payroll Detective does not present all three at once:

- **Layer 1:** Toast notification, "3 issues found in Argentina payroll cycle, action needed before Feb 25th." Single sentence. User opens the panel.
- **Layer 2:** Two straightforward issues (Lucia Torres and Pablo Reyes, missing CUIT numbers). High confidence, clear action. "I can send verification requests now. Continue with issue 3?"
- **Layer 3:** The Morales case, only revealed after the user confirms they want to continue. More complex, lower confidence, requires a different agent and a human decision.

If the agent had opened with all three cases including the full Morales risk analysis, the user would face a decision about legal escalation before they had even processed the simpler issues.

<!-- Screenshot: Deel, two-layer disclosure: CUIT issues first, Morales case only after confirmation -->
*[Screenshot: Payroll Detective, CUIT issues surfaced first; Morales complexity revealed only after user confirms]*

## Research grounding

- **Google PAIR Guidebook**: proactive and progressive design: surface the most relevant information first; offer paths to more detail rather than presenting everything simultaneously. [pair.withgoogle.com/guidebook/patterns](https://pair.withgoogle.com/guidebook/patterns)

- **ADEPTS Framework (Meta FAIR, 2025)**: progressive capability disclosure as a core user-facing property of trustworthy agents: users should be able to understand what an agent can do at increasing levels of depth. [arxiv.org/abs/2507.15885](https://arxiv.org/abs/2507.15885)

- **Nielsen Norman Group: "10 Guidelines for Designing AI Chatbots"**: guideline on layered content: chatbots should provide brief answers first with options to go deeper, rather than comprehensive responses that overwhelm. [nngroup.com/articles/ai-chatbots-design-guidelines](https://www.nngroup.com/articles/ai-chatbots-design-guidelines/)

## Related patterns

- [Proactive alerts](01-proactive-alerts.md), the alert is layer zero: a signal that something exists, not a full briefing
- [Trust calibration](04-trust-calibration.md), higher-confidence items surface first; uncertain items come later when the user is ready to engage with complexity
- [Human-in-the-loop](08-human-in-the-loop.md), the deepest layer often requires a human decision; progressive disclosure ensures that decision arrives with the right context, not before it
