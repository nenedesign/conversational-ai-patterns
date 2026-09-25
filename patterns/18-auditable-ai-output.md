# Pattern 18: Auditable AI Output

## The problem

AI outputs that look authoritative but cannot be traced back to their source data are a credibility problem in legal, regulatory, and investigative contexts. In those contexts, the question is not only whether the output is correct. It is whether the reasoning behind it can be examined, challenged, and reproduced.

A system that surfaces a finding without showing its provenance cannot be cross-examined. An output that cannot be cross-examined cannot be trusted in adversarial review. In high-stakes, compliance, and regulated contexts, that is not a design inconvenience. It is a disqualifying flaw.

The failure mode is subtle: the system looks authoritative. The language is confident. The output is plausible. But the evidence chain underneath it is invisible.

## The pattern

**Every AI output that may be used in legal, regulatory, or adversarial review contexts must be traceable to its source data, and that traceability must be a first-class element of the interface.**

Auditable output design has four properties:

1. **Citations are surface-level, not buried:** sources appear inline with outputs, not in a footnote, a tooltip, or a separate panel the user must actively open
2. **Confidence is bounded by evidence:** the system's expressed certainty reflects the quality and completeness of underlying sources; outputs cannot appear more authoritative than the evidence supports
3. **Filtering and exclusion decisions are logged:** what the system did not surface is part of the record, not just what it did
4. **Outputs are reproducible:** the same inputs, the same model, and the same settings produce the same traceable output; reproduction is possible by an independent reviewer

**What makes it work:** Auditability is designed in from the start, not bolted on as an export feature. The interface treats citations as UI elements with the same design priority as the output itself.

## Seen in practice

*Regulated Evidence Review demo (coming soon)*

This pattern applies to any AI-assisted review context where outputs may be used in legal proceedings, regulatory audits, or adversarial challenge. Any AI output used to prioritize, classify, or exclude records carries the obligation to show its work.

## Research grounding

- **NIST AI RMF 1.0 (2023):** defines explainability, traceability, and accountability as foundational trustworthy AI properties; the GOVERN and MANAGE functions require documentation of data lineage and human review processes. [nist.gov/system/files/documents/2023/01/26/AI%20RMF%201.0.pdf](https://www.nist.gov/system/files/documents/2023/01/26/AI%20RMF%201.0.pdf)

- **EU Artificial Intelligence Act, Article 12: Record-Keeping (2024):** high-risk AI systems must automatically log input data, reference databases, output decisions, and timestamps; for law enforcement systems, providers must log exactly what data produced each result. [artificialintelligenceact.eu/article/12](https://artificialintelligenceact.eu/article/12/)

- **ACPO Good Practice Guide for Digital Evidence, Principle 3 (2012):** mandates that an audit trail of all processes applied to digital evidence must be created and preserved; an independent third party must be able to examine those processes and achieve the same result. [forensiccontrol.com/guides/acpo-guidelines-principles-explained](https://forensiccontrol.com/guides/acpo-guidelines-principles-explained/)

- **Alam & Altiparmak, "XAI-CF: Examining the Role of Explainable Artificial Intelligence in Cyber Forensics" (2024/2026):** argues that AI applied to forensic analysis must be authentic, interpretable, understandable, and interactive to gain legal acceptance; investigators and court members require explanations of AI outputs to satisfy legal accountability requirements. [arxiv.org/abs/2402.02452](https://arxiv.org/abs/2402.02452)

## Related patterns

- [Knowledge grounding](11-knowledge-grounding.md): grounding answers in verified sources is a prerequisite; auditable output is how that grounding surfaces in the interface
- [Trust calibration](04-trust-calibration.md): expressed confidence must be bounded by the quality of underlying evidence
- [Scale triage with audit trail](19-scale-triage-audit-trail.md): when AI filters large evidence sets, the audit trail of exclusions is itself an auditable output
