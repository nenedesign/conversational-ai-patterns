# Pattern 15: Knowledge Assist for Human Agents

## The problem

Human agents in contact centers, compliance teams, and customer support roles need to find relevant information fast during live conversations. The customer is waiting. Manual knowledge base search takes time, breaks focus, and produces inconsistent answers depending on who is searching and how.

The information exists. Finding it at the right moment is the challenge.

The gap is sharpest in regulated domains. A compliance officer mid-escalation needs to know whether a specific clause applies. A support agent needs the exact refund policy for a specific booking class. A payroll reviewer needs a country-specific labor law. In each case, the human knows what they need. They just cannot find it fast enough to matter.

## The pattern

**The AI system monitors the live conversation and proactively surfaces relevant knowledge, policy excerpts, and suggested responses to the human agent, without interrupting the customer-facing conversation.**

Knowledge assist has four properties:

1. **Real-time monitoring**: the system reads the conversation as it happens, not after the fact. The system generates suggestions from what is being said right now, not from a static query.
2. **Proactive surfacing**: the system does not wait for the human to search. It surfaces relevant knowledge based on what the conversation is about, ranked by relevance to the current moment.
3. **Contextual grounding**: suggestions reference specific documents, policies, or knowledge base articles. The human knows where the information comes from and can verify it.
4. **Human control**: suggestions are offers, not instructions. The human decides what to use, what to ignore, and what to say. The AI assists; it does not speak for the human.

**What makes it work:** The system treats the conversation as a query signal. Every turn updates the context. Knowledge retrieval runs continuously and silently, surfacing only when something relevant is found. The human's attention stays on the conversation.

## Seen in practice

*Demonstrated in: [Payroll Intelligence](../demos/payroll-intelligence.md)*

### Payroll Intelligence: context delivered before it is requested

When the compliance officer receives the HITL escalation card, they do not need to search for the Morales file, the Law 20.744 reference, or the payment timeline. The system has already surfaced all of it. It monitored the conversation between the user and Border Buddy and assembled the context before the human arrived.

This is knowledge assist at the moment it matters most: a consequential decision under time pressure, where the cost of a wrong answer is real.

The pattern extends beyond the HITL moment. Throughout the Payroll Detective flow, contractor risk findings reference the specific labor codes and classification criteria that make each finding actionable, not just a flag.

![Knowledge assist: compliance context surfaced before the human decision point, no manual search required](../demos/assets/deel-hitl-card.png)

## Research grounding

- **Google Generative Knowledge Assist**: production implementation of real-time knowledge surfacing for human contact center agents. Surfaces summarized suggestions and referenced documents based on conversation history and the end-user's query. Agents receive relevant information without interrupting the live conversation. [cloud.google.com/agent-assist/docs/knowledge-assist](https://cloud.google.com/agent-assist/docs/knowledge-assist)

- **Microsoft Copilot for Customer Service**: AI-assisted knowledge surfacing integrated into contact center workflows. Reduces average handle time and improves response consistency by surfacing relevant articles at the right moment in the conversation. [microsoft.com/en-us/microsoft-copilot/microsoft-copilot-for-service](https://www.microsoft.com/en-us/microsoft-copilot/microsoft-copilot-for-service)

- **Google PAIR People + AI Guidebook, "Anchor on current user needs"**: AI assistance should be calibrated to the user's current task and context. Surfacing information the user has not asked for is appropriate when the system has high confidence the information is relevant to what the user is doing right now. [pair.withgoogle.com/guidebook](https://pair.withgoogle.com/guidebook)

- **Amershi et al., "Software Engineering for Machine Learning" (CHI 2019)**: human-AI collaboration should augment human judgment rather than replace it. AI suggestions presented to human experts are most effective when they include the source and confidence of the recommendation. [dl.acm.org/doi/10.1109/ICSE-SEIP.2019.00042](https://dl.acm.org/doi/10.1109/ICSE-SEIP.2019.00042)

## Related patterns

- [Knowledge grounding](11-knowledge-grounding.md), the same RAG architecture serves both patterns; grounding retrieves for the AI agent, assist retrieves for the human agent
- [Human-in-the-loop](08-human-in-the-loop.md), knowledge assist is most valuable at HITL gates where the human needs full context to decide
- [Conversation summarization](14-conversation-summarization.md), assist surfaces relevant documents; summarization compresses what has already been said
