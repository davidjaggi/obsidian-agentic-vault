# Skill: Frontmatter Schema

**When to use**: Creating or editing the YAML frontmatter of any note in
this vault. Use these fields instead of inventing new keys, so Bases and
Dataview queries stay reliable across the vault.

## Common to every note

| Field     | Type        | Notes                                          |
|-----------|-------------|-------------------------------------------------|
| `tags`    | list        | At minimum the note's type tag (see below).     |
| `created` | date        | `YYYY-MM-DD`, set once, never changed.          |

## Per note type

**Permanent note** (`60 Notes/`, `90 Meta/Templates/note.md`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | |
| `tags` | list | topic tags; add `moc` if this note is a MOC |
| `created` | date | |

**Daily note** (`10 Journals/`, `90 Meta/Templates/daily.md`)
| Field | Type | Notes |
|---|---|---|
| `date` | date | used instead of `created`/`title` |
| `tags` | list | always includes `daily` |

**Literature note** (`50 Literature/`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | |
| `author` | string | |
| `source` | string | book / article / podcast / video |
| `url` | string | optional, omit if not applicable |
| `created` | date | date captured, not date published |
| `tags` | list | |

**Project note** (`20 Projects/<project>/<project>.md`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | matches the project/folder name |
| `created` | date | |
| `tags` | list | always includes `project` |

**Project INDEX.md**
| Field | Type | Notes |
|---|---|---|
| `title` | string | |
| `created` | date | |
| `status` | string | `active` \| `someday` \| `archived` |
| `tags` | list | always includes `project` |

**Project CONTEXT.md**
| Field | Type | Notes |
|---|---|---|
| `title` | string | `<project> - Context` |
| `updated` | date | overwritten every interaction, not `created` |
| `tags` | list | always includes `project-context` |

**Project LOG.md**
| Field | Type | Notes |
|---|---|---|
| `title` | string | `<project> - Log` |
| `created` | date | set once |
| `tags` | list | always includes `project-log` |

**Area / Resource note** (`30 Areas/`, `40 Resources/`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | |
| `created` | date | |
| `tags` | list | |

Do not add a `status` field outside of Project `INDEX.md` - actionability
in this vault is expressed by which numbered folder a note lives in, not
by a status property.
