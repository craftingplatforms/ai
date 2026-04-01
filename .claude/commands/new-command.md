Create a new command for this repository.

## Steps

1. **Ask for the command details** if not already provided:
   - What workflow should this command orchestrate?
   - What is its name? (suggest a kebab-case verb phrase — the filename becomes `/command-name`)
   - Which existing skills does it call, if any?

2. **Use the `write-command` skill** to produce the command file content.

3. **Create the file** at `commands/<name>.md`.

4. **Update `README.md`** — find the Artifact Inventory section and add a row to the Commands table:
   ```
   | `/<name>` | <purpose> | Published |
   ```

5. **Update `CLAUDE.md`** — if this is an operational command for maintaining the repo itself, add it to the Operations table.

6. **Suggest committing** with a message like:
   ```
   Add /<name> command
   ```
