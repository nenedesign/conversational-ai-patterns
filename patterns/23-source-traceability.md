# Pattern 23: Source Traceability

## The problem

AI-generated outputs synthesize, summarize, and assert. When the source of an assertion is absent, buried in a footnote, or linked only to a document title, users cannot verify claims, trace errors, or defend outputs in downstream contexts. The output looks authoritative whether or not it is grounded.

This is not a niche concern. It applies any time an AI system makes a claim a user will act on: a recommendation, a summary, a risk assessment, a diagnosis. If the user cannot trace the claim to its source, they cannot evaluate it. They can only accept it or reject it on faith.

The problem compounds when outputs travel. A summary gets forwarded. A recommendation becomes a decision. A risk flag becomes a policy. At each step, the distance from the original source grows. By the time the output reaches the person acting on it, the grounding may be invisible.

## The pattern

**Provenance is a first-class UI element. Every AI output that synthesizes, summarizes, or asserts information must make the source traceable from the assertion itself, not from a reference list appended at the bottom.**

A traceable output has five properties:

1. **Inline traceability:** source links are attached to specific claims, not aggregated separately at the end
2. **Source fragment visible:** the exact passage, record, or data point is accessible, not just a document title
3. **Confidence bounded by evidence:** the system does not assert more certainty than the source material supports
4. **Gap disclosure:** when a claim has no traceable source, that absence is surfaced, not hidden
5. **Reproducible trace:** given the same input, the same sources are cited

**What makes it work:** Citation is not a post-processing step. Retrieval and sourcing are architectural decisions. The design question is not where to put the footnotes. It is whether the retrieval pipeline is built so that sourcing is always available when the output is generated.

## Seen in practice

Perplexity AI (inline numbered citations per claim), Microsoft Copilot (source cards in responses), Bing Chat, enterprise RAG search (Glean, Guru), legal research AI (Westlaw Precision, LexisNexis Lexis+).

## Research grounding

- **Lewis et al. (2020) "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks":** foundational RAG architecture. Grounding generation in retrieved documents is the infrastructure that makes source traceability possible. [arxiv.org/abs/2005.11401](https://arxiv.org/abs/2005.11401)

- **Gao et al. (2023) "Retrieval-Augmented Generation for Large Language Models: A Survey":** comprehensive overview of citation, attribution, and grounding techniques across RAG systems. Documents where citation quality breaks down. [arxiv.org/abs/2312.10997](https://arxiv.org/abs/2312.10997)

- **NIST AI RMF 1.0, Measure 2.5 (2023):** explainability and interpretability of AI outputs, including the ability to trace outputs to their inputs and source data. [doi.org/10.6028/NIST.AI.100-1](https://doi.org/10.6028/NIST.AI.100-1)

- **EU AI Act Articles 12 and 13 (2024):** record-keeping and transparency requirements for high-risk AI systems, including logging sufficient to trace outputs back to inputs and explain system behavior. [eur-lex.europa.eu](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32024R1689)

- **ACPO Good Practice Guide for Digital Evidence, Principle 3 (2012):** continuity of evidence requires that any person accessing material can account for what happened to it. Investigative traceability baseline that applies wherever outputs will be used in consequential or adversarial review. [forensiccontrol.com/guides/acpo-guidelines-principles-explained](https://forensiccontrol.com/guides/acpo-guidelines-principles-explained/)

## Related patterns

- [Auditable AI output](18-auditable-ai-output.md): auditable output requires traceable sources; this pattern is the sourcing layer
- [Adversarial output design](21-adversarial-output-design.md): defending outputs in adversarial review depends on source traceability being built in
- [Trust calibration](04-trust-calibration.md): trust calibration is only possible when users can see what the output is based on
