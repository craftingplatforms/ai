# GitHub Copilot Adapter

Deploy Crafting Platforms artifacts to GitHub Copilot.

## Quick Start

```bash
mkdir -p your-project/.github/
cp platform-engineer.md your-project/.github/copilot-instructions.md
```

GitHub Copilot automatically reads `.github/copilot-instructions.md` and uses it as context for all suggestions and chat in that repo.

## How It Works

- **Skills** are incorporated into a single `.github/copilot-instructions.md` file
- The file provides persistent context across the entire repository
- Copilot uses it in VS Code, JetBrains IDEs, and the GitHub web UI
- See `platform-engineer.md` for a consolidated example

## Creating Custom Instructions from Skills

If you want to add a skill from `../../skills/` to Copilot instructions:

1. Copy the skill content
2. Append it to `.github/copilot-instructions.md`
3. Remove the YAML frontmatter — Copilot doesn't use it

**See [../../README.md](../../README.md) for complete development guidelines.**
