# Obsidian AI Setup

A reproducible Obsidian vault template for working with AI coding/writing
agents (Claude Code, Codex, Perplexity, Antigravity, ...) directly against
your notes.

The core idea, borrowed from Nick Milo's PKM approach: every agent points at
a single **`Skills/`** folder in the vault. Each skill is a self-contained
note (or folder) describing a repeatable task — how to write a daily note,
how to triage the inbox, how to format a literature note, etc. Agents read
this folder to learn how you want work done, so you only maintain the
instructions once and every tool benefits.

## Structure

```
.
├── Skills/             # One skill per subfolder. The shared "brain" all agents read.
├── templates/           # Obsidian note templates (Templater/core Templates plugin).
├── Inbox/               # Unsorted capture - process into Notes/.
├── Notes/               # Permanent notes.
├── .obsidian/           # Obsidian app config (community plugins, hotkeys, etc).
├── CLAUDE.md            # Entry point for Claude Code.
├── AGENTS.md            # Entry point for Codex (and other agents that read AGENTS.md).
└── .perplexity/         # Perplexity Spaces instructions.
```

## Setting up your own vault

1. Use this repo as a template (or copy its contents into your existing vault).
2. Open the folder in Obsidian and enable the community plugins you use
   (Templater, Dataview, etc. - none are bundled, install as needed).
3. Add/edit skills under `Skills/` - see `Skills/example-skill/SKILL.md` for
   the format.
4. Point each agent at the vault root:
   - **Claude Code**: reads `CLAUDE.md`, which links to `Skills/`.
   - **Codex**: reads `AGENTS.md`, which links to `Skills/`.
   - **Perplexity**: paste/sync `.perplexity/instructions.md` into your Space
     instructions.
   - **Antigravity**: point its project/context config at `Skills/` the same
     way (see `AGENTS.md` - Antigravity reads the same conventions).
5. Commit your vault to git (recommended) so every agent's edits are
   versioned and reviewable.

## Adding a new skill

```
Skills/<skill-name>/SKILL.md
```

Each `SKILL.md` should state: when to use the skill, the steps to follow,
and any templates/files it depends on. Keep skills small and single-purpose
- compose multiple skills for bigger workflows rather than writing one giant
skill.
