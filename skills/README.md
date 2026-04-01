# Skills

Self-contained, AI vendor-agnostic skills for platform engineering tasks. Each skill teaches an AI agent how to approach a specific problem — designing segmentation strategies, scaffolding infrastructure, auditing security, and more.

Skills follow the [Agent Skills](https://agentskills.io) open format, supported by Claude Code, Cursor, GitHub Copilot, Gemini CLI, and many others.

## Structure

Each skill is a **directory**, not a single file:

```
skills/
└── skill-name/
    ├── SKILL.md        # Required: metadata + instructions
    ├── scripts/        # Optional: executable scripts (Python, Bash, etc.)
    ├── references/     # Optional: detailed reference docs loaded on demand
    └── assets/         # Optional: templates, schemas, data files
```

The directory name must match the `name` field in `SKILL.md`.

## SKILL.md format

```markdown
---
name: skill-name
description: What this skill does and when to use it. Be specific — this is how agents decide to activate the skill.
license: Apache-2.0
compatibility: Requires Terraform CLI and AWS credentials
metadata:
  version: "0.1.0"
  chapter: "4"        # optional — book chapter reference
allowed-tools: Bash(terraform:*) Read
---

# Skill Title

[Instructions for the agent. Keep under 500 lines.
Move detailed reference material to references/.]
```

### Frontmatter fields

| Field | Required | Notes |
|-------|----------|-------|
| `name` | Yes | Lowercase, hyphens only, max 64 chars. Must match directory name. |
| `description` | Yes | Max 1024 chars. Describe *what* it does and *when* to use it. |
| `license` | No | e.g. `Apache-2.0` |
| `compatibility` | No | System requirements, network access, intended tools |
| `metadata` | No | Arbitrary key-value pairs — use for `version`, `chapter`, author, etc. |
| `allowed-tools` | No | Pre-approved tools the skill may invoke (experimental) |

## Progressive disclosure

Agent Skills load in three stages — write accordingly:

1. **`name` + `description`** (~100 tokens) — loaded at startup for all skills. Make the description precise so the agent activates the skill reliably.
2. **`SKILL.md` body** — loaded when the skill is activated. Keep under 500 lines. Reference external files rather than embedding everything.
3. **`scripts/`, `references/`, `assets/`** — loaded only when the agent reads them. Put detail here.

## scripts/

Executable code the agent can run. Each script should:
- Be self-contained or clearly document dependencies
- Handle errors with helpful messages
- Work as a standalone tool, not just as a companion to the instructions

Common patterns: Terraform wrappers, validation scripts, scaffolding generators, data extractors.

## references/

Detailed documentation loaded on demand — not at activation. Keep files focused:

```
references/
├── REFERENCE.md      # Detailed technical reference
├── aws.md            # AWS-specific guidance
└── azure.md          # Azure-specific guidance
```

## assets/

Static resources: templates, schemas, configuration examples, data files.

## Best practices

- **One skill, one task** — if it does two things, consider two skills
- **Description is critical** — agents use it to decide whether to activate the skill; include specific keywords for the task domain
- **Keep SKILL.md focused** — move detail to `references/`; agents load the body in full when activated
- **Scripts are first-class** — implementation skills should ship working scripts, not just describe what to run
- **Version in metadata** — use `metadata.version` with semver; start at `0.1.0`, reach `1.0.0` when tested in real use
- **Compatibility matters** — declare system requirements so users know what the skill needs

## Contributing a skill

Read [CONTRIBUTING.md](../CONTRIBUTING.md) for the full process, quality bar, and PR checklist.

Use the `write-skill` skill (`.claude/skills/write-skill.md`) for the complete template and quality checklist.
