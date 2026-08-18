# skills/

Standalone skills — no commands, agents, hooks, or MCP servers, just a
`SKILL.md` — live here, one subfolder per skill. Each one is registered as its
own tiny installable "plugin" in the marketplace, so you can pull in exactly
the skill you need on a given machine instead of installing everything.

## Structure

```
skills/
  my-skill/
    SKILL.md
```

## Adding a new skill

1. Create `skills/<skill-name>/SKILL.md`:

   ```markdown
   ---
   description: One-line trigger description for when Claude should use this
   ---

   Instructions for the skill go here.
   ```

2. Register it in `.claude-plugin/marketplace.json` at the repo root as its
   own plugin entry pointing back at the marketplace root, scoped to just
   this skill's folder:

   ```json
   {
     "name": "<skill-name>",
     "source": "./",
     "skills": ["./skills/<skill-name>"],
     "description": "One-line description",
     "strict": false
   }
   ```

## Installing on any machine

```bash
claude plugin marketplace add DavidCanon07/Plugin_-_Skills
claude plugin install <skill-name>@plugin-skills
```

Only the skills you actually install get pulled onto that machine.
