# Pattern 11: Knowledge Grounding

## The problem

A conversational AI that answers from model memory alone is an unreliable witness. Large language models are trained on data that has a cutoff date, may contain errors, and cannot be verified by the user. In domains where accuracy matters — travel policy, payroll regulations, compliance requirements — an agent that confabulates is worse than an agent that says nothing.

The solution is not to make the model more accurate. It is to change where the agent gets its information. An agent grounded in a verified, curated knowledge source can be trusted not because the model is reliable, but because the knowledge base is.

## The pattern

**The agent retrieves answers from a verified, domain-specific knowledge base — not from model training data — and the retrieval architecture is explicit and auditable.**

Knowledge grounding has three components:

1. **A curated knowledge source** — policy documents, regulatory texts, procedure manuals, historical case data. Content that has been reviewed and approved, not scraped from the web.
2. **Semantic retrieval** — when the user asks a question, the agent searches the knowledge base by meaning, not by keyword. The most relevant passages are retrieved and injected into the agent's context.
3. **Source transparency** — the agent answers from retrieved passages, and those passages are traceable. When audited, you can identify exactly which document informed which response.

This architecture separates what the model knows from what the agent says. The model provides language capability. The knowledge base provides facts. The two are not the same.

**Why this matters beyond accuracy:** Knowledge grounding is also a governance pattern. Audit trails become possible. Regulatory compliance becomes defensible. When an agent says "under Argentina Law 20.744, full-time hours for 6+ consecutive months constitute a legally presumed employment relationship," that statement can be traced to a specific document in the knowledge base — not attributed to model training.

## Seen in practice

### Travel Disruption — RAG pipeline over policy and regulatory documents

The HTS Assist prototype is backed by an agentic RAG pipeline built in n8n. Policy documents, carrier regulations, and fintech product terms are embedded into a Supabase vector store using semantic embeddings. When a user scenario triggers a policy question, the agent retrieves the relevant passages and grounds its response in those documents.

The n8n workflow handles the full retrieval pipeline: webhook trigger → semantic search against the Supabase vector store → context injection → Claude response → structured output. The Supabase table stores the embedded document chunks with their source metadata.

<!-- Screenshot: n8n RAG pipeline workflow -->
*[Screenshot: n8n RAG pipeline — webhook → semantic search → Supabase vector store → Claude response]*

<!-- Screenshot: Supabase vector store table snippet -->
*[Screenshot: Supabase vector store — embedded policy document chunks with source metadata]*

This is not a UI demo backed by hardcoded responses. The agent's answers on coverage, eligibility, and regulatory requirements come from a retrievable, auditable knowledge base.

## Research grounding

- **OWASP LLM Top 10: LLM09 — Misinformation** — agents that answer from training data alone are susceptible to generating plausible but incorrect information. RAG-grounded architectures reduce misinformation risk by anchoring responses to verified sources. [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

- **OWASP LLM Top 10: LLM04 — Data and Model Poisoning** — the knowledge base itself is a risk surface; curated, reviewed document ingestion pipelines reduce poisoning risk compared to open-ended retrieval. [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

- **NIST AI RMF 1.0 — Validity and Reliability** — trustworthy AI systems must be valid (performing as intended) and reliable (performing consistently). Grounding responses in verified sources directly addresses both properties. [nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)

- **Anthropic: "Building Effective Agents"** — retrieval-augmented patterns: agents that retrieve rather than recall produce outputs that are more accurate, more auditable, and more aligned with the specific domain they operate in. [anthropic.com/engineering/building-effective-agents](https://www.anthropic.com/engineering/building-effective-agents)

## Related patterns

- [Trust calibration](04-trust-calibration.md) — grounded responses enable more accurate confidence expression; the agent knows the source of its information and can calibrate accordingly
- [Capability boundaries](07-capability-boundaries.md) — when the knowledge base does not contain relevant information, the agent should say so rather than falling back to model memory
- [Context awareness](02-context-awareness.md) — user context and knowledge grounding work together: the agent knows the user's situation (context) and the relevant policy (knowledge base)
