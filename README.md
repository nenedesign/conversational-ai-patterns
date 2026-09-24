# Conversational AI Patterns

A practitioner's framework for designing trustworthy conversational AI, built from real prototypes, grounded in research, and written from experience leading AI product design in regulated and high-stakes domains.

This is not a theoretical guide. Every pattern here was applied in a working prototype. The research citations are here to back up the design decisions, not to lead them.

---

**Neville Ko**: AI Product Manager, Designer & Builder  
[Portfolio](https://fromus.ca) · [LinkedIn](https://www.linkedin.com/in/nevilleko/)

---

> **Disclaimer:** Company and employer names and branding used in the demo prototypes are for design demonstration purposes only. These are unsolicited concept explorations, not official products of or affiliated with the named companies.

---

## Why this exists

Most conversational AI fails not because the model is wrong, but because the interaction design is. Agents that don't express uncertainty. Handoffs between agents that feel like dropped calls. Actions taken without asking. Escalations that arrive too late, or never.

These patterns address the design layer: how conversational AI should behave, communicate, and hand off control in ways that users can trust. The principle behind all of them: AI augments workflow for human judgment. It does not replace it.

---

## The Patterns

| # | Pattern | Core question | Seen in |
|---|---------|--------------|---------|
| 01 | [Proactive alerts](patterns/01-proactive-alerts.md) | How does the agent surface issues before the user asks? | [Payroll Intelligence](demos/payroll-intelligence.md) · [Travel Disruption](demos/travel-disruption.md) |
| 02 | [Context awareness](patterns/02-context-awareness.md) | How does the agent demonstrate it already knows the situation? | [Payroll Intelligence](demos/payroll-intelligence.md) · [Travel Disruption](demos/travel-disruption.md) |
| 03 | [Action-first framing](patterns/03-action-first-framing.md) | How does the agent lead with what it can do, not what it knows? | [Travel Disruption](demos/travel-disruption.md) |
| 04 | [Trust calibration](patterns/04-trust-calibration.md) | How does the agent express confidence, including when it's uncertain? | [Payroll Intelligence](demos/payroll-intelligence.md) |
| 05 | [Progressive disclosure](patterns/05-progressive-disclosure.md) | How does the agent reveal complexity in layers, not all at once? | [Payroll Intelligence](demos/payroll-intelligence.md) |
| 06 | [Multi-agent handoff](patterns/06-multi-agent-handoff.md) | How do agents transfer context without losing the user? | [Payroll Intelligence](demos/payroll-intelligence.md) |
| 07 | [Capability boundaries](patterns/07-capability-boundaries.md) | How does an agent signal what it cannot or should not do? | [Payroll Intelligence](demos/payroll-intelligence.md) |
| 08 | [Human-in-the-loop](patterns/08-human-in-the-loop.md) | How does the agent require human approval before consequential actions? | [Payroll Intelligence](demos/payroll-intelligence.md) |
| 09 | [Autonomous chaining](patterns/09-autonomous-chaining.md) | How does the agent complete multi-step tasks without interrupting the user? | [Travel Disruption](demos/travel-disruption.md) |
| 10 | [Resolution confirmation](patterns/10-resolution-confirmation.md) | How does the agent signal that a problem is fully closed? | [Payroll Intelligence](demos/payroll-intelligence.md) · [Travel Disruption](demos/travel-disruption.md) |
| 11 | [Knowledge grounding](patterns/11-knowledge-grounding.md) | How does the agent answer from verified sources, not model memory? | [Travel Disruption](demos/travel-disruption.md) |
| 12 | [Digression handling](patterns/12-digression-handling.md) | How does the agent maintain context when the user goes off-topic mid-flow? | [Travel Disruption](demos/travel-disruption.md) |
| 13 | [Testing and evaluation](patterns/13-testing-and-evaluation.md) | How does the team validate agent behavior before it reaches production? | [Travel Disruption](demos/travel-disruption.md) |
| 14 | [Conversation summarization](patterns/14-conversation-summarization.md) | How does the agent capture what happened for handoffs, audit, and context reload? | [Payroll Intelligence](demos/payroll-intelligence.md) |
| 15 | [Knowledge assist for human agents](patterns/15-knowledge-assist.md) | How does the system surface relevant knowledge to human agents during live conversations? | [Payroll Intelligence](demos/payroll-intelligence.md) |
| 16 | [Conversation repair](patterns/16-conversation-repair.md) | How does the agent recover when a user says something it cannot understand? | [Travel Disruption](demos/travel-disruption.md) |
| 17 | [Outcome measurement](patterns/17-outcome-measurement.md) | How does the team know whether the agent actually resolved what the user needed? | [Payroll Intelligence](demos/payroll-intelligence.md) |
| 18 | [Auditable AI output](patterns/18-auditable-ai-output.md) | When AI outputs must withstand legal or regulatory review, how does the interface make evidence traceable? | [Regulated Evidence Review](demos/regulated-evidence-review.md) *(coming soon)* |
| 19 | [Scale triage with audit trail](patterns/19-scale-triage-audit-trail.md) | When AI filters large evidence sets, how does the system preserve an audit trail of what was excluded and why? | [Regulated Evidence Review](demos/regulated-evidence-review.md) *(coming soon)* |
| 21 | [Adversarial output design](patterns/21-adversarial-output-design.md) | When AI methodology will be challenged, how does the interface expose the reasoning chain so it can be reproduced and defended? | [Regulated Evidence Review](demos/regulated-evidence-review.md) *(coming soon)* |
| 22 | [HITL handoff design](patterns/22-hitl-handoff-design.md) | When the agent escalates to a human, what does the handoff contain so the human can make a real decision? | [Payroll Intelligence](demos/payroll-intelligence.md) |
| 23 | [Source traceability](patterns/23-source-traceability.md) | How does the interface make AI outputs traceable to their source data, not just to a document list? | [Travel Disruption](demos/travel-disruption.md) |
| 24 | [Sycophancy mitigation](patterns/24-sycophancy-mitigation.md) | How does the interface counteract the model's structural tendency to agree with the user? | [Payroll Intelligence](demos/payroll-intelligence.md) · [Travel Disruption](demos/travel-disruption.md) |

---

## The Demos

Three working prototypes demonstrate these patterns in context. Screenshots throughout this repo are taken from the first two.

### Payroll Intelligence
**Context:** Global HR and payroll, proactive anomaly detection, cross-border compliance, multi-agent escalation  
**Patterns:** Trust calibration, progressive disclosure, multi-agent handoff, capability boundaries, HITL, inline page update  

[![Payroll Intelligence prototype](demos/assets/deel-toast-alert.png)](demos/payroll-intelligence.md)

[View demo details](demos/payroll-intelligence.md)

### Travel Disruption
**Context:** Agentic travel resolution, flight disruption, CFAR refunds, loyalty upgrades  
**Patterns:** Proactive alerts, context awareness, action-first framing, autonomous chaining, resolution confirmation, knowledge grounding  

[![Travel Disruption prototype](demos/assets/dreamer-joe-opening.png)](demos/travel-disruption.md)

[View demo details](demos/travel-disruption.md)

### Personal Creative Assistant *(coming soon)*
**Context:** Privacy-first local AI, minimalist conversational UI, GDPR-aligned, no cloud dependency  
[View demo details](demos/private-assistant.md)

### Regulated Evidence Review *(coming soon)*
**Context:** AI-assisted review of large evidence sets in regulated and legal contexts; scale triage, chain of custody, adversarial defensibility  
**Patterns:** Auditable AI output, scale triage with audit trail, adversarial output design, HITL handoff design

---

Video walkthroughs of each prototype are available at [fromus.ca](https://www.fromus.ca/conversational-ai) *(coming soon)*. To see a live demo, reach out on [LinkedIn](https://www.linkedin.com/in/nevilleko/).

---

## Research Foundation

These patterns are grounded in published research across industry, academia, and governance. Key sources:

- **Google PAIR Guidebook**: proactive design, mental models, user control
- **Microsoft HAX Toolkit + Amershi et al. (CHI 2019)**: 18 guidelines for human-AI interaction, 1,360+ citations
- **Anthropic: Building Effective Agents**: agentic workflow patterns, multi-agent orchestration
- **OpenAI: Governing Agentic AI Systems**: minimal footprint, reversibility, HITL gates
- **NIST AI RMF 1.0**: trustworthy AI attributes, risk management
- **EU AI Act**: transparency, human oversight, and record-keeping requirements
- **ACPO Good Practice Guide for Digital Evidence**: audit trail and reproducibility requirements for digital evidence
- **Alam & Altiparmak, XAI-CF (2024/2026)**: explainable AI in cyber forensics; interpretability as a legal admissibility requirement
- **Reedy / Interpol Digital Evidence Review (2026)**: AI triage admissibility and chain of custody documentation
- **Sharma et al. (2023)**: empirical characterization of sycophancy in instruction-following models
- **Lewis et al. (2020)**: retrieval-augmented generation as the architectural foundation for source traceability

Full bibliography: [references.md](references.md)

---

## Related Work

These prototypes share a technical foundation with production-grade AI workflows:

- [ai-governance-owasp10](https://github.com/nenedesign/ai-governance-owasp10), OWASP LLM Top 10 prompt library and n8n workflows
- [ai-governance-pci-dss](https://github.com/nenedesign/ai-governance-pci-dss), PCI-DSS cardholder data detection
- [ai-governance-soc2](https://github.com/nenedesign/ai-governance-soc2), SOC 2 audit log pipeline
- [ai-governance-osfi-e23](https://github.com/nenedesign/ai-governance-osfi-e23), OSFI E-23 model risk management
- [n8n-workflows](https://github.com/nenedesign/n8n-workflows), agentic RAG pipelines and AI automation templates
