# Plugin_-_Skills

Catálogo personal de plugins y skills de Claude Code. Este repo es también un
marketplace instalable (`plugin-skills`), así que cualquier PC puede sumarlo y
traer solo lo que necesite en ese momento.

## Estructura

- **`plugins/`** — plugins completos (comandos, agentes, hooks, MCP servers).
  Un subdirectorio por plugin. Ver `plugins/README.md`.
- **`skills/`** — skills sueltas (solo `SKILL.md`), cada una instalable por
  separado. Ver `skills/README.md`.
- **`.claude-plugin/marketplace.json`** — catálogo que lista todo lo anterior.
- **`.claude/settings.json`** — plugins de marketplaces externos (p. ej.
  `superpowers@claude-plugins-official`) habilitados para este proyecto.

## Sincronizar en una PC nueva

```bash
claude plugin marketplace add DavidCanon07/Plugin_-_Skills
claude plugin install <nombre>@plugin-skills
```

Repite el segundo comando por cada plugin o skill puntual que quieras traer a
esa máquina — no hace falta instalar todo el catálogo.

Para refrescar el catálogo tras un cambio:

```bash
claude plugin marketplace update plugin-skills
```
