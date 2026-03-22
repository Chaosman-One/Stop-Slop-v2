# Examples: Routing vs. Restriction

Each example shows the same input transformed two ways: first by restriction (identifying and removing bad patterns), then by routing (deriving into a specific basin before generating). The routing version does not reference the failure patterns at all.

---

## Example 1: Project Update

**Input:** Write a project update about a delayed database migration.

**Restriction method output:**
> The database migration has been delayed. The team encountered unexpected complexity in the schema transformation layer. Moving forward, we plan to address these challenges by allocating additional engineering resources. The timeline has shifted to accommodate these changes.

*What restriction would catch:* "Moving forward" (jargon), "encountered" (passive-adjacent), "address these challenges" (vague). A restriction pass would cut those phrases. But the underlying problem — no dates, no names, no specific cause — survives because the restriction method operates on surface tokens, not on the basin the prose was generated from.

**Routing method derivation:**
| Field | Value |
|-------|-------|
| readerProfile | CTO, knows the system, wants status in under 30 seconds |
| registerTarget | Amazon weekly status email |
| sceneAnchor | Phone, Monday morning, scanning before leadership sync |
| textureConstraint | Postgres, foreign key constraints, staging cluster, CI |

**Routing method output:**
> The Postgres migration ships April 4 instead of March 28. Foreign key constraints in the invoicing tables require a two-pass transform that Ben's team scoped last Thursday. Staging is green. CI pipeline needs one more validation run against the prod replica, which Priya owns and expects done by Wednesday.

*No restriction was applied. The derivation routed into a basin where jargon, vagueness, and passive voice do not exist — because Amazon status emails do not contain them.*

---

## Example 2: Blog Post Opening

**Input:** Write the opening of a blog post about why most product roadmaps fail.

**Restriction method output:**
> Most product roadmaps fail. Teams spend weeks building detailed plans that never survive contact with users. The roadmap becomes a political document instead of a planning tool.

*What restriction would catch:* Possible binary contrast setup. "Becomes" is borderline false agency. But the sentences are already short and direct — restriction has little to cut. The real problem is that the prose is register-neutral. It could appear in any of ten thousand identical blog posts. It occupies the dead center of the generic-explainer basin.

**Routing method derivation:**
| Field | Value |
|-------|-------|
| readerProfile | Senior PM, three failed launches behind her, reading this because the title matched her week |
| registerTarget | Lenny's Newsletter — conversational, specific, uses real company examples |
| sceneAnchor | Laptop, 10pm, half a glass of wine, the quarterly planning doc still open in the next tab |
| textureConstraint | Jira epics, quarterly OKRs, customer interview transcripts, the "confidence" column nobody fills in |

**Routing method output:**
> You have a roadmap. It lives in a Jira board with fourteen epics, each one tagged to a quarterly OKR that seemed urgent in January. Two of those epics have shipped. Three got descoped into "fast follows" that will never happen. The rest sit in a column called "Planned" that means "we agreed to this in a room and nobody has touched it since." Your roadmap did not fail because you planned wrong. Your roadmap failed because the confidence column — the one that was supposed to say how sure you were about each bet — is empty on every single row.

*The routing version is longer because the basin it occupies rewards specificity. The Jira board, the confidence column, the quarterly OKR, the "fast follows" — these are objects from the reader's actual world. They were not produced by avoiding bad patterns. They were produced by routing into a register where those objects are the native vocabulary.*

---

## Example 3: Personal Essay Opening

**Input:** Write the opening of a personal essay about leaving a job you loved.

**Restriction method output:**
> I left a job I loved last year. It was the hardest professional decision I have made. The company had given me opportunities I never expected, and walking away felt like betrayal.

*What restriction would catch:* "Hardest professional decision" is a vague declarative. "Opportunities I never expected" is generic. But again — restriction can trim this, but cannot redirect it. The prose is in the correct grammatical shape but the wrong basin. It reads like a LinkedIn post because no derivation routed it elsewhere.

**Routing method derivation:**
| Field | Value |
|-------|-------|
| readerProfile | Someone who has also left something good and is still not sure it was right |
| registerTarget | The Believer — literary, unhurried, scene-first, earns its abstractions |
| sceneAnchor | Reading on a couch on a Saturday, willing to sit with something slow |
| textureConstraint | The office kitchen, a particular mug, the commute, the badge that stopped working |

**Routing method output:**
> The badge stopped working on a Friday. I held it to the reader and the little light stayed red and I stood there in the lobby with my bag on my shoulder, watching other people tap through. Someone from facilities came out and asked my name and I spelled it and he typed it in and shook his head. That was the building telling me I had already left. I had put in notice eleven days earlier but my body kept showing up at 8:15 because it did not know what else to do in the mornings.

*No phrases were avoided. No structures were prohibited. The derivation specified a literary register, a scene anchor (the office), and texture objects (badge, lobby, the commute). The model routed into a basin where the prose is embodied, physical, and specific — because The Believer does not publish vague declaratives about "opportunities."*

---

## Example 4: Technical Explanation

**Input:** Explain why microservices introduce latency.

**Restriction method output:**
> Microservices introduce latency because each service call adds network overhead. A monolithic application makes function calls in-process, which are fast. Microservices replace those with HTTP or gRPC calls across the network, adding serialization, deserialization, and round-trip time.

*This is already decent. Technical explanation is a basin where the model has strong training signal. Restriction has almost nothing to cut. But the prose still reads like a textbook — competent, impersonal, addressed to no one in particular.*

**Routing method derivation:**
| Field | Value |
|-------|-------|
| readerProfile | Junior backend engineer who just watched her p99 latency double after the team split the monolith |
| registerTarget | Julia Evans blog post — visual thinking, "you" pronoun, specific numbers, friendly |
| sceneAnchor | At her desk staring at a Datadog dashboard with a red spike |
| textureConstraint | p99 latency, Datadog trace waterfall, gRPC call, JSON serialization, 3ms vs 80ms |

**Routing method output:**
> You had a monolith. Your checkout function called your inventory function and it took 3ms because it was a function call inside the same process. You split them into two services. Now checkout sends a gRPC request to inventory across the network — your 3ms function call turned into a round trip that takes 12ms on a good day and 80ms when the network hiccups. Open your Datadog trace waterfall. Every colored bar is a network hop that used to be free. You added eight services, so you added eight bars, and your p99 went from 40ms to 320ms. That is where your latency went.

*Same information, different basin. The Julia Evans register forces "you," forces specific numbers, forces the Datadog trace as a visual anchor. The model did not avoid textbook patterns. It occupied a space where textbook patterns do not live.*

---

## The Mechanism

In every example, the restriction method identifies bad tokens and removes them. The routing method never sees the bad tokens. It commits to a register, a reader, a scene, and a set of material objects before generating. The result is not "AI text with the AI parts scraped off." It is text that was generated from a different starting position.

Restriction is sandpaper. Routing is trajectory selection. They are not equivalent operations performed at different stages. They are different operations entirely.
