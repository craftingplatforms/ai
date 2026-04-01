---
name: write-command
description: Write a new command for the craftingplatforms/ai repository. Use this when asked to create a slash command for a repeatable platform engineering workflow.
---

# Writing a Crafting Platforms Command

## Context

You are working in the `craftingplatforms/ai` repository. Commands are named workflows invoked explicitly by the user (e.g., `/new-skill`, `/sync-inventory`). They are **orchestrators** — their job is to sequence steps, call other skills or tools, and guide the user through a workflow. They are not knowledge repositories.

A command differs from a skill: a **skill** contains deep domain knowledge for accomplishing a task; a **command** sequences that knowledge into a concrete workflow with a clear start and end.

## Design Principles

- **Short** — commands are workflows, not essays. If you're writing more than ~30 lines, extract the knowledge into a skill and call it from the command.
- **Action-oriented** — every step should be an instruction, not an explanation
- **Idempotent where possible** — running a command twice should be safe
- **User-facing** — commands may ask the user questions or present output; skills typically don't

## File Location and Name

`commands/<kebab-case-name>.md`

The filename becomes the slash command: `new-skill.md` → `/new-skill`.

## Template

```markdown
<One sentence: what this command does when invoked.>

## Steps

1. **<Step name>** — <what to do>
2. **<Step name>** — <what to do>
   ...

## Notes

<Optional: edge cases, warnings, or links to related skills the user might invoke next.>
```

Commands have no frontmatter. They are plain Markdown starting with the purpose sentence.

## What Belongs in a Command vs. a Skill

| Put it in a **command** | Put it in a **skill** |
|------------------------|----------------------|
| Step-by-step workflow | Deep domain knowledge |
| "Ask the user for X" | Templates and formats |
| "Run `/sync-inventory` after" | Quality checklists |
| Decision branches | Principles and reasoning |

If you find yourself writing principles, templates, or detailed checklists in a command — stop and create a skill instead.

## Quality Checklist

- [ ] Starts with a single purpose sentence (no frontmatter)
- [ ] Each step is an instruction, not an explanation
- [ ] Calls skills by name where knowledge is needed (e.g., "use the `write-skill` skill")
- [ ] No vendor-specific syntax
- [ ] Short — under 40 lines is a good target
- [ ] File is in `commands/` and named in kebab-case

## After Writing the Command

Run `/sync-inventory` to update the README.md inventory.
