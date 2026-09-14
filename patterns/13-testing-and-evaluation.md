# Pattern 13: Testing and Evaluation

## The problem

Conversational AI fails in ways that are hard to see. A model returns a plausible-sounding answer that misses the intent. A flow that worked last week breaks after a prompt change. An edge case no one anticipated shows up in production. Unlike deterministic software, where a broken function throws an error, a broken conversational agent still produces a response. It just produces the wrong one.

Without structured testing, these failures accumulate silently. The agent drifts from its intended behavior. Users lose trust. The team loses visibility into what changed and why.

Variability makes it worse. Conversational inputs are not fixed. Users phrase the same intent dozens of ways. A test suite that only covers the expected phrasing misses most of the surface area.

## The pattern

**The team maintains a library of structured test cases derived from real conversations, validates every change automatically, and reviews production logs to catch failure patterns before they reach users.**

A testing and evaluation framework has four properties:

1. **Test cases from real conversations**: each test case includes an input utterance, expected intent, expected entities, and the expected response path. Test cases are derived from real or representative user conversations, not invented by the development team.
2. **Automated regression**: every agent change triggers a test run. Regressions are caught before deployment. The team knows immediately when a change breaks an existing flow.
3. **Conversation history review**: the team reviews production logs regularly to identify failure patterns. Frequent NoMatch events, unexpected escalations, and conversations that end without resolution are signals worth investigating.
4. **Edge case coverage**: the test library covers ambiguous inputs, missing parameters, mid-flow topic changes, and recovery scenarios. The happy path is the minimum, not the goal.

**What makes it work:** Testing is part of the development workflow, not added at the end. Real conversations drive the test library. The team measures what the agent actually does, not what they expect it to do.

## Seen in practice

*Demonstrated in: [Travel Disruption](../demos/travel-disruption.md)*

### Dreamer: three personas as structured test cases

The Dreamer demo's persona selector (Joe Chen, Sarah Kim, Alex Morgan) is a testing pattern in visible form. Each persona was designed to exercise a distinct agent behavior: disruption rebooking, CFAR refund processing, loyalty upgrade. These are not arbitrary characters. They are structured test cases that validate the agent's ability to handle different intents, different emotional registers, and different resolution paths from the same entry point.

Building the demo this way means the team can validate every change against three known scenarios with defined expected outcomes. Regression is immediately visible.

![Dreamer persona selector: three structured test scenarios in one interface, each validating a distinct agent behavior](../demos/assets/dreamer-persona-selector.png)

## Research grounding

- **Google Conversational Agents, Test Cases and Validation Tools**: built-in test case management for Conversational Agents: create and maintain test cases, run automated validation against agent flows, and review conversation history logs to identify failure patterns and NoMatch events. [cloud.google.com/dialogflow/cx/docs/concept/test-cases](https://cloud.google.com/dialogflow/cx/docs/concept/test-cases)

- **NIST AI RMF 1.0, MEASURE Function**: evaluation as a core risk management practice. AI systems should be tested against defined performance metrics before deployment and monitored continuously in production. Evaluation coverage should include edge cases and failure modes, not just expected behavior. [nist.gov/system/files/documents/2023/01/26/AI RMF 1.0.pdf](https://www.nist.gov/system/files/documents/2023/01/26/AI%20RMF%201.0.pdf)

- **Anthropic: "Building Effective Agents"**: recommends testing agentic pipelines with curated datasets of inputs that cover diverse scenarios, with clear success criteria defined in advance for each case. [anthropic.com/engineering/building-effective-agents](https://www.anthropic.com/engineering/building-effective-agents)

- **Microsoft HAX Toolkit, G17: "Conduct testing under various conditions"**: AI systems should be tested across varied inputs, user types, and edge cases before deployment. Test coverage should reflect the diversity of real user behavior. [microsoft.com/en-us/haxtoolkit](https://www.microsoft.com/en-us/haxtoolkit)

## Related patterns

- [Conversation repair](16-conversation-repair.md), testing should specifically cover repair scenarios: NoMatch, NoInput, and ambiguous inputs
- [Capability boundaries](07-capability-boundaries.md), test cases should include inputs that push against capability limits to verify boundary behavior
- [Human-in-the-loop](08-human-in-the-loop.md), HITL escalation paths are high-stakes and should be covered by dedicated test cases
