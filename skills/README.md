# Skills

Self-contained, vendor-agnostic instructions for accomplishing platform engineering tasks. Each skill teaches an AI agent how to approach a specific problem: designing segmentation strategies, scaffolding infrastructure, auditing security, and more.

Skills may be grounded in the *Crafting Platforms* book, in platform engineering best practices, or in AI agent patterns. Where a skill relates to a book chapter, it links to it.

## Artifact format

```markdown
---
name: skill-name
description: One sentence — when to invoke this skill.
version: "0.1.0"
---

# Skill Title

## Your Goal
## Skill Type        ← Design | Implementation | Hybrid | Orchestration
## What to Gather First
## Process
## Output Format
## Principles to Apply
## External Skills and Tools   ← optional
## Related Chapter(s)          ← optional
```

**Skill types:**

| Type | Produces |
|------|---------|
| Design | Decision frameworks, architecture documents |
| Implementation | Working code — Terraform, scripts, pipelines |
| Hybrid | Design decisions interleaved with implementation |
| Orchestration | Sequences of other skills, with handoff context |

## Contributing a skill

Read [CONTRIBUTING.md](../CONTRIBUTING.md) for the full process, quality bar, and PR checklist.

Use the `write-skill` skill (`.claude/skills/write-skill.md`) for the complete template and quality checklist.
