# Obsidian AI Setup

A reproducible Obsidian vault template for working with AI coding/writing
agents (Claude Code, Codex, Perplexity, Antigravity, ...) directly against
your notes.

The core idea, borrowed from Nick Milo's PKM approach: every agent points at
a single **`90 Meta/Skills/`** folder in the vault. Each skill is a
self-contained note (or folder) describing a repeatable task — how to write
a daily note, how to triage the inbox, how to format a literature note,
etc. Agents read this folder to learn how you want work done, so you only
maintain the instructions once and every tool benefits.

The folder layout follows Tiago Forte's **PARA** method (Projects, Areas,
Resources, Archive) from Building a Second Brain, numbered by
actionability. Folders are kept flat — `20 Projects/` is the only place
that gets per-item subfolders, since a project is self-contained (notes,
drafts, and files for one project live together). MOCs (Maps of Content)
are plain notes tagged `moc`, not a separate folder.

## Structure

```
.
├── 00 Inbox/            # Unprocessed capture - triage out of here daily/weekly.
├── 10 Journals/         # Daily/weekly logs.
├── 20 Projects/         # Active, has a deadline/outcome. Self-contained per project
│   └── <project>/       # subfolder - the only folder that nests further.
│       ├── <project>.md # link target for the rest of the vault.
│       ├── INDEX.md     # project structure - see manage-project skill.
│       ├── CONTEXT.md   # short current-state snapshot, overwritten each time.
│       └── LOG.md       # thorough append-only history.
├── 30 Areas/            # Ongoing responsibilities, no end date.
├── 40 Resources/        # Topic reference material, no immediate action.
│   └── Literature/      # Literature source notes from ZotFlow.
├── 50 Notes/            # Permanent, atomic notes - includes MOCs (tag: moc).
├── 60 Bases/            # Obsidian Bases / databases.
├── 90 Meta/
│   ├── Skills/          # One skill per subfolder. The shared "brain" all agents read.
│   └── Templates/       # Obsidian note templates (Templater/core Templates plugin).
│       └── Project/     # Templates for <project>.md, INDEX.md, CONTEXT.md, LOG.md.
├── 99 Archive/          # Inactive items, mirrored by category.
│   ├── Projects/
│   ├── Areas/
│   ├── Resources/
│   └── Literature/
├── .obsidian/           # Obsidian app config (community plugins, hotkeys, etc).
├── CLAUDE.md            # Entry point for Claude Code.
├── AGENTS.md            # Entry point for Codex (and other agents that read AGENTS.md).
└── .perplexity/         # Perplexity Spaces instructions.
```

## Community plugins used

None are bundled in this repo (install via Obsidian's Community Plugins
browser) - this vault is set up with:

- **Copilot** - AI chat/assistant against vault content.
- **[Tasks](https://publish.obsidian.md/tasks/Introduction)** - task
  management via `#task` in note bodies.
- **[TaskNotes](https://tasknotes.dev/)** - note-based task/calendar
  management.
- **[ZotFlow](https://zotflow.peterduan.dev/)** - Zotero integration for
  literature notes.
- **Templater** - powers the templates under `90 Meta/Templates/`.

## Setting up your own vault

1. Use this repo as a template (or copy its contents into your existing vault).
2. Open the folder in Obsidian and enable the community plugins you use
   (see Community plugins used above - none are bundled, install as needed).
3. Add/edit skills under `90 Meta/Skills/` - see
   `90 Meta/Skills/example-skill/SKILL.md` for the format.
4. Point each agent at the vault root:
   - **Claude Code**: reads `CLAUDE.md`, which links to `90 Meta/Skills/`.
   - **Codex**: reads `AGENTS.md`, which links to `90 Meta/Skills/`.
   - **Perplexity**: paste/sync `.perplexity/instructions.md` into your Space
     instructions.
   - **Antigravity**: point its project/context config at
     `90 Meta/Skills/` the same way (see `AGENTS.md` - Antigravity reads
     the same conventions).
5. Commit your vault to git (recommended) so every agent's edits are
   versioned and reviewable.

## Adding a new skill

```
90 Meta/Skills/<skill-name>/SKILL.md
```

Each `SKILL.md` should state: when to use the skill, the steps to follow,
and any templates/files it depends on (templates live under
`90 Meta/Templates/`). Keep skills small and single-purpose - compose
multiple skills for bigger workflows rather than writing one giant skill.

## Bundled skills

- `example-skill/` - inbox triage.
- `create-moc/` - creating/updating Maps of Content.
- `manage-project/` - the project-note/`INDEX.md`/`CONTEXT.md`/`LOG.md`
  convention.
- `frontmatter/` - canonical YAML frontmatter fields per note type.
- `obsidian-markdown/`, `obsidian-bases/`, `obsidian-cli/`, `json-canvas/`,
  `defuddle/` - vendored from
  [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) (MIT,
  see `90 Meta/Skills/THIRD_PARTY_NOTICES.md`) for Obsidian-flavored
  Markdown, Bases, the Obsidian CLI, JSON Canvas, and web content
  extraction.
