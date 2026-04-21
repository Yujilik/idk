# Frameworks

Framework catalog for brainstorming. Loaded on demand by the main SKILL when the conversation enters a structured phase.

**The SKILL decides whether to apply directly or offer first, based on confidence** (see `SKILL.md ## Picking a framework`). In short:

- **High confidence** (problem shape matches a canonical pattern, single framework obviously fits) → apply directly, announce in one sentence.
- **Medium confidence** (2-3 frameworks would fit) → offer them with one line each.
- **Low confidence** → stay Socratic.

**Don't apply the wrong framework for the domain.** If the case clearly doesn't fit, say so and suggest another, or go back to Socratic.

---

## Index

Tags to match against the problem shape before loading the full entry. They're internal to the skill's routing — not shown to the user.

| Framework | Tags | Good for |
|-----------|------|----------|
| 5 Whys | `root-cause`, `dissatisfaction`, `vague` | When the user knows something is wrong but not where it comes from |
| MECE | `split`, `chaos`, `categorize` | Splitting a problem into non-overlapping parts that cover everything |
| SWOT | `strategy`, `business`, `positioning` | Strategic analysis of a position, product, career |
| Pre-mortem | `planning`, `risk`, `high-confidence` | When the user has already decided and needs to stress-test before executing |
| SCAMPER | `ideation`, `creative`, `iterate` | Generating variations/alternatives of an existing idea |
| Eisenhower | `prioritize`, `overwhelmed`, `tasks` | When there's too much to do and nothing is obviously first |
| Decision Tree | `choice`, `branching`, `consequences` | Sequential choices with dependent outcomes |
| Weighted Pros/Cons | `compare`, `2-4-options` | Choosing between 2-4 discrete alternatives |
| JTBD | `product`, `customer`, `feature` | Understanding what the user *really* hires a product to do |
| First Principles | `stuck`, `assumption`, `reinvent` | When the current solution seems constrained by inherited premises |
| Inversion | `goal`, `planning`, `blind-spot` | Inverting: "how would I GUARANTEE failure?" reveals what to avoid |
| Wheel of Life | `personal`, `balance`, `overwhelmed` | Bird's-eye view of areas of personal life |

---

## 5 Whys

**When:** the user describes dissatisfaction, a bug, conflict, stuck decision — knows something is wrong but the why is vague.

**How:** ask "why?" 5 times on the previous answer. Stop earlier if the root cause becomes obvious or answers start repeating.

**Example flow:**
- User: "I'm unmotivated at work."
- → "Why do you think you're unmotivated?"
- User: "The projects seem irrelevant."
- → "Why do they seem irrelevant?"
- [continue until root]

**Produces:** a causal chain written in the live doc under `## Context` as a numbered list. The last answer becomes the candidate real problem.

**Watch out:** repeated "why?" sounds like interrogation. Vary: "what's behind that?", "where does that feeling come from?", "what's causing this?".

---

## MECE (Mutually Exclusive, Collectively Exhaustive)

**When:** the problem feels chaotic, has many dimensions, or the user is mixing things that should be handled separately.

**How:** ask the user to list the pieces. Then, together, regroup into categories that (a) don't overlap (mutually exclusive) and (b) cover everything (collectively exhaustive). Test each item: "does this fit in only one category?" "is there anything that doesn't fit anywhere?".

**Produces:** a hierarchical tree in the live doc, under `## Context` or a new section `## Decomposition`.

**Watch out:** perfect MECE is a myth. Aim for MECE-enough: the user can look at the tree and know where to attack.

---

## SWOT

**When:** strategic decision about a position, product, career, project. Useful when there's an external environment in play (market, competition, circumstances).

**How:** 4 questions, each pulls a list.
- **Strengths:** what's in your favor, today?
- **Weaknesses:** what's working against you, today?
- **Opportunities:** what's changing out there that could become an advantage?
- **Threats:** what's changing out there that could become a problem?

**Produces:** a 2×2 matrix in the live doc.

**Watch out:** SWOT turns into a dead checklist if the quadrants don't connect. Always force cross-quadrant questions: "which strength attacks which threat?", "which opportunity covers which weakness?".

---

## Pre-mortem

**When:** the user has already decided or is about to. Excellent for stress-testing. Also the central tool of adversarial mode.

**How:** ask the user to imagine it's 6-12 months in the future and the plan has failed badly. Now write the obituary: what went wrong? List 5-10 causes. Then: of those causes, which are avoidable? What can be done now?

