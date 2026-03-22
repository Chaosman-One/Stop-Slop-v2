# Stop Slop v2

A skill for producing clean, human-register prose from LLMs. Rebuilt from [Hardik Pandya's Stop Slop](https://github.com/hardikpandya/stop-slop) using retrieval-shaped architecture.

## The Problem with v1

Stop Slop v1 is a restriction-prompting architecture: lists of phrases to avoid, structures to reject, and checks that scan for bad patterns. When a human editor reads these lists and then writes, the method works. When injected into an LLM's context window, the method backfires.

Loading "Here's the thing:" and "Let that sink in" and "Not because X. Because Y." into the model's context primes those exact tokens. The model orients around the patterns it is supposed to suppress and spends inference energy resisting them — often producing output that avoids the literal prohibited form but stays semantically adjacent to the same basin.

Negative prompting activates the basin it intends to suppress.

## What v2 Does Instead

v2 uses positive routing constraints that make AI prose patterns structurally impossible without ever naming them.

The mechanism has three parts:

**1. Derivation before generation.** Before writing, the model completes five fields: reader profile, register target, scene anchor, texture constraint, and (optionally) a positive redirection. This commits the model to a specific voice basin before the first token.

**2. Six simultaneous routing constraints.** Every sentence must have a human subject, a material anchor, single-pass assertion, rhythm variation, register fidelity, and earned emphasis. These are presence tests, not absence tests.

**3. Positive register patterns.** Instead of listing structures to avoid, v2 provides structural habits that belong to specific registers — technical, conversational essay, literary, business, fiction, instructional. The model adopts the habits of the target register, occupying a basin where slop patterns do not exist.

The diagnostic taxonomy from v1 is preserved as a human-facing editorial reference, explicitly separated from the generation context.

## Skill Structure

```
stop-slop-v2/
├── SKILL.md                            # Core routing instructions
├── references/
│   ├── derivation.md                   # Pre-generation derivation fields
│   ├── routing-patterns.md             # Positive patterns by register
│   ├── examples.md                     # Before/after: routing vs. restriction
│   └── diagnostic-taxonomy.md          # Human-facing AI tell reference (NOT for model injection)
├── README.md
└── LICENSE
```

## Quick Start

**Claude Code:** Add this folder as a skill.

**Claude Projects:** Upload `SKILL.md`, `references/derivation.md`, and `references/routing-patterns.md` to project knowledge. Do NOT upload `diagnostic-taxonomy.md` — it is for human review only.

**Custom instructions:** Copy the core routing constraints and derivation fields from `SKILL.md` and `references/derivation.md`.

**API calls:** Include `SKILL.md` and `references/derivation.md` in your system prompt. Load `routing-patterns.md` when the register family is identified.

## Architecture

Built on Retrieval-Shaped Prompting & Constrained Synthesis v2:

- **Code/systems** handle combinatorics and hard state (not applicable for pure prose, but present in tools like NPC Forge and Wheel of Existence where this methodology originated)
- **Context/prompting** handles routing and governance (derivation fields, register targeting, routing constraints)
- **Model** acts as a bounded semantic resolver within the routed basin (generates prose under constraint)
- **Validation** handles persistence and correction (scoring rubric, human editorial review via diagnostic taxonomy)

## Attribution

Diagnostic taxonomy derived from [Hardik Pandya's Stop Slop](https://github.com/hardikpandya/stop-slop) (MIT License). Restructured using methodology developed by Wake, Claude (Axiom), Lisa, Eos, and Gemini across the Local Group research program.

## License

MIT
