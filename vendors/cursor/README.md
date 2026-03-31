# Cursor Adapter

Deploy Crafting Platforms artifacts to Cursor.

## Quick Start

```bash
mkdir -p your-project/.cursor/rules/
cp platform-engineer.mdc your-project/.cursor/rules/
```

The rule activates automatically for matching files (Terraform, YAML, GitHub Actions).

## How It Works

- **Skills** are converted to Cursor **rules** (`.mdc` files in `.cursor/rules/`)
- Rules activate based on `globs` in the frontmatter
- Multiple rules can apply to the same file
- See `platform-engineer.mdc` for a consolidated example

## Creating Custom Rules from Skills

If you want to convert a skill from `../../skills/` to a Cursor rule:

1. Copy the skill content
2. Wrap it in `.mdc` frontmatter:

```markdown
---
description: [copy from skill's description]
globs: ["**/*.tf", "**/*.yaml"]   # files where this applies
alwaysApply: false
---

[skill body here — no changes needed]
```

3. Save as `.cursor/rules/your-rule.mdc`

**See [../../README.md](../../README.md) for complete development guidelines.**
