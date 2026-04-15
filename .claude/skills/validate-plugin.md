---
name: validate-plugin
description: Validate a plugin in the craftingplatforms/ai marketplace for structural correctness, manifest completeness, and skill quality. Use before publishing a new plugin or after editing plugin.json.
---

# Validating a Crafting Platforms Plugin

## Context

You are reviewing a plugin in the `craftingplatforms/ai` repository. Plugins must conform to the Claude Code Plugin Marketplace spec and the Crafting Platforms quality bar before being published.

## What to Check

### 1. Directory structure

Verify the plugin has this layout:
```
plugins/<name>/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── <skill-name>/
│       └── SKILL.md
└── references -> ../../references   (symlink)
```

- [ ] `.claude-plugin/plugin.json` exists
- [ ] `skills/` directory exists and contains at least one skill
- [ ] `references` is a symlink pointing to `../../references`
- [ ] No skills or agent files are inside `.claude-plugin/` (only `plugin.json` belongs there)

### 2. plugin.json manifest

Read `.claude-plugin/plugin.json` and check:

- [ ] Valid JSON (no syntax errors)
- [ ] `name` is present, lowercase, kebab-case, no spaces
- [ ] `name` matches the plugin directory name exactly
- [ ] `version` is present and follows semver (`x.y.z`)
- [ ] `description` is present and meaningful (not a placeholder)
- [ ] `license` is `"Apache-2.0"`
- [ ] `keywords` is an array of relevant strings

### 3. marketplace.json registration

Read `.claude-plugin/marketplace.json` and check:

- [ ] The plugin has an entry in the `plugins` array
- [ ] The `name` in the entry matches `plugin.json`
- [ ] The `source` path is `./plugins/<name>` (relative, starts with `./`)
- [ ] `description`, `version`, `license`, `category`, and `keywords` are present

### 4. Skill quality

For each skill in `plugins/<name>/skills/`:

- [ ] Directory name matches the `name` field in `SKILL.md`
- [ ] `name` is lowercase, hyphens only, max 64 chars
- [ ] `description` describes what it does *and* when to use it (max 1024 chars)
- [ ] `metadata.version` is set
- [ ] Skill type is declared (Design / Implementation / Hybrid / Orchestration)
- [ ] `SKILL.md` body is under 500 lines
- [ ] No references to specific AI tool mechanics in the body ("use the Skill tool", "in Claude Code")
- [ ] If chapter-related: `metadata.chapter` is set and a "Related Chapter(s)" section links to the book

### 5. Cross-validation

- [ ] Every skill directory listed in `skills/` has a valid `SKILL.md`
- [ ] No duplicate skill names across plugins in the marketplace

## Output Format

```
## Plugin Validation: <plugin-name>

**Overall:** Pass / Needs Work / Fail

### Structural Issues
- [CRITICAL] <must fix — plugin won't load>
- [MINOR] <should fix — degrades quality>

### Manifest Issues
- ...

### Skill Issues (<skill-name>)
- ...

### What Looks Good
- ...

### Recommended Fixes
<Specific edits with file paths>
```

If the plugin passes all checks, say so clearly and confirm it is ready to commit.
