# Tesseractuk-Skill-Template

Per-project scaffolding for the Claude Code workflow — this repo does NOT hold the
knowledge base or the skill library, only the template shape:

- `templates/` — copy into any new project to bootstrap its `CLAUDE.md` + `docs/`
  memory system (architecture, decisions, tasks, append-only context log, brainstorm)

Custom skills for repetitive tasks are NOT stored here — they live in
`~/.claude/skills/<name>/SKILL.md` (available in every project) or
`<project>/.claude/skills/<name>/SKILL.md` (project-only). `templates/skills/`
just holds the SKILL.md shape to copy from. The searchable skill library and the
shared reference knowledge base both live in the separate `Skills` repo
(github.com/UnnayanMishra/Skills, cloned locally at `~/Documents/Skills-Library/`).

## How this connects to Claude Code

- `~/.claude/CLAUDE.md` (global, loaded every session) — has the senior-dev persona
  and the rules that point at this repo and at `~/Documents/Skills-Library/`
- **New project:** copy `templates/CLAUDE.md.template` → `<project>/CLAUDE.md`, and
  each file in `templates/docs/*.template` → `<project>/docs/*.md` (drop the
  `.template` suffix)
- **Repetitive task noticed:** scaffold a skill with the `skill-creator` skill into
  `~/.claude/skills/<name>/` (global) or `<project>/.claude/skills/<name>/`
  (project-only), using `templates/skills/example-skill/SKILL.md` as the shape
- **Research/design question:** search `~/Documents/Skills-Library/` first; if
  nothing fits, research fresh and add a new file there

## Why context.md is separate from decisions.md

`context.md` is append-only and never edited — the full chronological trail of what
was attempted, including dead ends, so nothing is ever lost. `decisions.md` is the
curated summary (ADR-style) of what was actually decided and why. Read `decisions.md`
for the current rationale; read `context.md` when you need the full history of how
you got there.
