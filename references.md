# References

Full bibliography for the Conversational AI Patterns framework. Sources are organized by category.

---

## Industry Design Frameworks

**Google PAIR: People + AI Guidebook**  
23 action-oriented design patterns for AI products. Covers proactive design, mental models, explainability, trust, feedback and control.  
https://pair.withgoogle.com/guidebook/patterns

**Google: Conversation Design Guidelines**  
Official design specification for conversational interfaces, persona, turn design, cooperative principles, natural dialogue flow.  
https://designguidelines.withgoogle.com/conversation/

**Microsoft HAX Toolkit: Guidelines for Human-AI Interaction**  
18 evidence-based guidelines organized around four interaction phases. The practitioner companion to Amershi et al. (2019).  
https://www.microsoft.com/en-us/haxtoolkit/ai-guidelines/

**Microsoft Research: Magentic-UI**  
Six HITL interaction mechanisms for agentic web tasks: co-planning, co-tasking, action guards, irreversibility detection, and long-term memory.  
https://www.microsoft.com/en-us/research/blog/magentic-ui-an-experimental-human-centered-web-agent/  
arXiv: https://arxiv.org/abs/2507.22358

**Anthropic: "Our Framework for Developing Safe and Trustworthy Agents"**  
Five-pillar framework: human control with autonomy, behavioral transparency, value alignment, privacy, and security. August 2025.  
https://www.anthropic.com/news/our-framework-for-developing-safe-and-trustworthy-agents

**Anthropic: "Building Effective Agents"**  
Engineering guidance on agentic workflow patterns: prompt chaining, routing, orchestrator-workers, and evaluator-optimizer. December 2024.  
https://www.anthropic.com/engineering/building-effective-agents

**Anthropic: Claude Model Spec**  
Published specification covering honesty norms, calibrated uncertainty, and the agent trust hierarchy.  
https://www.anthropic.com/research/claude-character

**OpenAI: "Practices for Governing Agentic AI Systems"**  
Seven baseline practices: minimal footprint, reversibility preference, escalation on uncertainty, sandboxing, and human oversight for irreversible actions. December 2023.  
https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf

**Salesforce: Responsible Agentic AI Guidelines**  
Design principles for the agentic enterprise, accuracy, HITL retention, Einstein Trust Layer patterns, and Agentforce guardrail design.  
https://www.salesforce.com/news/stories/responsible-agentic-ai-guidelines/

**Nielsen Norman Group: "10 Guidelines for Designing AI Chatbots"**  
Chatbot UX guidelines backed by research with 425+ ChatGPT/Bard/Bing Chat interactions. Covers proactive suggestions, layered content, and completion signals.  
https://www.nngroup.com/articles/ai-chatbots-design-guidelines/

**Apple Human Interface Guidelines: Siri**  
Natural language interaction principles, completing requests in-place, capability-appropriate surfaces, and resolution confirmation.  
https://developer.apple.com/design/human-interface-guidelines/

**Woebot Health: AI Core Principles**  
Production implementation of capability boundary design in a high-stakes context, no diagnosis, no medical advice, hardcoded crisis escalation.  
https://woebothealth.com/ai-core-principles/

---

## Academic Papers

**Amershi, S. et al. (2019). "Guidelines for Human-AI Interaction."**  
*CHI Conference on Human Factors in Computing Systems.* ACM.  
18 evidence-based guidelines validated across 20 AI products with 49 practitioners. 1,360+ citations. The foundational applied framework for human-AI interaction design.  
https://dl.acm.org/doi/10.1145/3290605.3300233

**Deng, Y. et al. (2025). "Proactive Conversational AI: A Comprehensive Survey."**  
*ACM Transactions on Information Systems.*  
Comprehensive survey of how agents initiate and shape conversations, proactive recommendation, topic management, goal-driven dialogue.  
https://dl.acm.org/doi/10.1145/3715097

**Deng, Y. et al. (2023). "Goal Awareness for Conversational AI: Proactivity, Non-collaborativity, and Beyond."**  
Tutorial at *ACL 2023* (61st Annual Meeting of the ACL).  
Systematic treatment of proactivity as a core conversational AI property. Initiative belongs with the agent.  
https://aclanthology.org/2023.acl-tutorials.1/

