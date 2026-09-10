# Demo: Private Assistant *(coming soon)*

> **Disclaimer:** The company name and branding shown in this prototype are used for design demonstration purposes only. This is an unsolicited concept exploration, not an official product of or affiliated with the named company.

---

A conversational AI prototype demonstrating privacy-first interaction design, local model inference, minimalist floating prompt UI, and GDPR-aligned data handling, with no cloud dependency.

---

## The concept

Most conversational AI sends your data to a cloud. Every message, every query, every piece of context, processed on remote servers, retained in logs, used to improve models. For many use cases, this is an acceptable tradeoff. For personal data, healthcare, legal work, or any context where privacy is the product, it is not.

This prototype demonstrates what conversational AI looks like when privacy is the constraint that shapes everything else. Local model inference. Minimal data retention by design. Consent patterns that are legible, not buried. A floating prompt UI that is ambient but not intrusive.

---

## Patterns to demonstrate

| Pattern | How it applies |
|---------|---------------|
| [Capability boundaries](../patterns/07-capability-boundaries.md) | Agent is explicit about what it retains, what it forgets, and when |
| [Trust calibration](../patterns/04-trust-calibration.md) | Agent expresses uncertainty about local model limitations vs. cloud model capabilities |
| [Progressive disclosure](../patterns/05-progressive-disclosure.md) | Privacy controls surface progressively, consent at the point of need, not upfront |
| [Human-in-the-loop](../patterns/08-human-in-the-loop.md) | User explicitly approves any action that touches persistent storage |

---

## Status

This prototype is in design. It will be built after the Payroll Intelligence and Travel Disruption prototypes are complete.

Video walkthrough will be available at [fromus.ca](https://fromus.ca) when ready. To discuss the concept, reach out on [LinkedIn](https://www.linkedin.com/in/nevilleko/).
