# Agents

Specialized sub-agents with a focused system prompt, a minimal tool set, and a narrow scope. Agents are spawned by a parent session to handle a specific task autonomously — a reviewer, a designer, an auditor.

An agent differs from a skill: a **skill** teaches an AI *how* to do something; an **agent** *is* the AI doing that specific thing, with its own context and constraints.

## Artifact format

```markdown
---
name: agent-name
description: One sentence — when to spawn this agent.
version: "0.1.0"
tools: [Read, Grep]  # minimal — only what this agent needs
---

# Agent Name

## Role
## What This Agent Knows
## What This Agent Does Not Do   ← explicit out-of-scope
## Process
## Output Format
## Related Chapter(s)            ← optional
```

**Key principles:**
- Narrow scope — one thing done well
- Minimal tools — only what's needed
- Self-contained context — no assumed state from the parent session

## Contributing an agent

Read [CONTRIBUTING.md](../CONTRIBUTING.md) for the full process, quality bar, and PR checklist.

Use the `write-agent` skill (`.claude/skills/write-agent.md`) for the complete template and quality checklist.
