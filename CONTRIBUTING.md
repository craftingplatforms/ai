# Contributing to Crafting Platforms AI Artifacts

Thank you for contributing! Every artifact here helps platform engineers move faster and build better internal platforms. This guide explains how to add new artifacts and what quality looks like.

## What We Accept

Contributions grounded in the content of *Crafting Platforms* by Ezequiel Foncubierta:

- **Skills** — reusable AI instructions for platform engineering tasks (design, implementation, hybrid, orchestration)
- **Commands** — named workflows invoked via slash command
- **Agents** — specialized sub-agents with narrow scope and tool sets
- **Hooks** — event-driven automation scripts
- **MCP servers** — domain-specific tool extensions

We do **not** accept artifacts that are speculative, not tied to a book chapter, or duplicate existing work without clear improvement.

## Before You Start

1. **Check open issues and PRs** — someone may already be working on it
2. **Open an issue first** for new artifacts — use the [New artifact proposal](.github/ISSUE_TEMPLATE/new-artifact.md) template to discuss before building
3. **Read the book chapter** the artifact relates to — your artifact should reflect the book's principles, not generic best practices

## Writing a Skill

Use the `write-skill` skill (in `.claude/skills/write-skill.md`) as your guide. Key points:

- Every skill must have a **type**: Design, Implementation, Hybrid, or Orchestration
- **Implementation skills** should produce real, working output (Terraform, scripts, pipelines)
- **Orchestration skills** should reference other skills — internal or external — rather than duplicate their logic
- Skills are **vendor-agnostic**: no Claude Code / Cursor / Copilot-specific syntax in the body
- All skills must include a **version** in frontmatter (semver, start at `0.1.0`)
- Every skill must link back to its book chapter(s) in the "Related Chapter(s)" section

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
5. If your skill is new, add it to `../book/chapters/en/appendix-a-skills-catalog.md` (open a separate PR in the `book` repo, or note it in your PR description)

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
