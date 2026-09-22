---
name: TASK-NAME-HERE
description: One sentence describing exactly when this skill should trigger — be specific about the task, not generic. e.g. "Use when adding a new REST API endpoint to the backend — covers route registration, validation, and tests in this repo's pattern."
---

# Task Name Here

<!--
Rename this file's folder + frontmatter `name` to match the task, e.g.:
  .claude/skills/add-new-api-endpoint/SKILL.md
  .claude/skills/deploy-to-staging/SKILL.md
  .claude/skills/db-migration/SKILL.md

The description above is what Claude Code matches against to decide whether to
load this skill — make it specific to your repo's task, not generic advice.
-->

## When to use this

Describe the trigger condition in one or two lines: what request or situation should
cause this skill to be picked up.

## Prerequisites / context to check first

- Any docs/files to read before starting (e.g. `docs/architecture.md` section X)
- Any environment/config assumptions

## Requirements to proceed

List the specific pieces of information this task cannot be done correctly without —
not generic "gather requirements," but the actual inputs that change the outcome if
they're wrong or missing. For each one, give the exact question to ask if it isn't
already known. If a required item is missing, STOP and ask — do not guess a default
and proceed, since a wrong guess here is more expensive to unwind than asking.

- **<requirement 1>:** why it matters / what it changes about the approach.
  - *Ask if missing:* "<the actual question to ask the user>"
- **<requirement 2>:** ...
  - *Ask if missing:* "<...>"
- (as many as genuinely change the design/approach — don't pad with things that
  don't actually matter)

## Steps

1. Step one — be concrete: real file paths, real commands, real repo conventions.
2. Step two — include the gotcha you learned the hard way, not just the happy path.
3. Step three — ...

## Validation

How to confirm the task was done correctly (tests to run, command to check, output to
verify).

## Notes / known pitfalls

- Anything non-obvious that has bitten you before doing this task in this repo.
- Link to a `docs/decisions.md` entry if this pattern was the result of a past
  trial-and-error.
