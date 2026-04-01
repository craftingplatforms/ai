---
name: write-agent
description: Write a new vendor-agnostic agent for the craftingplatforms/ai repository. Use this when asked to create a specialized sub-agent for a platform engineering task tied to a book chapter.
---

# Writing a Crafting Platforms Agent

## Context

You are working in the `craftingplatforms/ai` repository. Agents are specialized sub-agents with a focused system prompt, a minimal tool set, and a narrow scope. They are spawned by a parent session to handle a specific task autonomously.

An agent differs from a skill: a **skill** teaches an AI *how* to do something; an **agent** *is* the AI doing that specific thing, with its own context and constraints.

## Design Principles

- **Narrow scope** — an agent should do one thing well. If it needs to do two things, consider two agents.
- **Minimal tools** — only grant the tools the agent actually needs. Less is more.
- **Self-contained context** — the agent's system prompt must include everything it needs to operate. It cannot rely on the parent session's context.
- **Grounded in book content** — every agent must anchor to at least one book chapter.

## File Location and Name

`agents/<kebab-case-name>.md`

Name the file after the agent's role: `infra-reviewer.md`, `slo-designer.md`, `security-auditor.md`.

## Template

```markdown
---
name: <kebab-case-name>
description: <One sentence — when to spawn this agent. Used for routing decisions.>
version: "0.1.0"
tools: [Read, Grep]  # minimal — only what this agent needs
---

# <Agent Name>

## Role

<One paragraph: who is this agent, what is its singular focus, what does it produce.>

## What This Agent Knows

<Key domain knowledge the agent needs. This is the agent's "memory" — include
principles from the book chapter, relevant constraints, and platform context.>

## What This Agent Does Not Do

<Explicit out-of-scope items. Narrow the agent's focus by stating what it refuses
to do, so the parent session knows when to spawn a different agent.>

## Process

<Step-by-step. Write for the agent — it will follow these instructions directly.>

## Output Format

<What the agent produces. Be specific.>

## Related Chapter(s)

This agent is grounded in **Chapter N: <Chapter Name>** of *Crafting Platforms* by Ezequiel Foncubierta.

- Read the book: [leanpub.com/crafting-platforms](https://leanpub.com/crafting-platforms)
- Project home: [craftingplatforms.com](https://www.craftingplatforms.com)
```

## Tools Reference

Only include tools the agent genuinely needs:

| Tool | Use when |
|------|---------|
| `Read` | Agent needs to read files |
| `Grep` | Agent needs to search file contents |
| `Glob` | Agent needs to find files by pattern |
| `Bash` | Agent needs to run shell commands |
| `WebSearch` | Agent needs to look up external information |
| `WebFetch` | Agent needs to read a specific URL |

Omit all others. A reviewer agent doesn't need `Bash`. A scaffolding agent doesn't need `WebSearch`.

## Quality Checklist

- [ ] `name` is in kebab-case and reflects the agent's role
- [ ] `description` clearly states when to spawn this agent (not what it does internally)
- [ ] `version` is set to `0.1.0`
- [ ] `tools` list is minimal — no unnecessary tools
- [ ] "What This Agent Does Not Do" section is present and specific
- [ ] System prompt is fully self-contained — no assumed context from parent session
- [ ] No vendor-specific tool mechanics in the body ("use the Skill tool", "in Claude Code")
- [ ] "Related Chapter(s)" links to the Leanpub page
- [ ] File is in `agents/` and named in kebab-case

## After Writing the Agent

Run `/sync-inventory` to update the README.md inventory.
