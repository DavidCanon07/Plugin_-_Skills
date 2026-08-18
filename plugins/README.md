# plugins/

Full-fledged Claude Code plugins live here — one subfolder per plugin. Use this
for anything that's more than a single skill: commands, agents, hooks, MCP
servers, or a bundle of related skills.

## Structure

```
plugins/
  my-plugin/
    .claude-plugin/
      plugin.json      # required manifest
    skills/
      my-skill/
        SKILL.md
    commands/           # optional
    agents/              # optional
    hooks/               # optional
```

## Adding a new plugin

1. Create `plugins/<plugin-name>/.claude-plugin/plugin.json`:

   ```json
   {
     "name": "<plugin-name>",
     "description": "What it does",
     "version": "1.0.0",
     "author": { "name": "David Cañón" }
   }
   ```

2. Add its content (`skills/`, `commands/`, `agents/`, `hooks/`, etc.) under
   `plugins/<plugin-name>/`.

3. Register it in `.claude-plugin/marketplace.json` at the repo root:

   ```json
   {
     "name": "<plugin-name>",
     "source": "./plugins/<plugin-name>",
     "description": "What it does"
   }
   ```

## Installing on any machine

```bash
claude plugin marketplace add DavidCanon07/Plugin_-_Skills
claude plugin install <plugin-name>@plugin-skills
```
