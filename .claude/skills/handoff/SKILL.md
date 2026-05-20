---
description: Compact the current conversation into a handoff document so a fresh agent can continue the work. Use when the conversation is approaching context limits or you want to hand off to a new session.
argument-hint: "What will the next session be used for?"
---

# /handoff - Conversation Handoff Document

Write a handoff document summarising the current conversation so a fresh agent can pick up the work.

## Where to save

**Always save inside the repo at `handoffs/YYYY-MM-DD-<slug>.md`.** Never write to `/tmp` or any OS tempdir — handoffs are part of the repo's history and must be committed.

The slug is a short kebab-case description of what the next session will work on (e.g. `auth-refactor`, `bug-investigation-payment`).

If multiple handoffs land on the same day, suffix with a number: `2026-05-20-auth-refactor-1.md`, `2026-05-20-auth-refactor-2.md`.

## Template

```markdown
# Handoff: <one-line summary>

**Date:** YYYY-MM-DD
**Next session focus:** <from the user's argument, or "general continuation">

## What we were doing

<2-4 sentences. What problem, what was attempted, where we landed.>

## State

- **Branch:** <git branch if relevant>
- **Open files / draft locations:** <list of paths being edited>
- **External references:** <issue links, PR URLs, ticket IDs — as clickable markdown links>

## Key findings

<Bullet list of anything substantive learned this session that isn't already captured in artifacts. Reference artifacts by path/URL — don't duplicate.>

## What's blocking / what's next

<What the next agent should do first. Be concrete.>

## Suggested skills

<List of `/skill-name` invocations the next agent should consider. Examples:
- `/standup` to re-orient on priorities
- `/grill-me` if the next step needs alignment
- `/write-a-skill` if a recurring need surfaced
>

## Redacted notes

<Anything sensitive that was in conversation but shouldn't land in the repo. Mark as `[REDACTED]` with a pointer to where the original lives.>
```

## Rules

- **Never duplicate** content already in plans, ADRs, issues, commits, diffs. Reference by path/URL.
- **Redact** API keys, passwords, tokens, customer PII, anything sensitive.
- **Always commit** the handoff file before ending the session. A handoff that's not committed isn't a handoff.
- If `git status` shows uncommitted work, list those files in **State** so the next agent doesn't lose them.

## Commit message

```
chore: handoff <YYYY-MM-DD> <slug>
```

---

*Adapted from [mattpocock/skills/productivity/handoff](https://github.com/mattpocock/skills/blob/main/skills/productivity/handoff/SKILL.md). See `memory/external-skill-sources.md` for full attribution.*
