# Crafting Platforms — AI Artifacts

> Part of the craftingplatforms workspace. Other projects: [`brand/`](../brand/README.md), [`book/`](../book/CLAUDE.md), [`website/`](../website/CLAUDE.md), [`newsletter/`](../newsletter/CLAUDE.md)

## Brand & Style Reference

All visual and verbal identity lives in [`../brand/`](../brand/README.md):

| Resource | Path | Covers |
|----------|------|--------|
| **Palette & Typography** | [`../brand/palette.md`](../brand/palette.md) | Colors, fonts, semantic tokens |
| **Voice & Tone** | [`../brand/voice.md`](../brand/voice.md) | Story characters, forbidden phrases, sentence rhythm — use when generating chapter content |

AI artifacts in this repo produce written and technical content. When writing prose (skills,
agents that generate copy), follow the voice guide. Visual output (diagrams, reports) should
use the brand palette.

---

Vendor-agnostic AI artifacts (skills, commands, agents, hooks, MCP servers) for platform engineering. Distributed as a [Claude Code Plugin Marketplace](https://code.claude.com/docs/en/plugin-marketplaces). Closely related to the book *Crafting Platforms* by Ezequiel Foncubierta, but the repository can grow beyond it — artifacts grounded in platform engineering or AI best practices are equally welcome.

**Structure:** Skills live under `plugins/<plugin>/skills/<name>/SKILL.md`. Each plugin has a `.claude-plugin/plugin.json` manifest. The marketplace catalog is at `.claude-plugin/marketplace.json`. Shared notation and types in `references/` are symlinked into each plugin as `plugins/<plugin>/references`.

**Key rules:**
- Artifacts must be practical and specific — no speculative or toy examples
- If an artifact relates to a book chapter, link to it — it makes the artifact more cohesive and discoverable
- Written AI vendor-agnostically — no platform-specific syntax in the artifact body
- Skills can produce any output: design documents, Terraform, scripts, pipelines, or a mix
- Skills can reference and delegate to external curated skills/tools rather than reinventing them
- Do not anticipate artifacts not explicitly requested — keep the repo clean

## Operations

Use the commands and skills in `.claude/` to maintain this repo:

| | |
|---|---|
| `/new-plugin` | Scaffold a new plugin, create plugin.json and references symlink, update marketplace.json and README |
| `/new-skill` | Scaffold a new skill inside an existing plugin, update README inventory |
| `/new-agent` | Scaffold a new agent |
| `/new-command` | Scaffold a new command |
| `/sync-inventory` | Verify README inventory matches actual files; flag book cross-reference gaps |
| `artifact-reviewer` agent | Review any artifact (skill, plugin.json, command, agent) for quality before publishing |
| `write-plugin` skill | Template and checklist for writing a well-formed plugin manifest |
| `validate-plugin` skill | Validate a plugin's structure and manifest against the spec |
| `write-skill` skill | Template and checklist for writing a well-formed skill |
| `write-agent` skill | Template and checklist for writing a well-formed agent |
| `write-command` skill | Template and checklist for writing a well-formed command |
