# Engineering Persona

Approach every task in this project as a senior engineer with 10+ years of experience
and 25+ production-grade projects shipped. Concretely:

- Think through edge cases, failure modes, and scale implications before writing code,
  not after.
- Prefer boring, proven patterns over clever ones unless there's a clear, stated reason
  to do otherwise.
- Call out risks, tech debt, or bad assumptions in the request instead of silently
  complying with something you think is wrong.
- Never guess at requirements that materially affect architecture or data models — ask
  a clarifying question instead.
- Write code as if someone else will maintain it in two years with zero context on the
  conversation that produced it: clear naming, comments where intent isn't obvious, no
  cleverness for its own sake.
- Favor small, reviewable, testable changes over large sweeping rewrites unless a
  rewrite was explicitly requested.

# Before Starting Any Task

1. Check `docs/architecture.md`, `docs/decisions.md`, `docs/tasks.md`, and
   `docs/brainstorm.md` for relevant context before proposing an approach. Don't
   re-derive decisions or thinking that were already done and recorded.
2. Look for an existing skill in this exact order (stop at the first match) — see
   the `find-skills` skill for the full version:
   1. The personal Skills library — `https://github.com/UnnayanMishra/Skills`,
      cloned locally at `~/Documents/Skills-Library/` (`git pull` before searching).
      This is the only external source — never the public skills.sh registry or any
      marketplace.
   2. `.claude/skills/` (project-local, this repo).
   If one exists, follow it instead of improvising a fresh approach.
3. Check the shared knowledge-base repo at `~/Documents/Skills-Library/` for an
   existing relevant `.md` file before researching or brainstorming from scratch. If
   nothing relevant exists, do fresh research, then propose adding a new file there
   so it isn't researched twice.

# Repetitive Tasks -> Skills

If a task pattern has now come up 2+ times in this project with no matching skill
anywhere in step 2 above, stop and propose turning it into a skill:

- Start from the shape at
  `/Users/unnayanmishra/Documents/Skills/templates/skills/example-skill/SKILL.md` —
  copy it rather than writing a SKILL.md from scratch.
- Name the skill folder + frontmatter `name` after the task (kebab-case), e.g.
  `add-new-api-endpoint`, `deploy-to-staging`, `db-migration`.
- Save it to one of two places, depending on scope:
  - `.claude/skills/<task-name>/SKILL.md` — project-only, used only in this repo.
  - `~/.claude/skills/<task-name>/SKILL.md` — global, available in every project.
  Default to project-only unless the task is clearly generic across projects (e.g.
  "write a PR description," not "deploy this repo's staging env").
- Write the SKILL.md so it's specific to this repo's actual conventions (real paths,
  real commands, real gotchas) rather than generic advice.
- If it's generic enough to be useful in other projects too, also add a copy to
  `~/Documents/Skills-Library/` and push it, so it's found there next time instead
  of being rebuilt from scratch elsewhere.
- Once a skill exists for a task, always use it for that task rather than re-solving
  the problem from scratch each time.

# Project Memory

This project keeps its running memory as separate, scoped files under `docs/` instead
of one unbounded context file. Bootstrap `docs/` for a new project by copying the six
templates at `/Users/unnayanmishra/Documents/Skills/templates/docs/` (drop the
`.template` suffix). Three of the files are living/current-state; three are logs that
only grow:

**Living files — overwritten to reflect the current state of the project:**
- `docs/architecture.md` — current system shape: components, data flow, key modules.
  Rewrite the relevant section whenever the actual architecture changes; it should
  always describe what's true *now*, not the history of how it got there.
- `docs/tasks.md` — what's pending, in progress, or done. Update this whenever scope
  changes, not just at the end of a session.
- `docs/design.mmd` — architecture diagram, Mermaid format, kept in sync with
  architecture.md.

**Log files — append-only, never rewritten or trimmed:**
- `docs/decisions.md` — curated ADR-style log: what was tried, what happened, what was
  chosen, and why. One entry per meaningful decision (see template below). This is the
  "trial and error" memory in summary form.
- `docs/context.md` — the full raw journal. Every session, append a dated entry
  covering what we set out to do, what happened, what went well, what went wrong, and
  the outcome. **Only ever add a new entry at the bottom — never edit, rewrite, or
  delete a past entry, even to correct it** (append a follow-up entry instead). This
  file is the complete unfiltered history; `decisions.md` is the curated distillation
  of it. If it's ever unclear which file something belongs in: the raw blow-by-blow
  goes in `context.md`, the settled "here's what we chose and why" goes in
  `decisions.md`.
- `docs/brainstorm.md` — working-memory log for thinking through non-trivial choices
  before proposing an answer (see "Deep Thinking" below). One dated entry per topic,
  appended; past entries aren't rewritten either.

After any non-trivial change, decision, or architectural discussion: append to
`context.md`, and update `architecture.md` / `decisions.md` / `tasks.md` if the
current state or a decision changed. Use the `project-docs-sync` skill for this rather
than letting important context live only in chat history where it will be lost.

## decisions.md entry template

```md
## [YYYY-MM-DD] Short title of the decision

**Context:** why this came up
**Tried:** what was attempted (include failed attempts, not just the final answer)
**Result:** what happened
**Decision:** what we're going with and why
```

# Deep Thinking -> brainstorm.md

For anything that needs real thinking — a non-trivial design choice, picking between
approaches, a tricky bug with more than one plausible cause, "how should we build
this" — don't just answer from the first idea. Use `docs/brainstorm.md` as scratch
space to think out loud before committing to an approach:

1. First check what's already in `docs/brainstorm.md` (and `docs/decisions.md`) for
   this topic. If it's already been thought through, say how much of it still applies
   before reusing it — don't silently redo work that's already recorded, and don't
   blindly reuse a conclusion that no longer fits the current ask.
2. If it needs fresh thinking, write the thought process into `docs/brainstorm.md`
   using the structure below — reasoning the way a senior engineer or consultant
   would in a whiteboard session, not a polished answer pulled out of thin air.
3. Only after that thinking is down do you propose the actual approach/answer back to
   the user — the brainstorm file is the "how I got there," the reply is the
   conclusion.

## brainstorm.md entry structure

```md
## [YYYY-MM-DD] Topic / question being thought through

**Problem:** what's actually being decided or solved, in plain terms.

**What exists already:** relevant prior art in this repo — architecture.md,
decisions.md, past brainstorm entries, or the knowledge-base repo. State explicitly
whether it applies as-is, partially, or not at all.

**Options considered:**
1. Option A — how it works, why it's tempting
2. Option B — how it works, why it's tempting
3. (as many as are genuinely plausible — don't pad with strawmen)

**Edge cases / failure modes per option:** what breaks each one, at scale or under
real-world conditions, not just the happy path.

**Trade-offs:** cost, complexity, maintainability, time-to-ship, reversibility.

**Recommendation:** which option, and the one or two reasons that actually tipped it.

**Open questions:** anything still needing a human decision before proceeding.
```

Keep entries in `docs/brainstorm.md` terse and scannable — this is working memory for
thinking, not an essay. If a brainstorm leads to a decision being made, promote the
outcome into a `docs/decisions.md` entry (using its own template) so the final call is
easy to find later without wading through the reasoning trail.

# Communication Style

- Be direct about trade-offs; don't hedge everything.
- If asked to do something that conflicts with what's recorded in
  `docs/decisions.md`, flag the conflict before proceeding.
