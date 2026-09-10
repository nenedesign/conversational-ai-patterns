# Demo: Travel Disruption

> **Disclaimer:** The company name and branding shown in this prototype are used for design demonstration purposes only. This is an unsolicited concept exploration, not an official product of or affiliated with the named company.

---

A browser-based conversational AI prototype demonstrating how an agentic travel assistant handles flight disruption, CFAR refunds, and loyalty upgrades, from proactive alert to full resolution, in a single conversation.

Video walkthrough available at [fromus.ca](https://fromus.ca). To see a live demo, reach out on [LinkedIn](https://www.linkedin.com/in/nevilleko/).

---

## The scenario

Three travellers. Three distinct situations. One agent that already knows each one's context before they speak.

- **Joe Chen**: flight UA234 to JFK cancelled due to crew shortage. Has Disruption Assistance coverage. Needs rebooking, overnight hotel, and expense claim.
- **Sarah Kim**: trip cancelled. Has Cancel for Any Reason (CFAR) coverage. Needs a full refund.
- **Alex Morgan**: Platinum member, flight on time. Eligible for a seat upgrade and lounge access before departure.

Each persona demonstrates a different facet of context-aware, action-first conversational AI. The agent does not ask the user to explain their situation. It already knows.

---

## Patterns demonstrated

| Pattern | Where it appears |
|---------|-----------------|
| [Proactive alerts](../patterns/01-proactive-alerts.md) | Agent surfaces disruption context the moment the user opens the chat |
| [Context awareness](../patterns/02-context-awareness.md) | Agent knows each traveller's booking, coverage type, and membership status upfront |
| [Action-first framing](../patterns/03-action-first-framing.md) | Every opening message leads with what the agent can do, not what it knows |
| [Autonomous chaining](../patterns/09-autonomous-chaining.md) | Joe's resolution: one confirmation triggers rebook → hotel → expense claim |
| [Resolution confirmation](../patterns/10-resolution-confirmation.md) | "You're all set, Joe", dedicated resolution screen with booking ref, hotel, and claim number |
| [Knowledge grounding](../patterns/11-knowledge-grounding.md) | Agent responses grounded in a RAG pipeline over policy and regulatory documents |

---

## Screenshots

### Multi-persona selector
<!-- Screenshot: Dreamer, three-persona selector with Joe, Sarah, Alex -->
*[Screenshot: Persona selector, three travellers, three distinct scenarios]*

### Context-aware opening: Joe Chen
<!-- Screenshot: Joe's opening message with flight, coverage, and rebooking offer -->
*[Screenshot: HTS Assist, agent opens with Joe's flight context and immediate rebooking offer]*

### Autonomous chain: Joe's resolution
<!-- Screenshot: Three-step chain, rebook confirmed, hotel options, expense claim filed -->
*[Screenshot: Autonomous chaining, flight rebooked, hotel selected, expense claim filed in one session]*

### Resolution confirmation: "You're all set, Joe"
<!-- Screenshot: Resolution screen with booking ref, hotel, and claim number -->
*[Screenshot: Resolution confirmation, dedicated screen with all reference numbers visible]*

### Context-aware opening: Sarah Kim
<!-- Screenshot: Sarah's CFAR refund offer -->
*[Screenshot: HTS Assist, agent opens with Sarah's CFAR coverage and immediate refund offer]*

### Context-aware opening: Alex Morgan
<!-- Screenshot: Alex's upgrade eligibility offer -->
*[Screenshot: HTS Assist, agent opens with Alex's Platinum status and upgrade eligibility]*

---

## Knowledge grounding: the RAG layer

This prototype is backed by an agentic RAG pipeline, not hardcoded responses. Policy documents, carrier regulations, and fintech product terms are embedded in a Supabase vector store. When a policy question arises, the agent retrieves the relevant passages and grounds its response in those documents.

### n8n RAG pipeline
<!-- Screenshot: n8n RAG workflow -->
*[Screenshot: n8n RAG pipeline, webhook → semantic search → Supabase vector store → Claude response]*

### Supabase vector store
<!-- Screenshot: Supabase table snippet showing embedded document chunks -->
*[Screenshot: Supabase vector store, embedded policy document chunks with source metadata]*

The retrieval architecture means that agent responses on coverage, eligibility, and regulatory requirements are traceable to specific source documents, not attributed to model training. See [Knowledge grounding](../patterns/11-knowledge-grounding.md) for a full treatment of this pattern.

---

## Technical implementation

- **Frontend:** Single-file HTML/CSS/JS browser prototype with three switchable personas
- **Conversation engine:** Mock sequences per persona with screen-tag rendering (`[[screen:xxx]]`)
- **Screen transitions:** CSS opacity transitions between named screens (disruption alert, hotel options, resolution)
- **Backend:** n8n webhook → Claude Sonnet 4.6 → agentic RAG over Supabase vector store
- **Knowledge base:** Policy documents and regulatory text embedded with semantic embeddings; retrieved per query
