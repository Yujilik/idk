# Live Document Templates

Pick one template per session, chosen by the detected domain. If you detected wrong, switch without drama — copy existing content to the equivalent sections and keep going.

**When the user writes in a language other than English** (common case, since `LANGUAGE=mirror` by default), **translate the section headers** to their language as you generate the doc. Structure is English here; the generated doc matches the user.

**General rules for all templates:**

- Substitute `[topic]` with the actual slug, `[YYYY-MM-DD]` with today's date.
- The top of the file always has metadata in a markdown blockquote.
- Sections marked *(tentative)* keep that marker until the user explicitly confirms.
- Never delete user content without asking.

---

# generic — fallback

Use when you can't detect a domain or the brainstorm is clearly hybrid.

```markdown
# Brainstorm: [topic]

> **Session:** [YYYY-MM-DD]
> **State:** active
> **Mode:** adaptive

## Problem

_What's being thought through here. Refine over the conversation — starts vague, gets precise._

## Context

_Facts, constraints, history the user shared. List, not prose._

- 

## Options considered

_Alternatives as they emerge. Each with pros/cons as they surface._

### Option 1: [name]

- Pros:
- Cons:

## Current decision

_(tentative)_ —

## Open questions

- 

## Next steps

- 
```

---

# technical-project

Use when the brainstorm is about code, architecture, feature, bug, migration, performance.

```markdown
# Technical brainstorm: [topic]

> **Session:** [YYYY-MM-DD]
> **State:** active
> **Mode:** adaptive

## Problem

_What needs to be solved. Be specific about expected vs. actual behavior._

## Context

- **Relevant stack:** 
- **Technical constraints:** 
- **External constraints (deadline, team, deps):** 

## Options considered

### Option 1: [approach]

- How it works:
- Pros:
- Cons:
- Estimated effort:
- Risks:

## Risks / Pre-mortem

_Filled in if pre-mortem runs or adversarial mode activates._

- 

## Current decision

_(tentative)_ —

## Open questions

- 

## Next steps

- [ ] 
```

---

# personal-decision

Use when the brainstorm is about career, relationship, life change, personal choice.

```markdown
# Personal brainstorm: [topic]

> **Session:** [YYYY-MM-DD]
> **State:** active
> **Mode:** adaptive

## Problem

_The decision or feeling that brought you here._

## Context

- **Current situation:** 
- **What changed recently:** 
- **Values at play:** _what actually matters to you in this choice_
- **Time horizon:** _urgent / medium / long / no deadline_
- **Stakeholders:** _who's affected besides you_

## Options considered

### Option 1: [path]

- What it looks like in practice:
- Pros:
- Cons:
- How you feel about it:

## Current decision

_(tentative)_ —

## Open questions

- 

## Next steps

- 
```

---

# writing

Use when the brainstorm is about structuring a piece of text, post, essay, script, long email.

```markdown
# Writing brainstorm: [topic]

> **Session:** [YYYY-MM-DD]
> **State:** active
> **Mode:** adaptive

## Thesis / core idea

_One sentence. If you don't have it yet, leave empty — it'll emerge._

## Target audience

_Who this is written for. What they already know, what needs explaining._

## What they should feel/think/do by the end

- 

## Arguments / main points

_Each will become a section/paragraph. Order matters._

1. 
2. 
3. 

## Evidence / examples / references

- 

## Outline

- 
  - 
    - 

## Open questions

- _Where the author doesn't yet know what to say_
- 

## Next steps

- [ ] 
```

---

# business

Use when the brainstorm is about product, feature, business strategy, positioning.

```markdown
# Business brainstorm: [topic]

> **Session:** [YYYY-MM-DD]
> **State:** active
> **Mode:** adaptive

## Problem

_What needs to be decided or solved._

## Jobs-to-be-Done

_When [situation], the customer wants [action/motivation], so that [outcome]._

- 

## Context

- **Customer / segment:** 
- **Metric that matters:** 
- **Competition / existing alternatives:** 
- **Constraints (resource, deadline, team):** 

## Options considered

### Option 1: [approach]

- Job it addresses:
- Pros:
- Cons:
- Estimated cost:
- Expected impact:

## SWOT (if run)

| | Internal | External |
|---|---|---|
| Positive | Strengths: | Opportunities: |
| Negative | Weaknesses: | Threats: |

## Current decision

_(tentative)_ —

## Open questions

- 

## Next steps

- [ ] 
```

---

## Switching template mid-session

If you detect the domain was wrong:

1. Warn: *"This looks more like [new domain] than [old]. I'm going to switch the template — existing content preserved."*
2. Read the current doc.
3. Map equivalent sections (`## Context` → `## Context`, `## Options` → `## Options`, etc.). Preserve any new content that doesn't have an equivalent, at the end of the file under `## Orphan notes`.
4. Rewrite with the new template + preserved content.
5. Continue the conversation.