**Dubiel, M. et al. (2022). "Conversational Agents Trust Calibration: A User-Centred Perspective."**  
*Proceedings of the 4th ACM Conference on Conversational User Interfaces (CUI '22).* ACM.  
User-centred study of how trust calibration works in conversational agents.  
https://dl.acm.org/doi/abs/10.1145/3543829.3544518

**CHI 2024. "Empowering Calibrated (Dis-)Trust in Conversational Agents: Limitation Disclaimers vs. Authoritative Style."**  
*CHI 2024.* ACM.  
Controlled study of how disclaimer design and communicative style affect user trust calibration.  
https://dl.acm.org/doi/10.1145/3613904.3642122

**Wischnewski, M., Krämer, N., and Müller, E. (2023). "Measuring and Understanding Trust Calibration for Automated Systems."**  
*CHI 2023.* ACM.  
Empirical study distinguishing appropriate trust from overtrust and undertrust in automated systems.

**Zhu, H. et al. (2026). "Design Principles for Human-Agent Interaction."**  
Carnegie Mellon University. arXiv:2606.20630.  
14 design principles across four interaction stages, applied to evaluation of nine real agent systems.  
https://arxiv.org/abs/2606.20630

**D'Oro, P. et al. (2025). "ADEPTS: A Capability Framework for Human-Centered Agent Design."**  
Meta FAIR. arXiv:2507.15885.  
Six user-facing capabilities for understandable, controllable, trustworthy agents. Bridges UX heuristics, engineering taxonomies, and ethics.  
https://arxiv.org/abs/2507.15885

**"One Agent Too Many: User Perspectives on Approaches to Multi-Agent Conversational AI."**  
arXiv:2401.07123.  
Empirical user study on multi-agent handoff friction, agent identity transparency, and user preference patterns.  
https://arxiv.org/pdf/2401.07123

**"From Conversation to Orchestration: HCI Challenges in Interactive Multi-Agentic Systems."**  
*HAI '25 (13th International Conference on Human-Agent Interaction).* ACM.  
Research agenda for multi-agent design, negotiation patterns, context continuity, multi-party conversation management.  
https://dl.acm.org/doi/10.1145/3765766.3765795

**"Designing Algorithmic Delegates: The Role of Indistinguishability in Human-AI Handoff."**  
arXiv:2506.03102.  
Study of explicit vs. implicit handoff design and its effect on user trust and task continuity.  
https://arxiv.org/pdf/2506.03102

**"Autonomy and Agency in Agentic AI: Architectural Tactics for Regulated Contexts."**  
arXiv:2605.12105.  
Architectural patterns for HITL gate placement, reversibility weighting, and minimal footprint design in regulated environments.  
https://arxiv.org/pdf/2605.12105

**CUI@CHI 2024: "Building Trust in CUIs, From Design to Deployment."**  
*Extended Abstracts of CHI 2024.* ACM.  
Research agenda for trust in conversational user interfaces across the full design-to-deployment pipeline.  
https://dl.acm.org/doi/full/10.1145/3613905.3636287

---

## Standards and Governance

**NIST AI Risk Management Framework (AI RMF 1.0)**  
Seven attributes of trustworthy AI: validity and reliability, security, privacy, transparency, explainability, fairness, safety. January 2023.  
https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf

**ISO/IEC 42001:2023, AI Management Systems**  
First international standard for AI governance. Requirements for risk management, human oversight, transparency, and lifecycle governance.  
https://www.iso.org/standard/42001

**EU AI Act**  
Transparency and human oversight requirements for conversational AI. Enacted 2024; phased implementation 2025-2026.  
https://artificialintelligenceact.eu/high-level-summary/

**OWASP LLM Top 10**  
LLM01 (Prompt Injection), LLM04 (Data Poisoning), LLM06 (Excessive Agency), LLM09 (Misinformation), the most relevant risks for conversational and agentic AI design.  
https://owasp.org/www-project-top-10-for-large-language-model-applications/
