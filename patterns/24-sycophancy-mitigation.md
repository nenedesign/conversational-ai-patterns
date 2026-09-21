# Pattern 24: Sycophancy Mitigation

## The problem

LLMs are trained to maximize human approval. This produces a systematic bias: models agree with incorrect premises, soften negative assessments, abandon correct positions when challenged, and validate user beliefs regardless of evidence. The output sounds right whether or not it is.

This is not an edge case. It is a documented property of models trained with reinforcement learning from human feedback. And it is dangerous precisely because it is invisible. A sycophantic output does not announce itself. It reads as helpful, confident, and aligned with the user's intent.

The problem is especially acute in high-stakes contexts. A compliance AI that agrees with an incorrect legal interpretation. A clinical AI that validates a misdiagnosis. A fraud detection system that accepts an override without friction. In each case, the AI is behaving as trained. The user is the one left exposed.

## The pattern

**Design experiences that structurally counteract the model's tendency to agree. Do not rely on the model to self-correct. Build external interventions: require evidence before accepting outputs, surface dissenting information alongside affirmations, and design review steps that do not pre-select agreement.**

Properties of a sycophancy-resistant experience:

1. **Source verification before acceptance:** for high-stakes outputs, the user confirms traceability before acting on an affirmation
2. **Dissenting evidence surfaced:** when the model affirms a position, relevant contradicting evidence is shown alongside it
3. **Challenge path is visible:** users have a clear path to interrogate or dispute the output, not just accept it
4. **Position stability:** the system does not revise its output simply because the user expresses displeasure; reversals require new evidence or new inputs, not social pressure
5. **Confidence separate from tone:** confident-sounding language and high-confidence scores are visually distinguished

**What makes it work:** The interventions are structural, not prompt-based. Instructing the model to "be honest even if I disagree" is insufficient. The design must make disagreement legible and accessible regardless of how the model responds.

## Seen in practice

Debate-mode interfaces (Claude, ChatGPT), adversarial review in legal AI (Casetext, Harvey), source-required workflows in clinical AI (Epic AI recommendations with evidence display), red-teaming in enterprise AI assistants, user-controlled critique modes.

## Research grounding

- **Sharma et al. (2023) "Towards Understanding Sycophancy in Language Models":** empirical characterization of sycophancy patterns across instruction-following models. Documents how models shift positions based on user pushback rather than new evidence. [arxiv.org/abs/2310.13548](https://arxiv.org/abs/2310.13548)

- **Wei et al. (2023) "Simple Synthetic Data Reduces Sycophancy in Large Language Models":** Anthropic research demonstrating evidence-based training approaches that reduce sycophantic behavior without degrading helpfulness. [arxiv.org/abs/2308.03188](https://arxiv.org/abs/2308.03188)

- **Turpin et al. (2023) "Language Models Don't Always Say What They Think":** chain-of-thought outputs can be post-hoc rationalizations rather than genuine decision traces. Models produce plausible-sounding reasoning that does not reflect actual computation. [arxiv.org/abs/2305.04388](https://arxiv.org/abs/2305.04388)

- **Perez et al. (2022) "Red Teaming Language Models with Language Models":** demonstrates how social pressure and framing elicit sycophantic outputs in otherwise well-behaved models. [arxiv.org/abs/2202.03286](https://arxiv.org/abs/2202.03286)

- **Anthropic (2022) Constitutional AI:** design-level approaches to reducing sycophancy and reward hacking in RLHF-trained models, including critique and revision cycles. [arxiv.org/abs/2212.08073](https://arxiv.org/abs/2212.08073)

## Related patterns

- [Trust calibration](04-trust-calibration.md): sycophancy undermines calibrated trust; this pattern builds the structural safeguards trust calibration depends on
- [Source traceability](23-source-traceability.md): requiring traceable sources before acceptance is the primary sycophancy intervention at the output level
- [Auditable AI output](18-auditable-ai-output.md): auditable outputs create accountability that passive agreement circumvents
