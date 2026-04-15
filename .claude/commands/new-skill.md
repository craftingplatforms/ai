Create a new skill for this repository following the Agent Skills format.

## Steps

1. **Ask for the skill details** if not already provided:
   - What platform engineering task should this skill accomplish?
   - What type? (Design / Implementation / Hybrid / Orchestration)
   - Which plugin should this skill belong to? (existing: `aws`, `azure`, `gcp`, `kubernetes`, `platform-design` — or create a new one with `/new-plugin`)
   - Does it relate to a book chapter? If so, which one(s)?
   - Does it have system requirements? (tools, network access, cloud credentials)
   - What should it be named? (suggest a kebab-case action name)

2. **Use the `write-skill` skill** to produce the content.

3. **Create the skill directory and files:**
   ```
   plugins/<plugin>/skills/<name>/
   ├── SKILL.md          # always
   ├── scripts/          # if Implementation or Hybrid
   └── assets/           # if templates or data files are needed
   ```
   Note: do not create a `references/` subdirectory inside the skill — use `references/notation.md` and `references/types.md` from the plugin's `references` symlink instead.

4. **Update `README.md`** — add a row to the Artifact Inventory under the correct plugin section:
   ```
   | [`<name>`](plugins/<plugin>/skills/<name>/) | <Chapter N or "—"> | Published |
   ```

5. **If the skill relates to a book chapter**, remind the user:
   > Consider updating `../book/chapters/en/appendix-a-skills-catalog.md`. Open a Claude session in `book/` to do this.

6. **Suggest committing:**
   ```
   Add <name> skill to <plugin> plugin
   ```
