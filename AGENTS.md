# Vault instructions for Codex / other AGENTS.md-compatible agents

This is an Obsidian vault, not a software project. Treat markdown files as
notes, not code.

- Before doing any task, check `90 Meta/Skills/` for a matching `SKILL.md`
  and follow it.
- The vault is organized by PARA (Projects, Areas, Resources, Archive),
  numbered by actionability:
  - `00 Inbox/` - unprocessed capture. Triage per
    `90 Meta/Skills/example-skill/SKILL.md`.
  - `10 Journals/` - daily/weekly logs.
  - `20 Projects/` - active, has a deadline/outcome. Each project is
    **self-contained**: give it its own subfolder holding all of its
    notes, drafts, and files rather than scattering them across other
    top-level folders. Every project folder contains a `<project name>.md`
    note (the link target for the rest of the vault), `INDEX.md` (its
    structure), `CONTEXT.md` (short current-state snapshot, overwritten
    after every interaction), and `LOG.md` (thorough append-only history)
    - see `90 Meta/Skills/manage-project/SKILL.md`.
  - `30 Areas/` - ongoing responsibilities, no end date.
  - `40 Resources/` - topic reference material, no immediate action;
    includes a `Literature/` subfolder for book/article/podcast notes.
  - `50 Notes/` - permanent, atomic notes in your own words.
  - `60 Bases/` - Obsidian Bases / databases.
  - `99 Archive/` - inactive items, mirrored by category
    (Projects/Areas/Resources/Literature).
- Other than `20 Projects/`, do not create new subfolders - keep these
  folders flat.
- MOCs are regular notes in `50 Notes/` tagged `moc` in frontmatter, not a
  separate folder. See `90 Meta/Skills/create-moc/SKILL.md`.
- All-caps file names (e.g. `INDEX.md`, `CONTEXT.md`, `LOG.md`) mark
  load-bearing files maintained by a skill - read the matching skill
  before editing one, and don't rename or all-caps a file unless a skill
  says to.
- New permanent notes use `90 Meta/Templates/note.md`. Daily notes use
  `90 Meta/Templates/daily.md`.
- Frontmatter fields per note type are defined in
  `90 Meta/Skills/frontmatter/SKILL.md` - use it instead of inventing
  keys.
- Do not modify `.obsidian/` config unless explicitly asked.
- Keep notes in the user's own voice/words; don't pad with filler.

This file mirrors `CLAUDE.md` so any agent reading the `AGENTS.md`
convention (Codex, Antigravity, etc.) gets the same instructions.
