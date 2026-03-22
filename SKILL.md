---
name: stop-slop-v2
description: Produce clean, human-register prose by routing into specific voice basins. Use when drafting, editing, or reviewing text. Replaces restriction-based anti-slop methods with retrieval-shaped positive constraints.
metadata:
  trigger: Writing prose, editing drafts, reviewing content for AI patterns
  author: Wake & Claude (Axiom), rebuilt from Hardik Pandya's Stop Slop diagnostic taxonomy
  architecture: Retrieval-Shaped Prompting & Constrained Synthesis v2
---

# Stop Slop v2

Route prose into specific human-register basins. Do not load AI failure patterns into context.

## Architecture Principle

Negative prompting activates the basin it intends to suppress. Listing phrases to avoid primes those phrases. Cataloguing structures to reject makes those structures salient at inference time. The model spends generation energy resisting tokens that would not have been attractive if they had not been injected.

This skill uses the opposite mechanism: **positive routing constraints that make slop structurally impossible.** The model never sees the failure patterns. It sees where to go, not where to avoid.

## Before Generating Prose

Complete the derivation fields in [references/derivation.md](references/derivation.md) silently before writing. Do not skip this step. Do not treat it as optional. The derivation commits the model to a specific basin before the first sentence is rendered. Without it, the model defaults to its highest-probability prose register, which is the slop basin.

## Core Routing Constraints

These six constraints are simultaneous. Every sentence of output must satisfy all six. They are phrased as positive requirements, not prohibitions.

### 1. Human Subject Rule

Every sentence has a named or specific human subject performing a concrete action. "You" counts. A named role ("the engineer," "her landlord") counts. Inanimate objects, abstractions, and unnamed collectives do not act.

- ✓ "She cancelled the contract on Thursday."
- ✓ "You will lose three clients if the API goes down."
- ✗ "The decision emerged from weeks of discussion."
- ✗ "The market rewards bold moves."

### 2. Material Anchor Rule

Every claim, observation, or argument must contain at least one concrete noun: an object, a cost, a distance, a duration, a name, a sensory detail. Sentences that consist only of abstract nouns evaluating other abstract nouns fail this rule.

- ✓ "The migration will take nine weeks and cost the Austin office $14,000 in overtime."
- ✗ "The implications of this shift are significant."

### 3. Single-Pass Assertion Rule

State the point on arrival. No runway. No negation-then-assertion. No "not X, but Y." No previewing what you are about to say. The first sentence of a paragraph is the claim. Everything after it is evidence or consequence.

- ✓ "Retention dropped 12% after the rebrand."
- ✗ "The problem isn't the product. It's the positioning."

### 4. Rhythm Variation Rule

No three consecutive sentences may fall within five words of each other in length. Inline lists contain two items. Paragraphs do not end with their shortest sentence. No stacked fragments.

### 5. Register Lock Rule

The derivation fields specify a target register. Every sentence must be plausible in that register. If the derivation says "working engineer's Slack message," then no sentence may read like a keynote speech. If the derivation says "literary essay for Granta," then no sentence may read like a blog post. The register is a fence. Stay inside it.

### 6. Earned Emphasis Rule

No sentence may announce its own importance. Importance is earned by the specificity and consequence of the content. "This matters" is empty. The reader decides what matters based on what you showed them.

- ✓ "If the patch ships late, the 2.0 launch slips to Q3 and the Series B deck needs new numbers."
- ✗ "This matters because timing is everything."

## Quick Routing Checks

Before delivering prose, run these checks. Each one is a presence test, not an absence test.

- Does every sentence have a human subject? Find the actor in each one.
- Does every paragraph contain at least one concrete noun (object, number, name, place, texture)?
- Does the first sentence of each paragraph state the point?
- Do sentence lengths vary across every three-sentence window?
- Does the prose stay inside the register specified in the derivation?
- Is every claim of importance backed by a specific consequence in the same paragraph?
- Could a reader identify the author's target register without being told? (If the prose is register-neutral, the derivation failed.)

## Scoring

Rate 1-10 on each dimension. Each dimension measures a positive quality.

| Dimension | Measures |
|-----------|----------|
| Specificity | Concrete nouns per paragraph. Objects, costs, names, textures, durations. |
| Agency | Percentage of sentences with a human subject performing a concrete verb. |
| Rhythm | Sentence-length variance across the piece. Standard deviation of word counts. |
| Register fidelity | Would this paragraph be publishable in the target outlet without editing for voice? |
| Density | Ratio of load-bearing sentences to total sentences. Every sentence advances the argument or provides evidence. |

**Below 35/50: the derivation was too thin. Re-derive and rewrite.**

## Reference Files

- [references/derivation.md](references/derivation.md) — Derivation fields. Complete before every prose task.
- [references/routing-patterns.md](references/routing-patterns.md) — Positive structural patterns organized by register.
- [references/examples.md](references/examples.md) — Before/after transformations showing routing vs. restriction.
- [references/diagnostic-taxonomy.md](references/diagnostic-taxonomy.md) — Human-facing reference catalogue of AI prose tells. For editorial review, NOT for injection into generation context.

## License

MIT
