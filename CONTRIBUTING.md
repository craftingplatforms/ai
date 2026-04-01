# Contributing to Crafting Platforms AI Artifacts

Thank you for contributing! Every artifact here helps platform engineers move faster and build better internal platforms. This guide explains how to add new artifacts and what quality looks like.

## What We Accept

Practical, vendor-agnostic artifacts for platform engineering and AI:

- **Skills** — reusable AI instructions for platform engineering tasks (design, implementation, hybrid, orchestration)
- **Commands** — named workflows invoked via slash command
- **Agents** — specialized sub-agents with narrow scope and tool sets
- **Hooks** — event-driven automation scripts
- **MCP servers** — domain-specific tool extensions

Artifacts may be grounded in the *Crafting Platforms* book, in platform engineering best practices, or in AI agent patterns. What we don't accept: speculative ideas without a concrete use case, or duplicates of existing artifacts without clear improvement.

If your artifact relates to a book chapter, link to it — it makes the artifact more cohesive and discoverable for readers.

## Before You Start

1. **Check open issues and PRs** — someone may already be working on it
2. **Open an issue first** for new artifacts — use the [New artifact proposal](.github/ISSUE_TEMPLATE/new-artifact.md) template to discuss before building
3. **If your artifact relates to the book**, read the corresponding chapter first — your artifact should reflect the book's principles, not generic best practices

## Writing a Skill

Skills follow the [Agent Skills](https://agentskills.io) open format — a **directory**, not a single file:

```
skills/skill-name/
├── SKILL.md        # Required: metadata + instructions (under 500 lines)
├── scripts/        # Optional: working scripts agents can run
├── references/     # Optional: detailed docs loaded on demand
└── assets/         # Optional: templates, schemas, data files
```

Key points:

- Every skill must have a **type**: Design, Implementation, Hybrid, or Orchestration
- **Implementation skills** must ship working scripts in `scripts/` — not just prose describing what to run
- **Orchestration skills** reference other skills rather than duplicating their logic
- Skills are **AI vendor-agnostic**: no Claude Code / Cursor / Copilot-specific syntax in the body
- `metadata.version` in `SKILL.md` frontmatter, starting at `0.1.0`
- If the skill relates to a book chapter, set `metadata.chapter` and add a "Related Chapter(s)" section

Use the `write-skill` skill (`.claude/skills/write-skill.md`) for the complete template, frontmatter spec, and quality checklist.

## Writing an Agent

Use the `write-agent` skill (in `.claude/skills/write-agent.md`). Agents are narrow by design — resist the urge to make them general-purpose.

## Writing a Command

Use the `write-command` skill (in `.claude/skills/write-command.md`). Commands are workflow orchestrators, not knowledge repositories — keep them short.

## Quality Bar

Before submitting a PR, run the `artifact-reviewer` agent against your artifact:

```
Review the artifact at skills/your-skill.md using the artifact-reviewer agent.
```

All CRITICAL issues must be resolved. MINOR issues should be addressed. SUGGESTIONs are optional.

## Submitting a PR

1. Fork the repository
2. Create a branch: `artifact/<name>` for new artifacts, `fix/<name>` for corrections
3. Follow the PR template — fill in all sections
4. Run `/sync-inventory` to keep the README inventory accurate
5. If your artifact relates to a book chapter, consider adding it to `appendix-a-skills-catalog.md` in the `book` repo (open a separate PR there, or note it in your PR description)

## Versioning

All artifacts use [semantic versioning](https://semver.org/) in frontmatter:

```yaml
version: "0.1.0"
```

- **Patch** (`0.1.x`) — fixes, clarifications, typos
- **Minor** (`0.x.0`) — new sections, extended scope, improved output
- **Major** (`x.0.0`) — breaking changes (renamed fields, fundamentally different approach)

Start new artifacts at `0.1.0`. Version `1.0.0` signals the artifact has been tested in real-world use.

## Code of Conduct

Be respectful. Focus feedback on the artifact, not the person. Platform engineering has many valid approaches — disagreements about implementation choices are welcome; dismissiveness is not.

## Questions?

Open a discussion or reach out to the author at [foncubierta.com](https://foncubierta.com).
