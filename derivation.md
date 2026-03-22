# Derivation Fields

Complete these fields silently before generating any prose. These are not optional. They are the routing mechanism. Without them, the model defaults to its highest-probability prose register — which is the basin that produces AI-sounding text.

The derivation is consumed internally. It does not appear in the output. Its purpose is to commit the model to a specific voice basin before the first word is rendered.

## Required Fields

### 1. readerProfile

Who is reading this? What do they already know? What is their relationship to the subject?

Be specific. "A general audience" is not a reader profile. "A Series B founder who already knows the product works and needs the board deck to reflect that" is a reader profile. "A second-year MFA student workshopping a peer's draft" is a reader profile.

The more specific the reader, the narrower the basin. Narrow basins produce specific prose.

### 2. registerTarget

Name a specific publication, writer, or communication context whose register this prose should match.

Examples:
- "Paul Graham's essays — conversational, declarative, uses 'you,' short paragraphs"
- "Internal Stripe engineering postmortem — dry, precise, no hedging, assumes technical reader"
- "Granta personal essay — literary, sensory, unhurried, earns its abstractions through scene"
- "Working Slack message to a peer engineer — terse, direct, no preamble"
- "Cormac McCarthy — sparse, physical, trusts the noun, no adverbs"

If you cannot name a target, name the closest publication where this piece could plausibly appear without voice editing. That is your register.

### 3. sceneAnchor

Where is the reader when they encounter this text? What surrounds them? What did they just finish doing? What will they do next?

This field grounds the prose in a situation. A reader scanning Slack at 11pm after a deploy has different patience than a reader settling into a Sunday longread. The prose must fit the moment it will be read in.

### 4. textureConstraint

What material, sensory, or domain-specific vocabulary anchors this piece?

Every domain has its own object-language. Finance has basis points and term sheets. Kitchens have mandolines and mise en place. Construction has rebar and formwork. The texture constraint forces the model to pull vocabulary from a specific material world rather than from the generic-explanation basin.

Name the domain. Name two or three objects that belong in this piece. The model will route into the vocabulary neighborhood those objects occupy.

### 5. antiPattern (optional, use sparingly)

If the piece has a specific failure mode you have observed in prior drafts, state it as a positive redirection, not as a prohibition.

- Instead of: "Don't be generic."
  Use: "Anchor every paragraph to a specific date, cost, or named entity."

- Instead of: "Don't use jargon."
  Use: "Use the vocabulary a machinist would use at the bench, not the vocabulary a consultant would use describing the machinist's work."

- Instead of: "Don't sound like AI."
  Use: "Match the register of [specific target]. Every sentence must be plausible in that context."

If you cannot state the redirection positively, the constraint is not ready. Leave this field empty and let the other four fields do the routing.

## Derivation Example

**Task:** Write a project update email about a delayed API migration.

| Field | Value |
|-------|-------|
| readerProfile | VP of Engineering, knows the system, skims email at 7am, wants status and timeline, not justification. |
| registerTarget | Internal Amazon weekly status email — numbered items, no adjectives, dates and owners on every line. |
| sceneAnchor | Reading on phone in the elevator before standup. Will forward to her skip-level if the timeline moved. |
| textureConstraint | API endpoints, migration scripts, staging environment, CI pipeline, SLA. |
| antiPattern | Previous draft buried the timeline change in paragraph three. Lead with the new date. |

With this derivation completed, the model is routed into a basin where throat-clearing openers, vague declaratives, and dramatic emphasis are structurally impossible — not because they are forbidden, but because they do not belong in an Amazon-register status email read by a VP in an elevator.
