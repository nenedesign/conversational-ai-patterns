# Pattern 17: Outcome Measurement

## The problem

Most teams measure the wrong things. Conversations handled. Response time. Intents matched. These are inputs. They tell you how busy the agent was, not whether it worked.

An agent that handles a hundred conversations a day but resolves twenty of them is not a high-performing agent. It is a high-volume problem. Without outcome data, that distinction is invisible. The team improves based on guesswork, fixes what is visible, and misses what matters.

The problem is self-reinforcing. Bad outcome data means bad training signals. Bad training signals mean the agent repeats the same failures. The loop runs indefinitely until something forces it open: a user complaint, a compliance audit, a spike in escalations.

## The pattern

**The system measures whether each conversation achieved its goal, how the user felt during it, and whether the agent's expressed confidence matched the actual outcome. Outcome data feeds a continuous improvement loop.**

Outcome measurement has four properties:

1. **Resolution tracking**: each conversation is tagged at close with whether the primary intent was resolved. Partial resolutions and unresolved handoffs are tracked separately. A conversation that ends with a human escalation is not the same outcome as one that ends with a confirmed action.
2. **Sentiment signals**: the system captures sentiment throughout the conversation, not just at the end. A user who started frustrated and ended satisfied has a different story than one who started neutral and escalated. Both matter.
3. **Confidence calibration**: when the agent expresses a confidence level ("I am confident this applies to your situation"), the outcome is tracked. High confidence followed by a wrong answer is a calibration failure, not a model failure. The two require different fixes.
4. **Feedback loop**: outcome data flows back into test case updates, intent model training, and pattern reviews. The improvement cycle is explicit, not ad hoc.

**What makes it work:** Outcomes are defined before the agent is built, not inferred after. The team knows what a resolved conversation looks like before the first conversation happens. Measurement is a design decision, not an afterthought.

## Seen in practice

*Demonstrated in: [Payroll Intelligence](../demos/payroll-intelligence.md)*

### Payroll Intelligence: escalation as an outcome signal

Every HITL escalation in the Payroll Intelligence flow is an outcome signal. Border Buddy's handoff to legal review is not a failure. It is the correct outcome for a case that exceeded the agent's authorization boundary. The system records it as a resolved handoff, not an unresolved conversation.

The distinction matters for measurement. An agent that escalates appropriately on high-risk cases is performing well. An agent that escalates everything because its confidence thresholds are miscalibrated is not. Tracking escalation outcomes separately from resolution outcomes surfaces the difference.

The Morales case closes with one of two outcomes: payment processed or legal review opened. Both are defined resolutions. Neither is ambiguous.

![Outcome measurement: HITL resolution card records whether payment was processed or escalated, not just that the conversation ended](../demos/assets/deel-hitl-card.png)

## Research grounding

- **Google Conversational Insights, Outcome and Sentiment Analysis**: production implementation of outcome measurement for contact center AI. Tracks resolution status, customer satisfaction signals, agent performance, and topic-level sentiment across conversations. Exports to BigQuery for custom dashboards and trend analysis. [cloud.google.com/conversational-insights/docs/overview](https://cloud.google.com/conversational-insights/docs/overview)

- **NIST AI RMF 1.0, GOVERN and MEASURE Functions**: AI systems require ongoing monitoring against defined performance criteria. Outcome measurement operationalizes the MEASURE function: tracking whether AI outputs achieve their intended goals and flagging drift before it becomes a risk. [nist.gov/system/files/documents/2023/01/26/AI RMF 1.0.pdf](https://www.nist.gov/system/files/documents/2023/01/26/AI%20RMF%201.0.pdf)

- **Anthropic: "Building Effective Agents"**: agent evaluation requires empirical grounding in real outcomes. Test suites that track whether agents accomplish their intended tasks, not just whether they produce syntactically correct responses, are the foundation of reliable agentic systems. [anthropic.com/engineering/building-effective-agents](https://www.anthropic.com/engineering/building-effective-agents)

- **Microsoft HAX Toolkit, G18: "Tell users when the system is uncertain"**: confidence calibration is a design requirement. Systems that express certainty when uncertain erode trust faster than systems that acknowledge uncertainty. Outcome tracking is how miscalibration is detected. [microsoft.com/en-us/haxtoolkit](https://www.microsoft.com/en-us/haxtoolkit)

## Related patterns

- [Testing and evaluation](13-testing-and-evaluation.md), outcome data drives test case updates; the two patterns form a closed loop
- [Trust calibration](04-trust-calibration.md), confidence calibration failures are visible only through outcome measurement; the two patterns are coupled
- [Human-in-the-loop](08-human-in-the-loop.md), escalation outcomes should be tracked separately from resolutions; they are different signals requiring different responses
