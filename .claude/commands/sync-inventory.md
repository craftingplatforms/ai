Check that the README.md Artifact Inventory is accurate and in sync with what is actually in the repository.

## Steps

1. **Scan the repository** for all artifacts:
   - List all `*.md` files in `skills/` (excluding `README.md`)
   - List all `*.md` files in `commands/` (excluding `README.md`)
   - List all `*.md` files in `agents/` (excluding `README.md`)
   - List all `*.sh` files in `hooks/`
   - List all subdirectories in `mcp/`

2. **Read the Artifact Inventory section** from `README.md`.

3. **Compare** — flag any discrepancy:
   - Artifacts present in the file system but missing from the inventory
   - Inventory entries referencing files that do not exist
   - Status mismatches (file exists but status says "Planned")

4. **Fix discrepancies automatically** — update `README.md` to reflect the current state:
   - Add missing entries
   - Remove stale entries
   - Update statuses from "Planned" to "Published" where files now exist

5. **Check the book cross-reference** *(optional)* — if `../book/chapters/en/appendix-a-skills-catalog.md` exists, read it and flag any skills present here that have a book chapter reference but are not listed there.
   - Skip skills with no book chapter reference — they don't need to be in the catalog.
   - Do not edit the book file — just report what needs updating.

6. **Report** a brief summary of what was changed and what (if anything) still needs manual attention in the book.
