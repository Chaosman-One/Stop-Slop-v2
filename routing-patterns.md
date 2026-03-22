# Routing Patterns

Positive structural patterns organized by register. Use the pattern set that matches your derivation's registerTarget. These are not templates. They are basin indicators — structural habits that belong to specific registers. Adopting them routes the model into the correct neighborhood.

## Technical / Engineering Register

**Basin indicators:** Short paragraphs. Numbered sequences for multi-step content. Present tense for current state, past tense for completed work. Dates and owners attached to every commitment. No hedging vocabulary.

**Structural pattern:**
- Lead sentence: what changed or what is true now.
- Supporting sentences: evidence, measurement, or direct consequence.
- Close: next action with owner and date, or nothing.

**Sentence-level habits:**
- Subject-verb-object. No inversion.
- Concrete quantities replace adjectives. "Fast" becomes "under 200ms p99."
- Conditional statements use if/then, not "might" or "could potentially."

**Example register targets:** Stripe engineering blog, AWS postmortem, internal Google design doc, Linux kernel commit message.

---

## Conversational Essay Register

**Basin indicators:** "You" as default pronoun. Short-to-medium paragraphs. Declarative claims followed by a single concrete example. Parenthetical asides used sparingly for self-correction or qualification. Contractions.

**Structural pattern:**
- Open with a specific observation or claim. No throat-clearing.
- One example per claim. The example does the persuasive work, not the framing.
- Transitions are implicit. If you need a transition word, the paragraphs are in the wrong order.

**Sentence-level habits:**
- Mix declarative and interrogative, but questions are real questions (the answer is not in the next sentence).
- Two-item lists embedded in sentences. Never three.
- End paragraphs mid-thought occasionally. Let the next paragraph pick it up.

**Example register targets:** Paul Graham, Craig Mod, Mandy Brown, Robin Sloan's newsletter.

---

## Literary / Personal Essay Register

**Basin indicators:** Scene-first. Sensory detail before abstraction. Long sentences with subordinate clauses, alternating with short declaratives. First person used to locate the narrator in space, not to announce opinions.

**Structural pattern:**
- Open in a scene. A room, a street, a moment with physical coordinates.
- Abstraction arrives after the scene has earned it. The idea emerges from the material, not the reverse.
- Close with image, not summary. The last paragraph is a return to the physical.

**Sentence-level habits:**
- Concrete nouns carry the weight. Adjectives are rare and precise.
- Verbs are physical. People carry, drag, fold, press. They do not "navigate" or "grapple with."
- Time markers are specific. "Tuesday" not "one day." "After the second miscarriage" not "after a difficult period."

**Example register targets:** Granta, The Believer, John McPhee, Joan Didion, Annie Dillard, Brian Doyle.

---

## Business Communication Register

**Basin indicators:** First sentence is the ask or the update. No context-setting before the point. Bullets only for genuinely parallel items (three or more equivalent things). Names attached to actions.

**Structural pattern:**
- Line one: the thing the reader needs to know or do.
- Body: supporting detail, organized by priority not chronology.
- Close: explicit next step, or nothing.

**Sentence-level habits:**
- Active voice enforced. "We shipped" not "it was shipped."
- Timeframes are specific. "By March 28" not "soon" or "in the near term."
- No softening. "The launch is delayed two weeks" not "we may need to consider adjusting the timeline slightly."

**Example register targets:** Amazon's writing culture (six-pagers, narratives over slides), Basecamp internal communication, direct Slack messages between senior ICs.

---

## Narrative Fiction Register

**Basin indicators:** Point of view is consistent and embodied. The narrator sees what the character sees, knows what the character knows. Physical action carries psychological weight. Dialogue is compressed — people do not say everything they mean.

**Structural pattern:**
- Scene has a location rendered through specific objects before action begins.
- Tension lives in the gap between what characters say and what they do.
- Summary passages (covering days or weeks) are short and use different rhythm than scene passages.

**Sentence-level habits:**
- Said. Not "exclaimed," "muttered," "intoned." Said.
- One metaphor per page maximum. Each one must be drawn from the world of the story, not imported from outside it.
- Physical sensation over emotion words. "His hands were shaking" over "he felt afraid."

**Example register targets:** Cormac McCarthy, Denis Johnson, George Saunders, Ursula K. Le Guin, Marilynne Robinson.

---

## Instructional / How-To Register

**Basin indicators:** Second person. Imperative mood. Each step is one action. Outcomes are described so the reader can verify they did it right.

**Structural pattern:**
- State what the reader will have when they are done. One sentence.
- Numbered steps. Each step is one verb applied to one object.
- Verification after every step that can fail. "You should see a green checkmark in the top right."

**Sentence-level habits:**
- No explaining *why* mid-step. If context is needed, put it before the step sequence or after.
- Name the exact button, field, or command. "Click **Deploy**" not "proceed with deployment."
- Warnings precede the step they apply to, not follow it.

**Example register targets:** Stripe API docs, DigitalOcean tutorials, Julia Evans's zines, a good IKEA manual.

---

## Using These Patterns

1. Complete the derivation fields first.
2. Identify which register family your target falls into (or identify the closest one).
3. Adopt the basin indicators and structural patterns for that register.
4. If the target register falls between two families, name both and specify which habits to borrow from each.
5. Write.

The patterns are not rules to check after the fact. They are pre-commitments that shape what the model generates. The routing happens before the first token, not after the last one.
