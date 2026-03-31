# Crafting Platforms — AI Artifacts (Development)

> Part of the craftingplatforms workspace. Other projects: [`book/`](../book/CLAUDE.md), [`website/`](../website/CLAUDE.md), [`newsletter/`](../newsletter/CLAUDE.md)

## Overview

This repository houses reusable AI artifacts (skills, commands, agents, hooks, MCP servers) that implement concepts from each chapter of *Crafting Platforms*. Artifacts are written **vendor-agnostically** and deployed to Claude Code, GitHub Copilot, Cursor, or other AI platforms via thin adapters in `vendors/`.

**For getting started, setup instructions, and examples, see [README.md](README.md).**

## Development Guidelines

### When to Create a New Artifact

- A new chapter has been published and needs corresponding AI guidance
- You're generalizing a workflow that multiple users would benefit from
- The artifact is reusable across contexts (not one-off automation for a single org)

### Artifact Types and Locations

| Type | Location | When to use |
|------|----------|------------|
| **Skill** | `skills/*.md` | Standalone task guidance (e.g., "design a segmentation strategy") |
| **Command** | `commands/*.md` | Repeatable named workflow (e.g., `/platform-review`) |
| **Agent** | `agents/*.md` | Specialized sub-agent with narrow focus and tool set |
| **Hook** | `hooks/*.sh` | Event-driven automation (pre/post tool, on-stop) |
| **MCP Server** | `mcp/server-name/` | Domain-specific tools (query Terraform, read observability data) |

### Writing Skills (Most Common)

**Location:** `skills/skill-name.md`

**Template:**

```markdown
---
name: skill-name
description: One sentence — when to invoke this skill.
---

# Skill Title

## Your Goal

[What the AI should accomplish]

## What to Gather First

[Questions to ask the user or context to infer — make this detailed]

## Process

[Step-by-step approach]

## Output Format

[Expected deliverables and structure]

## Related Chapter

This skill corresponds to **Chapter N: Chapter Name** of *Crafting Platforms*.
See [craftingplatforms.com](https://www.craftingplatforms.com) for the full chapter.
```

**Principles:**

- Write for an AI, not a human. Be explicit.
- Self-contained — the skill should work standalone without reading the book chapter.
- Link to the chapter for deeper context and reasoning.
- No platform-specific code (Terraform, Kubernetes, etc.) — the skill teaches *approach*, not implementation details.
- Test with multiple users — does the skill produce useful output?

### Writing Commands

Commands are shorter than skills and focused on a repeatable action.

**Location:** `commands/command-name.md`

**Template:** Same as skills, but context and process are typically shorter.

### Writing Agents

Agents have a `tools` field in frontmatter specifying what they can do.

**Location:** `agents/agent-name.md`

**Template:**

```markdown
---
name: agent-name
description: When to spawn this agent.
tools: [Read, Grep, Bash]
---

[System prompt — full context and instructions]
```

### Keeping Things Vendor-Agnostic

- Don't assume a specific tool is available (e.g., "use the Skill tool" assumes Claude Code)
- Speak generically ("you have access to files and can run commands")
- If a vendor feature is essential, document it in `vendors/platform/README.md` instead

### Vendor Adapters

The `vendors/` directory contains platform-specific docs and consolidated files:

- `vendors/claude-code/README.md` — deployment instructions (no code changes needed)
- `vendors/cursor/platform-engineer.mdc` — consolidated Cursor rule (consolidated, not duplicated from skills)
- `vendors/github-copilot/platform-engineer.md` — consolidated Copilot instructions

**Do not duplicate artifact content across vendors.** If a skill needs vendor-specific notes, add them to the vendor's README, not to the skill itself.

### Updating the Artifact Inventory

When you add a new artifact:

1. Update the table in [README.md](README.md) — add the skill name, chapter, and status
2. Reference the book chapter in the artifact's "Related Chapter" section
3. Keep the inventory table in sync as artifacts move from planned → in-progress → published

### What Claude Should Do

- Write complete, actionable artifacts — not outlines or skeletons
- Include enough detail that the artifact works for users unfamiliar with the book
- Always link to the corresponding chapter
- Test artifacts before committing (run them through an AI to see if they're clear)
- Keep the artifact inventory table up to date

### What Claude Should NOT Do

- Do not anticipate agents, commands, etc. that aren't explicitly requested — keep the repo clean
- Do not duplicate content across vendor directories
- Do not put application code here — this repo is about AI guidance, not implementation
- Do not commit skills without a corresponding book chapter (or at least a planned chapter)
- Do not assume a specific vendor's tool availability in the artifact body
