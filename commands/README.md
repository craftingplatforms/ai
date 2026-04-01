# Commands

Named workflows invoked via slash command (e.g., `/platform-review`, `/scaffold-infra`). Commands are **orchestrators** — they sequence steps, call skills, and guide the user through a workflow. They are not knowledge repositories.

A command differs from a skill: a **skill** contains deep domain knowledge; a **command** sequences that knowledge into a concrete, repeatable workflow.

## Artifact format

Commands are plain Markdown files — no frontmatter. The filename becomes the command name.

```markdown
One sentence describing what this command does.

## Steps

1. **Step name** — what to do
2. **Step name** — what to do
   ...

## Notes   ← optional
```

**Key principles:**
- Short — if you're writing principles or templates, extract them into a skill instead
- Action-oriented — every step is an instruction, not an explanation
- Calls skills by name for the knowledge-heavy parts

## Contributing a command

Read [CONTRIBUTING.md](../CONTRIBUTING.md) for the full process, quality bar, and PR checklist.

Use the `write-command` skill (`.claude/skills/write-command.md`) for the complete template and quality checklist.
