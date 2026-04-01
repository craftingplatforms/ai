Create a new skill for this repository following the Agent Skills format.

## Steps

1. **Ask for the skill details** if not already provided:
   - What platform engineering task should this skill accomplish?
   - What type? (Design / Implementation / Hybrid / Orchestration)
   - Does it relate to a book chapter? If so, which one(s)?
   - Does it have system requirements? (tools, network access, cloud credentials)
   - What should it be named? (suggest a kebab-case action name)

2. **Use the `write-skill` skill** to produce the content.

3. **Create the skill directory and files:**
   ```
   skills/<name>/
   ├── SKILL.md          # always
   ├── scripts/          # if Implementation or Hybrid
   ├── references/       # if content exceeds 500 lines in SKILL.md
   └── assets/           # if templates or data files are needed
   ```

4. **Update `README.md`** — add a row to the Artifact Inventory:
   ```
   | [`<name>`](skills/<name>/) | <Chapter N or "—"> | Published |
   ```

5. **If the skill relates to a book chapter**, remind the user:
   > Consider updating `../book/chapters/en/appendix-a-skills-catalog.md`. Open a Claude session in `book/` to do this.

6. **Suggest committing:**
   ```
   Add <name> skill
   ```
