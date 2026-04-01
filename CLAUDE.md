# Crafting Platforms — AI Artifacts

> Part of the craftingplatforms workspace. Other projects: [`book/`](../book/CLAUDE.md), [`website/`](../website/CLAUDE.md), [`newsletter/`](../newsletter/CLAUDE.md)

Vendor-agnostic AI artifacts (skills, commands, agents, hooks, MCP servers) that implement concepts from each chapter of *Crafting Platforms* by Ezequiel Foncubierta. Artifacts live in capability directories (`skills/`, `commands/`, etc.); `vendors/` holds thin deployment adapters for Claude Code, Cursor, and GitHub Copilot.

**Key rules:**
- One artifact per task, written vendor-agnostically
- Every artifact maps to a book chapter — no chapter, no artifact
- No Terraform/Kubernetes/application code here — skills teach *approach*, not implementation
- Do not anticipate artifacts not explicitly requested — keep the repo clean

## Operations

Use the commands and skills in `.claude/` to maintain this repo:

| | |
|---|---|
| `/new-skill` | Scaffold a new skill, update README inventory, prompt book appendix update |
| `/sync-inventory` | Verify README inventory matches actual files; flag book cross-reference gaps |
| `artifact-reviewer` agent | Review any artifact for quality before publishing |
| `write-skill` skill | Guidance and template for writing a well-formed skill |
