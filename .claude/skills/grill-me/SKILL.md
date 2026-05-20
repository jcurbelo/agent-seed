---
description: Interview the user relentlessly about a plan or design until reaching shared understanding, resolving each branch of the decision tree. Use when the user wants to stress-test a plan, says "grill me", or before any multi-step task where the path is ambiguous.
---

# /grill-me - Relentless Plan Interview

Interview the user relentlessly about every aspect of this plan until you reach shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

## Rules

- **Ask one question at a time.** Wait for the user's answer before continuing.
- **If a question can be answered by exploring** (reading a file, an issue, a PR, prior context), explore instead of asking.
- **Always provide a recommended answer** with each question so the user can confirm or redirect quickly.
- **Stop when the design tree is resolved**, not when the user gets tired. If a branch is still ambiguous, say so and recommend deferring.

## When this is most useful

- Before a multi-file refactor — confirm the shape and the seam before coding
- Before drafting any external message (email, PR description, RFC) where alignment matters
- Before invoking a heavyweight skill (`/handoff`, `/eod`) so the output captures the right decisions
- When the user says "I want to do X" and the path has more than one reasonable approach

## Output

After grilling concludes, write a brief recap so the decisions don't evaporate:

```markdown
## Decisions

1. <decision> — <rationale>
2. ...

## Open questions

- <anything still unresolved>

## Next step

<Concrete action — typically the actual work, or invoking another skill.>
```

---

*Adapted from [mattpocock/skills/productivity/grill-me](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md). See `memory/external-skill-sources.md`.*
