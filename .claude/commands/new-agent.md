Create a new agent for this repository.

## Steps

1. **Ask for the agent details** if not already provided:
   - Does this agent relate to a book chapter? If so, which one(s)?
   - What is the agent's singular focus — what does it do and nothing else?
   - What tools does it need? (default: Read, Grep — ask only if more seem necessary)
   - What should the agent be named? (suggest a kebab-case role name)

2. **Use the `write-agent` skill** to produce the agent file content.

3. **Create the file** at `agents/<name>.md`.

4. **Update `README.md`** — find the Artifact Inventory section and add a row to the Agents table:
   ```
   | `<name>` | <Chapter N or "—"> | <focus> | Published |
   ```

5. **Remind the user** that if this agent is meant to be invoked from a skill or command, that skill/command should reference it by name.

6. **Suggest committing** with a message like:
   ```
   Add <name> agent
   ```
