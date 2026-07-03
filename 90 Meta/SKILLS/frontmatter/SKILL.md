# Skill: Frontmatter Schema

**When to use**: Creating or editing the YAML frontmatter of any note in
this vault. Use these fields instead of inventing new keys, so Bases and
Dataview queries stay reliable across the vault.

## Common to every note

| Field     | Type        | Notes                                          |
|-----------|-------------|-------------------------------------------------|
| `type`    | string      | Mandatory. Fixed value per note kind - see the per-type tables below. Identifies what the note *is*, independent of `tags`. |
| `tags`    | list        | Free-form topical/cross-cutting tags. Still carries `daily`/`project`/etc. for the note kinds listed below - `type` is additive, not a replacement for those. |
| `created` | date        | `YYYY-MM-DD`, set once, never changed.          |

## Per note type

**Permanent note** (`50 Notes/`, `90 Meta/Templates/note.md`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | |
| `type` | string | `note` |
| `tags` | list | topic tags; add `moc` if this note is a MOC - MOCs are identified by the `moc` tag, not a separate `type` value |
| `created` | date | |

**Person note** (`50 Notes/`, `90 Meta/Templates/person.md`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | person's name |
| `type` | string | `person` |
| `tags` | list | topic tags |
| `created` | date | |

**Daily note** (`10 Journals/`, `90 Meta/Templates/daily.md`)
| Field | Type | Notes |
|---|---|---|
| `date` | date | used instead of `created`/`title` |
| `type` | string | `daily` |
| `tags` | list | always includes `daily` |

**Literature note** (`40 Resources/Literature/`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | |
| `type` | string | `literature` |
| `author` | string | |
| `source` | string | book / article / podcast / video |
| `url` | string | optional, omit if not applicable |
| `created` | date | date captured, not date published |
| `tags` | list | |

**Project note** (`20 Projects/<project>/<project>.md`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | matches the project/folder name |
| `type` | string | `project` |
| `created` | date | |
| `tags` | list | always includes `project` |

**Project INDEX.md**
| Field | Type | Notes |
|---|---|---|
| `title` | string | |
| `type` | string | `project-index` |
| `created` | date | |
| `status` | string | `active` \| `someday` \| `archived` |
| `tags` | list | always includes `project` |

**Project CONTEXT.md**
| Field | Type | Notes |
|---|---|---|
| `title` | string | `<project> - Context` |
| `type` | string | `project-context` |
| `updated` | date | overwritten every interaction, not `created` |
| `tags` | list | always includes `project-context` |

**Project LOG.md**
| Field | Type | Notes |
|---|---|---|
| `title` | string | `<project> - Log` |
| `type` | string | `project-log` |
| `created` | date | set once |
| `tags` | list | always includes `project-log` |

**Area note** (`30 Areas/`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | |
| `type` | string | `area` |
| `created` | date | |
| `tags` | list | |

**Resource note** (`40 Resources/`, excluding `Literature/`)
| Field | Type | Notes |
|---|---|---|
| `title` | string | |
| `type` | string | `resource` |
| `created` | date | |
| `tags` | list | |

Do not add a `status` field outside of Project `INDEX.md` - actionability
in this vault is expressed by which numbered folder a note lives in, not
by a status property.
