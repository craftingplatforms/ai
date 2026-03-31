# Claude Code Adapter

Deploy Crafting Platforms artifacts to Claude Code.

## Quick Start

```bash
# Copy skills globally
cp ../../skills/*.md ~/.claude/skills/

# Or per-project
mkdir -p your-project/.claude/skills/
cp ../../skills/*.md your-project/.claude/skills/
```

Then invoke in Claude Code:
```
Use the design-segmentation skill to help me design a platform segmentation strategy.
```

## Artifact Types

| Artifact | Where it goes | Example |
|----------|---------------|---------|
| Skill | `~/.claude/skills/` or `.claude/skills/` | `design-segmentation.md` |
| Command | `.claude/commands/` | `platform-review.md` → invoked as `/platform-review` |
| Agent | `.claude/agents/` | Spawned via the Agent tool |
| Hook | `.claude/hooks/` | Configured in `.claude/settings.json` |
| MCP | `.claude/mcp/` | Configured in `.claude/settings.json` |

**See [../../README.md](../../README.md) for complete setup and development guidelines.**
