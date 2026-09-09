# Conversational AI Patterns

A practitioner's framework for designing trustworthy conversational AI — built from real prototypes, grounded in research, and written from experience leading AI product design in regulated and high-stakes domains.

This is not a theoretical guide. Every pattern here was applied in a working prototype. The research citations are here to back up the design decisions, not to lead them.

---

**Neville Ko** — AI Product Designer & Builder  
[Portfolio](https://fromus.ca) · [LinkedIn](https://www.linkedin.com/in/nevilleko/)

---

> **Disclaimer:** Employer names and branding used in the demo prototypes are for design demonstration purposes only. These are unsolicited concept explorations, not official products of the named companies.

---

## Why this exists

Most conversational AI fails not because the model is wrong, but because the interaction design is. Agents that don't express uncertainty. Handoffs between agents that feel like dropped calls. Actions taken without asking. Escalations that arrive too late — or never.

These patterns address the design layer: how conversational AI should behave, communicate, and hand off control in ways that users can trust.

---

## The Patterns

| # | Pattern | Core question | Seen in |
|---|---------|--------------|---------|
| 01 | [Proactive alerts](patterns/01-proactive-alerts.md) | How does the agent surface issues before the user asks? | Both demos |
| 02 | [Context awareness](patterns/02-context-awareness.md) | How does the agent demonstrate it already knows the situation? | Both demos |
| 03 | [Action-first framing](patterns/03-action-first-framing.md) | How does the agent lead with what it can do, not what it knows? | Travel disruption |
| 04 | [Trust calibration](patterns/04-trust-calibration.md) | How does the agent express confidence — including when it's uncertain? | Payroll intelligence |
| 05 | [Progressive disclosure](patterns/05-progressive-disclosure.md) | How does the agent reveal complexity in layers, not all at once? | Payroll intelligence |
| 06 | [Multi-agent handoff](patterns/06-multi-agent-handoff.md) | How do agents transfer context without losing the user? | Payroll intelligence |
| 07 | [Capability boundaries](patterns/07-capability-boundaries.md) | How does an agent signal what it cannot or should not do? | Payroll intelligence |
| 08 | [Human-in-the-loop](patterns/08-human-in-the-loop.md) | How does the agent require human approval before consequential actions? | Payroll intelligence |
| 09 | [Autonomous chaining](patterns/09-autonomous-chaining.md) | How does the agent complete multi-step tasks without interrupting the user? | Travel disruption |
| 10 | [Resolution confirmation](patterns/10-resolution-confirmation.md) | How does the agent signal that a problem is fully closed? | Both demos |
| 11 | [Knowledge grounding](patterns/11-knowledge-grounding.md) | How does the agent answer from verified sources, not model memory? | Travel disruption |

---

## The Demos

Two working prototypes demonstrate these patterns in context. Screenshots throughout this repo are taken from both.

### Payroll Intelligence
**Context:** Global HR and payroll — proactive anomaly detection, cross-border compliance, multi-agent escalation  
**Patterns:** Trust calibration, progressive disclosure, multi-agent handoff, capability boundaries, HITL, inline page update  
[View demo details](demos/payroll-intelligence.md)

### Travel Disruption
**Context:** Agentic travel resolution — flight disruption, CFAR refunds, loyalty upgrades  
**Patterns:** Proactive alerts, context awareness, action-first framing, autonomous chaining, resolution confirmation, knowledge grounding  
[View demo details](demos/travel-disruption.md)

### Private Assistant *(coming soon)*
**Context:** Privacy-first local AI — minimalist conversational UI, GDPR-aligned, no cloud dependency  
[View demo details](demos/private-assistant.md)

---

Video walkthroughs of each prototype are available at [fromus.ca](https://fromus.ca). To see a live demo, reach out on [LinkedIn](https://www.linkedin.com/in/nevilleko/).

---

## Research Foundation

These patterns are grounded in published research across industry, academia, and governance. Key sources:

- **Google PAIR Guidebook** — proactive design, mental models, user control
- **Microsoft HAX Toolkit + Amershi et al. (CHI 2019)** — 18 guidelines for human-AI interaction, 1,360+ citations
- **Anthropic: Building Effective Agents** — agentic workflow patterns, multi-agent orchestration
- **OpenAI: Governing Agentic AI Systems** — minimal footprint, reversibility, HITL gates
- **NIST AI RMF 1.0** — trustworthy AI attributes, risk management
- **EU AI Act** — transparency and human oversight requirements

Full bibliography: [references.md](references.md)

---

## Related Work

These prototypes share a technical foundation with production-grade AI workflows:

- [ai-governance-owasp10](https://github.com/nenedesign/ai-governance-owasp10) — OWASP LLM Top 10 prompt library and n8n workflows
- [ai-governance-pci-dss](https://github.com/nenedesign/ai-governance-pci-dss) — PCI-DSS cardholder data detection
- [ai-governance-soc2](https://github.com/nenedesign/ai-governance-soc2) — SOC 2 audit log pipeline
- [ai-governance-osfi-e23](https://github.com/nenedesign/ai-governance-osfi-e23) — OSFI E-23 model risk management
- [n8n-workflows](https://github.com/nenedesign/n8n-workflows) — agentic RAG pipelines and AI automation templates
