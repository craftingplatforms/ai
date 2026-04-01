Create a new skill for this repository.

## Steps

1. **Ask for the skill details** if not already provided:
   - Which book chapters does this skill correspond to?
   - What platform engineering task should the skill accomplish?
   - What should the skill be named? (suggest a kebab-case name based on the task)

2. **Use the `write-skill` skill** to produce the skill file content.

3. **Create the file** at `skills/<name>.md`.

4. **Update `README.md`** — find the Artifact Inventory section and add a row to the Skills table:
   ```
   | `<name>` | Ch. N — <Chapter Name> | Published |
   ```

5. **Remind the user** to update the book's appendix:
   > The skills catalog in `../book/chapters/en/appendix-a-skills-catalog.md` should be updated to include this skill. Open a Claude session in `book/` to do this.

6. **Suggest committing** with a message like:
   ```
   Add <name> skill (Chapter N: <Chapter Name>)
   ```
