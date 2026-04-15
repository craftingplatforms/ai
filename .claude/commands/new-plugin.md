Create a new plugin for the craftingplatforms/ai marketplace.

## Steps

1. **Ask for the plugin details** if not already provided:
   - What should this plugin be called? (suggest a kebab-case name — e.g., `aws`, `platform-design`)
   - What is it for? (one sentence description — cloud provider, domain, and what it enables)
   - What category? (`platform-engineering`, `cloud-infrastructure`, `security`, or other)
   - What keywords best describe it?
   - What skills should it include? (if known up front)

2. **Use the `write-plugin` skill** to scaffold the full plugin structure:
   - `plugins/<name>/.claude-plugin/plugin.json`
   - `plugins/<name>/skills/` directory
   - `plugins/<name>/references` symlink → `../../references`
   - Entry added to `.claude-plugin/marketplace.json`

3. **If skills were specified**, create them using the `write-skill` skill for each one, placing each in `plugins/<name>/skills/<skill-name>/SKILL.md`.

4. **Update `README.md`** — add a row to the Artifact Inventory under the appropriate plugin heading:
   ```
   | [`<skill-name>`](plugins/<plugin>/skills/<skill-name>/) | <Chapter N or "—"> | Published |
   ```
   If this is a new plugin with no prior section, add a new `### <Plugin Name>` heading.

5. **Validate the plugin** using the `validate-plugin` skill. Fix any issues before continuing.

6. **If any skill relates to a book chapter**, remind the user:
   > Consider updating `../book/chapters/en/appendix-a-skills-catalog.md`. Open a Claude session in `book/` to do this.

7. **Suggest committing:**
   ```
   Add <name> plugin
   ```
