# Plugin - Skills

A Claude Code plugin marketplace hosted in this repo. It currently vendors
one plugin: **ponytail**.

## ponytail

"Lazy senior dev mode" — a skill that forces the simplest, shortest solution
that actually works: YAGNI first, reuse before rewrite, standard library and
native platform features before new dependencies, one line before fifty.
Never trades away validation, error handling, security, or accessibility.

- Upstream: https://github.com/dietrichgebert/ponytail
- License: MIT (Dietrich Gebert) — see [`LICENSE`](LICENSE)
- Vendored version: `4.9.0`

This repo carries only the Claude Code plugin surface from upstream
(`.claude-plugin/`, `hooks/`, `skills/`, `AGENTS.md`, `LICENSE`). The
upstream repo also ships adapters for ~20 other agents (Codex, Copilot CLI,
Cursor, Windsurf, opencode, etc.), plus benchmarks, docs, and tests — those
were intentionally left out since they aren't needed to install or run the
plugin in Claude Code. To update, re-pull the same subset from upstream and
diff against what's here; this is a manual vendor, not a submodule.

### Install

```
/plugin marketplace add DavidCanon07/Plugin_-_Skills
```
```
/plugin install ponytail@ponytail
```

(Send these as two separate prompts — installing right after adding the
marketplace in the same message doesn't register.)

The plugin runs two small Node.js lifecycle hooks (`SessionStart`,
`SubagentStart`, `UserPromptSubmit` — see
[`hooks/claude-codex-hooks.json`](hooks/claude-codex-hooks.json)), so `node`
needs to be on your PATH. If it isn't, the skills still work; the
always-on activation just stays quiet instead of erroring on every prompt.

### What's in the box

| Path | Purpose |
|---|---|
| `.claude-plugin/plugin.json` | Plugin manifest |
| `.claude-plugin/marketplace.json` | Marketplace manifest (this repo as a marketplace) |
| `hooks/` | Lifecycle hooks that activate/track ponytail mode each session |
| `skills/ponytail/` | Main skill: the laziness ladder |
| `skills/ponytail-audit/`, `-debt/`, `-gain/`, `-help/`, `-review/` | Companion skills (debt tracking, code review, help) |

Switch intensity anytime with `/ponytail lite\|full\|ultra`, or turn it off
with "stop ponytail" / "normal mode".
