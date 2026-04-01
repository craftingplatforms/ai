# Crafting Platforms — AI Artifacts

> Part of the craftingplatforms workspace. Other projects: [`book/`](../book/CLAUDE.md), [`website/`](../website/CLAUDE.md), [`newsletter/`](../newsletter/CLAUDE.md)

Vendor-agnostic AI artifacts (skills, commands, agents, hooks, MCP servers) for platform engineering. Closely related to the book *Crafting Platforms* by Ezequiel Foncubierta, but the repository can grow beyond it — artifacts grounded in platform engineering or AI best practices are equally welcome.

**Key rules:**
- Artifacts must be practical and specific — no speculative or toy examples
- If an artifact relates to a book chapter, link to it — it makes the artifact more cohesive and discoverable
- Written vendor-agnostically — no platform-specific syntax in the artifact body
- Skills can produce any output: design documents, Terraform, scripts, pipelines, or a mix
- Skills can reference and delegate to external curated skills/tools rather than reinventing them
- Do not anticipate artifacts not explicitly requested — keep the repo clean

## Operations

Use the commands and skills in `.claude/` to maintain this repo:

| | |
|---|---|
| `/new-skill` | Scaffold a new skill, update README inventory, prompt book appendix update |
| `/new-agent` | Scaffold a new agent |
| `/new-command` | Scaffold a new command |
| `/sync-inventory` | Verify README inventory matches actual files; flag book cross-reference gaps |
| `artifact-reviewer` agent | Review any artifact for quality before publishing |
| `write-skill` skill | Template and checklist for writing a well-formed skill |
| `write-agent` skill | Template and checklist for writing a well-formed agent |
| `write-command` skill | Template and checklist for writing a well-formed command |
