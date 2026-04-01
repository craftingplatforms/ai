---
name: write-skill
description: Write a new vendor-agnostic skill for the craftingplatforms/ai repository. Use this when asked to create a skill for a platform engineering task tied to a book chapter.
---

# Writing a Crafting Platforms Skill

## Context

You are working in the `craftingplatforms/ai` repository — a companion to the book *Crafting Platforms* by Ezequiel Foncubierta. Skills here are reusable, vendor-agnostic instructions that teach AI agents how to accomplish platform engineering tasks. Each skill maps to a book chapter.

## File Location and Name

`skills/<kebab-case-name>.md`

Name the file after the action: `design-segmentation.md`, `scaffold-infra.md`, `audit-security.md`.

## Template

```markdown
---
name: <kebab-case-name>
description: <One sentence — when to invoke this skill. This is used for matching by AI platforms.>
---

# <Title>

## Your Goal

<What the AI should accomplish — one paragraph, outcome-focused.>

## What to Gather First

Before proceeding, ask the user (or infer from context):

- <Question 1>
- <Question 2>
- ...

## Process

<Step-by-step approach. Be explicit — write for an AI, not a human. Each step should be actionable.>

## Output Format

<What deliverables to produce. Include structure, format, and any required sections.>

## Principles to Apply

- <Principle 1 from the book chapter>
- <Principle 2>
- ...

## Related Chapter

This skill corresponds to **Chapter N: <Chapter Name>** of *Crafting Platforms* by Ezequiel Foncubierta.

- Read the chapter: [leanpub.com/crafting-platforms](https://leanpub.com/crafting-platforms)
- Project home: [craftingplatforms.com](https://www.craftingplatforms.com)
```

## Quality Checklist

Before saving the file, verify:

- [ ] The `description` field is one sentence and captures when to use this skill
- [ ] "What to Gather First" lists real questions — not generic placeholders
- [ ] The process is explicit enough for an AI with no prior context to follow
- [ ] No Terraform/Kubernetes/application code — skills teach *approach*, not implementation
- [ ] No vendor-specific tool assumptions in the body (no "use the Skill tool", no "in Claude Code...")
- [ ] "Related Chapter" section links to the Leanpub page
- [ ] File is in `skills/` and named in kebab-case

## After Writing the Skill

Run `/sync-inventory` to ensure the README.md inventory is updated and the book's appendix cross-reference is flagged for update.
