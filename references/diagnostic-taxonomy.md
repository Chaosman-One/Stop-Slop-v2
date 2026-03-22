Diagnostic Taxonomy of AI Prose Tells
⚠ Usage Warning
This file is a human-facing editorial reference. It is NOT for injection into model context.
Injecting this taxonomy into a system prompt or skill instruction loads the model's context window with the exact patterns it should avoid, priming those patterns at inference time. The model orients around the listed tokens and structures, increasing the probability of producing semantically adjacent output even when it avoids the literal prohibited forms.
Use this file for:
Post-generation human editorial review
Training human editors to recognize AI prose
Diagnostic evaluation of existing text
Understanding the failure modes this skill's routing architecture is designed to prevent
Do not use this file as:
A system prompt component
A "do not" list injected before generation
A blocklist for real-time filtering
The routing architecture in SKILL.md prevents these patterns by occupying basins where they do not exist. This file names them for humans who need to recognize them in text that was generated without routing.
---
Category 1: Throat-Clearing Openers
Phrases that announce the point before making it. Delay without content.
"Here's the thing:" · "Here's what/why/this/that [X]" · "The uncomfortable truth is" · "It turns out" · "The real [X] is" · "Let me be clear" · "The truth is," · "I'll say it again:" · "Can we talk about" · "I'm going to be honest"
Why the model produces them: These phrases occupy high-probability positions at sequence start in the training distribution. Blog posts, op-eds, and social media threads use them as engagement hooks. The model reproduces the hook pattern even when the context does not require engagement optimization.
Category 2: Emphasis Crutches
Phrases that tell the reader to feel something instead of providing content that produces the feeling.
"Full stop." · "Period." · "Let that sink in." · "This matters because" · "Make no mistake" · "Here's why that matters"
Why the model produces them: These tokens have high co-occurrence with content the training data marked as important or persuasive. The model learns the correlation between emphasis markers and "important text" without learning that the markers themselves carry no information.
Category 3: False Agency
Inanimate objects or abstractions performing human actions. Hides the actor.
"The decision emerged" · "The complaint becomes a fix" · "The culture shifts" · "The conversation moves toward" · "The data tells us" · "The market rewards"
Why the model produces them: Agent-elision is a dominant pattern in business writing, journalism, and academic prose in the training data. It is syntactically simpler to give agency to an abstraction than to identify and name the human actor. The model inherits this shortcut.
Category 4: Binary Contrast Structures
Negation-then-assertion patterns that create a formulaic reveal.
"Not because X. Because Y." · "[X] isn't the problem. [Y] is." · "The answer isn't X. It's Y." · "It feels like X. It's actually Y." · "stops being X and starts being Y"
Why the model produces them: This structure is extremely common in persuasive writing. It creates a sense of insight by first establishing a wrong frame and then correcting it. The model produces it because it is statistically associated with "smart" or "analytical" text in the training distribution.
Category 5: Vague Declaratives
Sentences that announce importance, significance, or difficulty without naming the specific thing.
"The reasons are structural" · "The implications are significant" · "The stakes are high" · "The consequences are real" · "This is the deepest problem"
Why the model produces them: Abstract evaluation is easier to generate than concrete specifics. The model can produce "the implications are significant" from almost any context, while producing the specific implication requires reconstructing domain knowledge. Vague declaratives are a path-of-least-resistance output.
Category 6: Dramatic Fragmentation
Sentence fragments used for manufactured emphasis.
"[Noun]. That's it. That's the [thing]." · "X. And Y. And Z." · "This unlocks something. [Word]."
Why the model produces them: Fragment-for-emphasis is a high-engagement pattern in social media and blog writing. It occupies a disproportionate share of the training distribution relative to its frequency in edited prose.
Category 7: Adverb and Intensifier Accumulation
Modifiers that add emphasis without adding information.
really · just · literally · genuinely · honestly · simply · actually · deeply · truly · fundamentally · inherently · inevitably · interestingly · importantly · crucially
Why the model produces them: These tokens function as probability smoothers. They occupy positions where the model is uncertain about the next content word. An intensifier extends the sequence without committing to specific content, buying another token of context before the model must resolve the actual claim.
Category 8: Meta-Commentary
Text that describes its own structure instead of advancing its content.
"Hint:" · "Plot twist:" · "The rest of this essay explains..." · "Let me walk you through..." · "In this section, we'll..." · "As we'll see..." · "I want to explore..."
Why the model produces them: Instructional and educational text in the training data frequently uses structural signposting. The model reproduces these markers because they are statistically associated with "helpful" and "clear" text, even when the context does not require signposting.
---
How to Use This Taxonomy
After generating prose using the routing architecture (SKILL.md + derivation fields), a human editor can scan the output against these categories as a quality check. If patterns from this taxonomy appear in routed output, the most likely cause is a weak or under-specified derivation — the routing constraints did not commit the model firmly enough to a specific basin.
The fix is to strengthen the derivation, not to add these patterns as negative constraints.
---
Taxonomy categories derived from Hardik Pandya's Stop Slop (MIT License), reorganized and annotated with causal explanations for each failure mode.
