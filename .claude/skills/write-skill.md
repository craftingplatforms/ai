---
name: write-skill
description: Write a new vendor-agnostic skill for the craftingplatforms/ai repository. Use this when asked to create a skill for a platform engineering or AI task.
---

# Writing a Crafting Platforms Skill

## Context

You are working in the `craftingplatforms/ai` repository. Skills follow the [Agent Skills](https://agentskills.io) open format — a directory containing a `SKILL.md` file plus optional scripts, references, and assets. This format is supported by Claude Code, Cursor, GitHub Copilot, Gemini CLI, and others.

Skills may be grounded in the *Crafting Platforms* book, in platform engineering best practices, or in AI agent patterns. If a skill relates to a book chapter, linking to it makes the skill more cohesive — but it is not required.

## Skill Types

Declare the type before writing — it determines what the skill produces:

| Type | Produces |
|------|---------|
| **Design** | Decision frameworks, architecture documents |
| **Implementation** | Working code — Terraform, scripts, pipelines |
| **Hybrid** | Design decisions interleaved with implementation |
| **Orchestration** | Sequences of other skills, with handoff context |

## Directory Structure

```
skills/
└── skill-name/
    ├── SKILL.md        # Required: metadata + instructions (keep under 500 lines)
    ├── scripts/        # Optional: executable scripts
    ├── references/     # Optional: detailed docs loaded on demand
    └── assets/         # Optional: templates, schemas, data files
```

The directory name must exactly match the `name` field in `SKILL.md`.

## SKILL.md Template

```markdown
---
name: <kebab-case-name>
description: <What this skill does and when to use it. Include domain keywords. Max 1024 chars.>
license: Apache-2.0
compatibility: <System requirements, if any. E.g. "Requires Terraform CLI and AWS credentials.">
metadata:
  version: "0.1.0"
  chapter: "<N>"     # optional — book chapter reference
allowed-tools: <space-delimited tools, if pre-approval needed. E.g. "Bash(terraform:*) Read">
---

# <Skill Title>

## Skill Type

<Design | Implementation | Hybrid | Orchestration>

## Your Goal

<What the agent should accomplish — one paragraph, outcome-focused.>

## What to Gather First

Before proceeding, ask the user (or infer from context):

- <Question 1>
- <Question 2>
- ...

## Process

<Step-by-step instructions. Write for an AI. Each step should be directly actionable.>
<For Implementation: include actual code, templates, or references to scripts/.>
<For Orchestration: list sub-skills in sequence with handoff context between them.>

## Output Format

<What to produce. Specify structure, format, and file names where relevant.>

## Principles to Apply

<Draw from the book chapter if applicable, or from platform engineering / AI best practices.>

- <Principle 1>
- <Principle 2>
- ...

## External Skills and Tools *(optional)*

<If this skill delegates to external skills or tools, list them with URLs and usage notes.>

## Related Chapter(s) *(optional)*

*(Include if the skill maps to the book. Omit otherwise.)*

This skill is grounded in **Chapter N: <Chapter Name>** of *Crafting Platforms*.

- Read the book: [leanpub.com/crafting-platforms](https://leanpub.com/crafting-platforms)
- Project home: [craftingplatforms.com](https://www.craftingplatforms.com)
```

## scripts/

For Implementation and Hybrid skills, ship working scripts — not just instructions about what to run.

Place scripts in `scripts/` and reference them from `SKILL.md`:

```markdown
Run the scaffolding script:
scripts/scaffold.sh
```

Each script should:
- Be self-contained or clearly declare dependencies at the top
- Handle errors with helpful messages
- Work standalone, not just as a companion to the instructions

## references/

Move detailed content that isn't needed on every activation to `references/`. Agents load these files only when they read them — this keeps the main `SKILL.md` focused and saves context.

Good candidates: cloud-specific variants, extended examples, troubleshooting guides.

```
references/
├── aws.md
├── azure.md
└── REFERENCE.md     # catch-all detailed reference
```

## assets/

Static files the skill uses: Terraform templates, YAML schemas, configuration examples, data lookup tables.

## Quality Checklist

Before saving, verify:

- [ ] Directory name matches `name` field exactly
- [ ] `name` is lowercase, hyphens only, max 64 chars
- [ ] `description` describes what the skill does *and* when to use it — specific keywords, not vague
- [ ] `metadata.version` is set to `0.1.0`
- [ ] `compatibility` is set if the skill has system requirements
- [ ] Skill type is declared
- [ ] `SKILL.md` body is under 500 lines — move detail to `references/`
- [ ] Implementation skills have working scripts in `scripts/`, not just prose
- [ ] Orchestration skills list sub-skills with handoff context
- [ ] External skills/tools credited with URLs
- [ ] No vendor-specific AI tool syntax in the body ("use the Skill tool", "in Claude Code")
- [ ] If the skill relates to a book chapter: `metadata.chapter` is set and "Related Chapter(s)" section links to Leanpub

## After Writing the Skill

Run `/sync-inventory` to update the README.md inventory and flag any book appendix gaps.
