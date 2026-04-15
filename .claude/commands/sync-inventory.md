Check that the README.md Artifact Inventory is accurate and in sync with what is actually in the repository.

## Steps

1. **Scan the repository** for all artifacts:
   - For each plugin directory under `plugins/`, list all `SKILL.md` files in `plugins/<plugin>/skills/`
   - List all `*.md` files in `.claude/commands/` (excluding internal meta-commands)
   - List all `*.md` files in `agents/` (excluding `README.md`)
   - List all `*.sh` files in `hooks/`
   - List all subdirectories in `mcp/`
   - Read each plugin's `.claude-plugin/plugin.json` to get its name and description

2. **Read the Artifact Inventory section** from `README.md`.

3. **Compare** — flag any discrepancy:
   - Plugins or skills present in the file system but missing from the inventory
   - Inventory entries referencing files that do not exist
   - Status mismatches (file exists but status says "Planned")
   - Skills listed under the wrong plugin section

4. **Fix discrepancies automatically** — update `README.md` to reflect the current state:
   - Add missing entries under the correct plugin section
   - Remove stale entries
   - Update statuses from "Planned" to "Published" where files now exist
   - Inventory rows for skills use path format: `plugins/<plugin>/skills/<name>/`

5. **Check the book cross-reference** *(optional)* — if `../book/chapters/en/appendix-a-skills-catalog.md` exists, read it and flag any skills present here that have a book chapter reference but are not listed there.
   - Skip skills with no book chapter reference — they don't need to be in the catalog.
   - Do not edit the book file — just report what needs updating.

6. **Report** a brief summary of what was changed and what (if anything) still needs manual attention in the book.