**Produces:** a risk list in the live doc under `## Risks` or `## Pre-mortem`, each tagged `avoidable` / `mitigable` / `accepted`.

**Watch out:** don't let it become abstract pessimism. Force specificity — "fails exactly how?".

---

## SCAMPER

**When:** ideation. The user has a base idea and wants to generate variations.

**How:** apply each letter as a provocation:
- **S**ubstitute — swap a part for something else
- **C**ombine — merge with another idea
- **A**dapt — borrow from another context
- **M**odify/Magnify — enlarge, shrink, exaggerate
- **P**ut to other use — use it for something else
- **E**liminate — remove parts
- **R**everse/Rearrange — invert, reorder

**Produces:** a list of variations under `## Options considered`.

**Watch out:** 7 prompts is a lot. Pick the 3-4 that make the most sense for the idea, not all.

---

## Eisenhower Matrix

**When:** the user is overwhelmed, has too much on the table, and "everything seems important."

**How:** 2×2 of urgency × importance.
- Urgent + important → **do now**
- Important + not urgent → **schedule**
- Urgent + not important → **delegate or automate**
- Neither urgent nor important → **eliminate**

List every task/commitment and classify one by one. The matrix forces the differentiation between urgency (clock pressure) and importance (impact on what matters).

**Produces:** a 2×2 matrix with items, in the live doc.

**Watch out:** "important" without a reference is subjective. Anchor first: "important to which goal?".

---

## Decision Tree

**When:** sequential choices — decision A depends on B, which depends on C. Consequences branch.

**How:** map the first node (immediate decision). For each option, ask "if you pick this, what's the next decision?". Go 2-3 levels deep. At each leaf, note the expected consequence.

**Produces:** a tree in markdown (indented list) in the live doc.

**Watch out:** trees explode fast. Stop at 2-3 levels or at the first leaf that already answers the question.

---

## Weighted Pros/Cons

**When:** 2-4 discrete options, user stuck between them.

**How:** for each option, list pros and cons. Then — and this is the part most people skip — assign a weight (1-5) to each pro/con. Sum. Compare.

**Produces:** a table per option in the live doc. At the end, a score for each.

**Watch out:** the weight exposes what the user actually values. If the score "feels wrong" to the user, it's a sign the weights are off or there's a hidden criterion they didn't list. Ask.

---

## Jobs-to-be-Done (JTBD)

**When:** thinking about a product, feature, service, offering. The user wants to understand what people actually buy/use.

**How:** ask "when [situation], I want [action/motivation], so that [expected outcome]." Force specificity in each slot.

**Produces:** job statement(s) in the live doc under `## Jobs` or `## Context`.

**Watch out:** job ≠ feature. If the answer sounds like "when I open the app I want to click X", the abstraction is too low — why do they open the app?

---

## First Principles

**When:** the current solution seems constrained by inherited premises ("that's how it's always been done"). User wants to reinvent.

**How:** ask for the assumptions that support the current solution. For each one, ask: "is that an *immutable physical/mathematical/economic fact* or is that *convention/inertia*?". Drop the conventions. With what's left (the facts), rebuild.

**Produces:** two lists in the live doc — immutable assumptions vs. conventions — and a minimal reconstruction.

**Watch out:** not about being contrarian. A convention can be rational. Test with "if nobody had done it before, would you do it this way?".

---

## Inversion

**When:** clear goal but fuzzy path, or user keeps listing positives without seeing blind spots.

**How:** invert the question. "How would I GUARANTEE I fail at this?" List. The list becomes a script of things to avoid. Complements pre-mortem but faster.

**Produces:** a "traps to avoid" list in the live doc.

**Watch out:** works best when the user lists quickly and specifically. If it goes generic ("not study", "not put effort"), push: "concretely, what does 'not study' mean here?".

---

## Wheel of Life

**When:** personal brainstorm, overwhelm, sense that "something" is off but not sure what.

**How:** list 6-8 areas of life (career, health, relationships, family, finances, leisure, personal growth, purpose — adapt). For each, give a 0-10 rating for current satisfaction and 0-10 for what you *would like*. The biggest delta points to the area that needs the most attention.

**Produces:** an areas × current × desired × delta table in the live doc.

**Watch out:** don't let it become a self-criticism session. A low rating isn't a problem if the delta is zero (user doesn't want more there). Focus on the delta.
