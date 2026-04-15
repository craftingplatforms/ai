---
name: write-plugin
description: Scaffold a new plugin for the craftingplatforms/ai marketplace. Use when asked to create a new plugin — produces the directory structure, plugin.json manifest, and references symlink.
---

# Writing a Crafting Platforms Plugin

## Context

You are working in the `craftingplatforms/ai` repository, which is structured as a Claude Code Plugin Marketplace. Plugins are self-contained directories under `plugins/` — each contains a `.claude-plugin/plugin.json` manifest, a `skills/` directory, and a `references` symlink to the shared `references/` at the repo root.

Plugins group related skills by cloud provider or domain. Each plugin is independently installable:
```
/plugin install aws@crafting-platforms
```

## Plugin Directory Structure

```
plugins/<name>/
├── .claude-plugin/
│   └── plugin.json        # Required: plugin manifest
├── skills/
│   └── <skill-name>/
│       └── SKILL.md
└── references -> ../../references   # Symlink — gives skills access to shared notation
```

## plugin.json Template

```json
{
  "name": "<kebab-case-name>",
  "version": "0.1.0",
  "description": "<One sentence describing what this plugin provides>",
  "author": {
    "name": "Ezequiel Foncubierta"
  },
  "homepage": "https://github.com/efoncubierta/craftingplatforms-ai",
  "repository": "https://github.com/efoncubierta/craftingplatforms-ai",
  "license": "Apache-2.0",
  "keywords": ["<keyword1>", "<keyword2>"]
}
```

### Required fields
| Field | Notes |
|-------|-------|
| `name` | Kebab-case, no spaces, max 64 chars. Must match directory name. |
| `version` | Start at `"0.1.0"` |
| `description` | One sentence. What platform engineering tasks does this plugin cover? |
| `license` | Always `"Apache-2.0"` for this repo |

### Optional but recommended
| Field | Notes |
|-------|-------|
| `author` | Always `{"name": "Ezequiel Foncubierta"}` for first-party plugins |
| `keywords` | Include cloud provider, domain, and key task names |

## Steps to Create a Plugin

1. **Create the directory structure:**
   ```bash
   mkdir -p plugins/<name>/.claude-plugin
   mkdir -p plugins/<name>/skills
   ```

2. **Create `plugin.json`** using the template above.

3. **Create the references symlink** so skills can access shared notation:
   ```bash
   ln -s ../../references plugins/<name>/references
   git add plugins/<name>/references
   ```

4. **Add skills** using the `write-skill` skill. Each skill goes in `plugins/<name>/skills/<skill-name>/SKILL.md`.

5. **Register in `marketplace.json`** — add a new entry to the `plugins` array in `.claude-plugin/marketplace.json`:
   ```json
   {
     "name": "<plugin-name>",
     "source": "./plugins/<plugin-name>",
     "description": "<same as plugin.json description>",
     "version": "0.1.0",
     "license": "Apache-2.0",
     "category": "<platform-engineering | cloud-infrastructure | security | ...>",
     "keywords": ["<keyword1>", "<keyword2>"]
   }
   ```

6. **Update `README.md`** — add a section for the new plugin in the Artifact Inventory.

## References Symlink

The `references` symlink points to `../../references` (the repo-root `references/` directory). This gives skills access to `references/notation.md` and `references/types.md` without embedding them.

**Why this works:** The marketplace is distributed via Git. When users install via `/plugin marketplace add efoncubierta/craftingplatforms-ai`, the full repo structure is cloned, so the relative symlink resolves correctly. Symlinks are preserved in the plugin cache rather than dereferenced.

## Quality Checklist

Before finishing:

- [ ] `plugins/<name>/.claude-plugin/plugin.json` exists and is valid JSON
- [ ] `name` matches the directory name exactly
- [ ] `version` is set
- [ ] `description` is specific — says what cloud/domain and what tasks
- [ ] `references` symlink created and staged with `git add`
- [ ] Entry added to `.claude-plugin/marketplace.json`
- [ ] `README.md` inventory updated
- [ ] Skills follow the `write-skill` quality checklist

## After Writing the Plugin

Run `/sync-inventory` to verify the README.md inventory is accurate.
