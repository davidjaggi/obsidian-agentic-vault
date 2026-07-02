# Skill: Manage a Project

**When to use**: Creating a new project under `20 Projects/`, or doing any
work inside an existing project folder.

**Project structure**: every project is a self-contained subfolder of
`20 Projects/<project name>/` and always contains:

- `<project name>.md` - a note with the **same name as the project
  folder**, created from `90 Meta/Templates/Project/PROJECT.md`. This is
  the only file in the project meant to be linked to from elsewhere in
  the vault (e.g. from a daily note or another project) - all-caps files
  below are internal to the project and not link targets.
- `INDEX.md` - the structure of the project: outcome, links to its
  Meeting Notes/Tasks/sub-notes. Created once from
  `90 Meta/Templates/Project/INDEX.md`, edited as the project's shape
  changes.
- `CONTEXT.md` - a short, current-state snapshot (status, next step, open
  questions), created from `90 Meta/Templates/Project/CONTEXT.md`.
  **Overwrite this file after every interaction** with the project - it
  is not a history, just enough for an agent to pick the project up cold.
  Keep it a few lines; if it's growing long, you're writing log entries
  into it by mistake.
- `LOG.md` - the thorough, append-only history this project's `CONTEXT.md`
  is summarized from, created from `90 Meta/Templates/Project/LOG.md`.
  Append a dated entry with real detail (what was discussed, decided,
  done) after every interaction. Never edit or delete past entries.

All-caps file names (`INDEX.md`, `CONTEXT.md`, `LOG.md`) mark
load-bearing, machine-maintained files internal to the project, not
regular notes and not link targets.

Other project contents (meeting notes, journals, tasks) live as regular
files directly in the project folder, or in subfolders if there are many
of one kind (e.g. `Meeting Notes/`) - this is the one place in the vault
where that extra nesting is allowed, since the project must stay
self-contained.

**Steps for a new project**:
1. Create `20 Projects/<project name>/`.
2. Add `<project name>.md`, `INDEX.md`, `CONTEXT.md`, and `LOG.md` from
   the templates above.
3. Fill in the outcome in `INDEX.md` and the description in
   `<project name>.md`.

**Steps during any interaction with an existing project**:
1. Read `INDEX.md` first to understand the project's shape, then
   `CONTEXT.md` for the current snapshot. Only open `LOG.md` if you need
   detail `CONTEXT.md` doesn't have.
2. Do the requested work.
3. Append a dated, detailed entry to `LOG.md`.
4. Overwrite `CONTEXT.md` with the new current state (status/next
   step/open questions) - don't append to it.
5. If the project's structure changed (new subfolder, new major note),
   update `INDEX.md` to reflect it.

**Depends on**: `90 Meta/Templates/Project/PROJECT.md`,
`90 Meta/Templates/Project/INDEX.md`,
`90 Meta/Templates/Project/CONTEXT.md`, `90 Meta/Templates/Project/LOG.md`
