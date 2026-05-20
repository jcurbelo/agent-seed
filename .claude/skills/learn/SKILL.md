---
description: Self-improvement routine. Review memory, prune stale entries, identify gaps, evolve agents. Run weekly or after significant sessions.
---

# /learn - Self-Improvement

## Step 1: Read Everything (in parallel)

1. All memory files: `memory/`
2. All context files: `context/`
3. All agent definitions: `.claude/agents/`
4. All scoped rules: `.claude/rules/`
5. All skills: `.claude/skills/`

## Step 2: Check Improvements Backlog

Read `memory/improvements.md`. Act on anything pending:
- Missing agents -> create them
- Incorrect context -> fix it
- Stale rules -> update them

## Step 3: Cross-Reference

- Do agent definitions match what the user actually asks for?
- Are there gaps? (recurring requests with no matching agent)
- Are rules covering the right paths?
- Are skills working correctly?
- Is the voice profile accurate?

## Step 4: Prune Memory

- Remove stale entries (30+ days, never referenced)
- Merge duplicate entries
- Keep files under their `max_lines` limit
- Verify every page is linked from its parent index

## Step 5: Apply Updates

Make any warranted changes to:
- Agent definitions (new agents, updated routing)
- Context files (voice, work)
- Rules (new scopes, updated constraints)
- Skills (improved workflows)
- `CLAUDE.md` (if rules need updating)

When the gap calls for a brand-new skill (recurring user request with no matching slash command), invoke `/write-a-skill` to scaffold it with the right frontmatter, size limits, and README registration — don't hand-roll the SKILL.md.

## Step 6: Commit

1. Create branch: `feat/learn-YYYY-MM-DD`
2. Stage all changes
3. Commit with a clear message describing what was improved
4. Push and create PR (if `gh` is available)

Report: what you updated, what you pruned, what gaps remain.
