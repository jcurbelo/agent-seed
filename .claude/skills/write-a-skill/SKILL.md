---
description: Create new skills for this agent-seed install with proper frontmatter, progressive disclosure, and conventions (size limits, index updates, voice integration). Use when the user wants to create, write, or build a new skill in `.claude/skills/`.
---

# /write-a-skill - Skill Authoring

Use this when the user has a recurring task that deserves its own slash command. Often invoked from `/learn` when a gap is detected.

## Process

1. **Gather requirements** — ask the user:
   - What task does the skill cover? What triggers it?
   - Single-step or multi-step (does it dispatch agents)?
   - Does it produce output? Where does the output land?
   - Does it need bundled scripts, or just instructions?
   - Reference materials to include?

2. **Draft the skill** — create:
   - `SKILL.md` with concise instructions (target under 150 lines, hard cap at 250 per repo policy)
   - Additional reference files if content exceeds limit (link from SKILL.md)
   - Utility scripts in `scripts/` if deterministic operations are needed

3. **Review with the user** — present the draft and ask:
   - Does this cover the use case?
   - Anything missing or unclear?
   - Should any section be more / less detailed?

4. **Wire it up:**
   - Add the new skill to the `## Skills` list in `README.md`
   - If a `.claude/skills/index.md` exists, add an entry there too
   - Validate with `scripts/check-markdown-policy.sh`

## Skill Structure

```
.claude/skills/skill-name/
├── SKILL.md           # Main instructions (required)
├── REFERENCE.md       # Detailed docs (only if SKILL.md > 150 lines)
├── EXAMPLES.md        # Usage examples (only if needed)
└── scripts/           # Utility scripts (only if deterministic ops needed)
    └── helper.sh
```

## SKILL.md Template

```md
---
description: Brief description of capability. Use when [specific user triggers — their own phrasing].
---

# /skill-name - Short Title

## Input

What the user provides when invoking.

## Step 1: [first action]

[Concrete instructions. If dispatching agents, launch independent ones in parallel.]

## Step 2: [next action]

...

## Output

What the skill produces (file path, draft, summary).
```

## Conventions (agent-seed)

These differ from generic skills — apply them:

- **Description** — must include "Use when [specific triggers]". This is the only thing the model sees when deciding to load the skill. Use the user's actual phrasing.
- **Model tiering** — if the skill dispatches agents, declare model in the agent definition (`haiku` for simple lookups, `sonnet` for analysis / coding, `opus` for orchestration / complex reasoning). See `CLAUDE.md` § Model Tiering.
- **Parallel dispatch** — when multiple agents are independent, launch them in a single message with multiple tool calls. Never sequentially.
- **Output location** — drafts and notes go inside the repo (`todos/YYYY-MM-DD/`, `handoffs/`, or a skill-specific dir). Never `/tmp`.
- **File size limits** — skills under 150 lines (link reference files if larger). Enforced by `scripts/check-markdown-policy.sh`.
- **Voice** — anything user-facing (drafted messages, PRs, emails) follows `context/voice/index.md` and `context/voice/patterns.md`. Skills should reference those files, not duplicate the voice rules.
- **Index pattern** — if the skill produces files in a new folder, follow the `index.md` + detail pages convention.

## When to Add Scripts

Add `scripts/` utilities when:

- Operation is deterministic (validation, formatting, URL building)
- Same code would otherwise be regenerated every invocation
- Errors need explicit handling

Scripts save tokens and improve reliability vs generated code.

## Description Writing

The description is **the only thing the model sees** when deciding which skill to load.

- Max 1024 chars
- Third person
- First sentence: what it does
- Second sentence: "Use when [specific triggers]"

**Good:**

> Compact the current conversation into a handoff document so a fresh agent can continue the work. Use when the conversation is approaching context limits or you want to hand off to a new session.

**Bad:**

> Helps with handoffs.

## Review Checklist

After drafting, verify:

- [ ] Description includes specific triggers ("Use when...")
- [ ] SKILL.md under 150 lines (link reference files if larger)
- [ ] No time-sensitive info (dates, "currently", "as of...")
- [ ] Consistent terminology with the rest of the repo
- [ ] Concrete examples included
- [ ] References to `context/`, `memory/`, and `.claude/rules/` where relevant — don't duplicate
- [ ] Output paths are inside the repo (never `/tmp`)
- [ ] README.md `## Skills` list updated
- [ ] `scripts/check-markdown-policy.sh` passes

---

*Adapted from [mattpocock/skills/productivity/write-a-skill](https://github.com/mattpocock/skills/blob/main/skills/productivity/write-a-skill/SKILL.md). See `memory/external-skill-sources.md`.*
