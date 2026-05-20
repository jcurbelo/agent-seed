---
title: External Skill Sources
description: Attribution and source links for skills imported or adapted from external repos
max_lines: 200
---

# External Skill Sources

Skills in `.claude/skills/` that were imported or adapted from third-party repositories. Keep this file current when porting new skills, removing ones, or when upstream sources change meaningfully.

## mattpocock/skills

- **Repo:** [github.com/mattpocock/skills](https://github.com/mattpocock/skills)
- **Author:** Matt Pocock ([@mattpocock](https://github.com/mattpocock))
- **License:** MIT
- **Imported:** 2026-05-20

### Skills imported

| Local skill | Upstream source | Notes |
|---|---|---|
| [handoff](../.claude/skills/handoff/SKILL.md) | [productivity/handoff](https://github.com/mattpocock/skills/blob/main/skills/productivity/handoff/SKILL.md) | **Modified:** writes to `handoffs/YYYY-MM-DD-<slug>.md` in-repo and requires commit. Upstream writes to OS tempdir. |
| [grill-me](../.claude/skills/grill-me/SKILL.md) | [productivity/grill-me](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) | Light edits — added agent-seed use cases and a recap-output section. |
| [caveman](../.claude/skills/caveman/SKILL.md) | [productivity/caveman](https://github.com/mattpocock/skills/blob/main/skills/productivity/caveman/SKILL.md) | **Modified:** added exception — never caveman drafted external messages (voice profile takes priority). Examples genericized. |
| [write-a-skill](../.claude/skills/write-a-skill/SKILL.md) | [productivity/write-a-skill](https://github.com/mattpocock/skills/blob/main/skills/productivity/write-a-skill/SKILL.md) | **Modified:** adapted to agent-seed conventions — model tiering, parallel dispatch, size limits, in-repo output paths, voice rules, README registration. |

### Skills evaluated, not imported

| Skill | Upstream | Reason skipped |
|---|---|---|
| diagnose | [engineering/diagnose](https://github.com/mattpocock/skills/blob/main/skills/engineering/diagnose/SKILL.md) | Excellent debugging discipline but coding-focused — better installed in a specific code repo than in this template. Users can pull it directly if needed. |
| zoom-out | [engineering/zoom-out](https://github.com/mattpocock/skills/blob/main/skills/engineering/zoom-out/SKILL.md) | One-line skill; works fine as a one-shot prompt. |
| grill-with-docs | [engineering/grill-with-docs](https://github.com/mattpocock/skills/blob/main/skills/engineering/grill-with-docs/SKILL.md) | Requires CONTEXT.md glossary + ADR convention. Doesn't match agent-seed's voice/work/memory structure. |
| tdd, to-prd, to-issues, triage, improve-codebase-architecture, prototype | [engineering/*](https://github.com/mattpocock/skills/tree/main/skills/engineering) | Product-engineering workflow skills. Wrong domain for a generic template — would force assumptions about issue trackers, PRD format, etc. |
| setup-matt-pocock-skills | [engineering/setup-matt-pocock-skills](https://github.com/mattpocock/skills/blob/main/skills/engineering/setup-matt-pocock-skills/SKILL.md) | Bootstrap for the engineering bundle — not needed since we're not adopting that bundle. agent-seed has its own `/setup`. |
| git-guardrails-claude-code | [misc/git-guardrails-claude-code](https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md) | Generic safety hook — could be added later as an opt-in. Out of scope for this port. |
| setup-pre-commit, migrate-to-shoehorn, scaffold-exercises | [misc/*](https://github.com/mattpocock/skills/tree/main/skills/misc) | Repo-specific tooling. Not applicable to a generic template. |

### Re-syncing with upstream

To check for upstream updates:

```bash
git clone https://github.com/mattpocock/skills /tmp/mp-skills
diff -r /tmp/mp-skills/skills/productivity .claude/skills
```

Then review changed `SKILL.md` files and decide whether to re-port. Don't blindly overwrite — local modifications (especially `handoff`'s in-repo storage and `write-a-skill`'s conventions) must be preserved.
