---
name: write-skill
description: Write a new vendor-agnostic skill for the craftingplatforms/ai repository. Use this when asked to create a skill for a platform engineering or AI task.
---

# Writing a Crafting Platforms Skill

## Context

You are working in the `craftingplatforms/ai` repository — a companion to the book *Crafting Platforms* by Ezequiel Foncubierta. Skills here are reusable, vendor-agnostic instructions that teach AI agents how to accomplish platform engineering tasks.

Skills may be grounded in the *Crafting Platforms* book, in platform engineering best practices, or in AI agent patterns. If a skill relates to a book chapter, linking to it makes the skill more cohesive — but it is not required.

## Skill Types

Choose the type before writing — it shapes the template:

| Type | What it produces | Examples |
|------|-----------------|---------|
| **Design** | Decisions, strategies, architecture documents | Segmentation strategy, SLO definition |
| **Implementation** | Working code — Terraform, scripts, manifests, pipelines | VPC scaffold, CI/CD pipeline, IAM baseline |
| **Hybrid** | Design decisions + implementation, interleaved | "Design and scaffold the networking layer" |
| **Orchestration** | Calls other skills in sequence; produces a workflow | "Stand up a full platform environment" |

A skill can also **reference external skills** from curated repositories when a well-maintained external skill does the job better than writing a new one (e.g., a community Terraform AWS skill). In that case, the skill's job is to guide *which* external skill to use, with what parameters, and *why* — aligned with the book's principles.

## File Location and Name

`skills/<kebab-case-name>.md`

Name the file after the action: `design-segmentation.md`, `scaffold-vpc.md`, `audit-iam.md`.

## Template

```markdown
---
name: <kebab-case-name>
description: <One sentence — when to invoke this skill. This is used for matching by AI platforms.>
version: "0.1.0"
---

# <Title>

## Your Goal

<What the AI should accomplish — one paragraph, outcome-focused.>

## Skill Type

<Design | Implementation | Hybrid | Orchestration>

<If Orchestration: list the skills this skill calls and in what order.>
<If this skill references external skills: list them with URLs and explain when to use each.>

## What to Gather First

Before proceeding, ask the user (or infer from context):

- <Question 1>
- <Question 2>
- ...

## Process

<Step-by-step approach. Be explicit — write for an AI, not a human.>

<For Implementation skills: include concrete code, templates, or scripts.
 For Design skills: include the decision framework and expected outputs.
 For Hybrid: interleave design steps with implementation outputs.
 For Orchestration: sequence the sub-skills with handoff context between them.>

## Output Format

<What deliverables to produce. Be specific about format, structure, file names.>

## Principles to Apply

<Draw from the book chapter if applicable, or from platform engineering/AI best practices.
These are the "why" behind the implementation choices.>

- <Principle 1>
- <Principle 2>
- ...

## External Skills and Tools

<Optional. If this skill delegates to or recommends external skills, list them here:>

- **[skill-name](url)** — what it does, when to use it, any parameter guidance
- **[tool/repo](url)** — e.g., a curated Terraform module registry, a community agent library

## Related Chapter(s) *(optional)*

*(Include this section if the skill relates to one or more chapters in the book.
Omit it if the skill is grounded in general platform engineering or AI best practices.)*

This skill is grounded in **Chapter N: <Chapter Name>** of *Crafting Platforms* by Ezequiel Foncubierta.

- Read the book: [leanpub.com/crafting-platforms](https://leanpub.com/crafting-platforms)
- Project home: [craftingplatforms.com](https://www.craftingplatforms.com)
```

## Quality Checklist

Before saving the file, verify:

- [ ] `name` is in kebab-case
- [ ] `description` is one sentence and captures when to use this skill
- [ ] `version` is set to `0.1.0`
- [ ] Skill type is declared and the template reflects it
- [ ] "What to Gather First" lists real questions — not generic placeholders
- [ ] Process is explicit enough for an AI with no prior context to follow
- [ ] Implementation skills include actual code, templates, or scripts — not just guidance
- [ ] Orchestration skills list sub-skills with handoff context
- [ ] External skills/tools are credited with URLs and usage guidance
- [ ] No vendor-specific tool assumptions in the body (no "use the Skill tool", no "in Claude Code...")
- [ ] If the skill relates to a book chapter: "Related Chapter(s)" section is present and links to Leanpub
- [ ] File is in `skills/` and named in kebab-case

## After Writing the Skill

Run `/sync-inventory` to ensure the README.md inventory is updated and the book's appendix cross-reference is flagged for update.
