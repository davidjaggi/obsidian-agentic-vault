# Skill: Lint / Health-Check the Vault

**When to use**: The user asks to "lint the vault", "check vault health",
or "clean up notes" - a maintenance pass across the whole vault, not a
single note. Run periodically as the vault grows, since these problems
accumulate silently otherwise.

**Checks to run**:
1. **Missing/invalid frontmatter** - every note has a `type` field with
   the value its folder/kind expects, per
   `90 Meta/Skills/frontmatter/SKILL.md`.
2. **Broken links** - `[[wikilinks]]` that don't resolve to any file in
   the vault.
3. **Orphan notes** - notes in `50 Notes/` or `40 Resources/` with no
   incoming links from anywhere else in the vault.
4. **Stale project context** - a `20 Projects/*/LOG.md` with entries
   dated after its sibling `CONTEXT.md`'s `updated` field means
   `CONTEXT.md` wasn't refreshed after the last interaction, per
   `manage-project`.
5. **Unsynthesized literature** - notes in `40 Resources/Literature/`
   with no permanent note in `50 Notes/` linking to them - captured but
   never turned into a distilled idea.
6. **Duplicate MOCs** - more than one note tagged `moc` covering
   near-identical topics.

**Steps**:
1. Glob all `.md` files in the vault, excluding `.obsidian/` and
   `90 Meta/Templates/`.
2. Run the checks above with Grep (frontmatter fields, `[[...]]`
   patterns) and cross-reference file names/links between them.
3. Report findings as a punch list grouped by check. Do not silently fix
   anything - an orphan note or a stale project can be intentional (an
   idea parked on purpose).
4. Only edit, relink, or delete something once the user confirms which
   findings to act on.

**Depends on**: `90 Meta/Skills/frontmatter/SKILL.md`,
`90 Meta/Skills/manage-project/SKILL.md`
