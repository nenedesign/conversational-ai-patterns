# Pattern 03: Action-First Framing

## The problem

Most AI assistants explain before they act. They describe the situation, acknowledge the user's concern, outline the options, and eventually get around to what they can do. This is the wrong order. In high-stakes or time-sensitive contexts, a cancelled flight, a payroll deadline, a compliance issue, the user does not need a summary of what they already know. They need to know what happens next.

An agent that leads with information when it could lead with action wastes the user's most scarce resource: attention. It also signals uncertainty. An agent that knows what to do says so.

## The pattern

**The agent leads with the action it can take, not with the information it holds.**

Action-first framing does not mean skipping explanation. It means sequencing correctly:

1. **State what the agent can do**: the specific, concrete action available right now
2. **Provide just enough context**: why this action is appropriate, what it covers
3. **Ask for confirmation**: a simple yes/no that puts the user in control

The user learns what happened and why it matters through the action being offered, not through a preamble that delays it.

**What makes it work:** The agent has already done the analysis. The opening statement is the conclusion, not the setup. Details follow only after the user engages.

**The risk to manage:** Action-first framing should not skip consent. The agent offers; the user approves. This pattern works in combination with [Human-in-the-loop](08-human-in-the-loop.md), never as a replacement for it.

## Seen in practice

*Demonstrated in: [Travel Disruption](../demos/travel-disruption.md)*

### Travel Disruption: rebooking, refund, and upgrade offers

Each HTS Assist persona receives an action-first opening:

- **Joe Chen (flight cancelled):** "I can rebook you on UA238, departing 7:00 AM Tuesday. Shall I go ahead?", not "Your flight was cancelled due to a crew shortage. Here is some information about your options."
- **Sarah Kim (CFAR refund):** "I can process a full refund right now. Would you like me to go ahead?", not "Your Cancel for Any Reason coverage is active and eligible for a refund under the following conditions."
- **Alex Morgan (upgrade):** "You're eligible for a seat upgrade on this flight, want me to check what's available?", not "As a Platinum member, you have access to upgrade benefits."

In each case, the agent's knowledge of the user's context and coverage is expressed through the action being offered, not stated separately.

<!-- Screenshot: Dreamer, action-first opening messages across Joe, Sarah, Alex personas -->
*[Screenshot: HTS Assist, action-first opening messages for all three personas]*

## Research grounding

- **Google Conversation Design Guidelines**: conversation design principles for Google Assistant: lead with resolution, not with information retrieval. Agents should complete tasks, not describe them. [designguidelines.withgoogle.com/conversation](https://designguidelines.withgoogle.com/conversation/)

- **Apple Human Interface Guidelines: Siri**: "complete requests without requiring users to navigate away": the agent should resolve the situation in the current interaction, not redirect. [developer.apple.com/design/human-interface-guidelines](https://developer.apple.com/design/human-interface-guidelines/)

- **ACL 2023 Tutorial: "Goal Awareness for Conversational AI"**: agents with goal awareness do not merely respond; they pursue resolution. Initiative belongs with the agent. [aclanthology.org/2023.acl-tutorials.1](https://aclanthology.org/2023.acl-tutorials.1/)

## Related patterns

- [Context awareness](02-context-awareness.md), action-first framing requires pre-loaded context; an agent that doesn't know the situation cannot lead with a specific action
- [Autonomous chaining](09-autonomous-chaining.md), once the first action is confirmed, the agent chains subsequent steps without requiring the user to re-initiate
- [Human-in-the-loop](08-human-in-the-loop.md), action-first framing always pairs with explicit user confirmation before consequential actions are taken
