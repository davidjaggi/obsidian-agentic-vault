# Skill: Weave Trails

**When to use**: Periodically as the vault grows, or after a batch of new
permanent notes has landed in `50 Notes/` - a maintenance pass to
strengthen the associative link network, not to file or triage notes.
Complements `vault-lint`, which finds orphan notes but doesn't fix them.

**Rationale**: `90 Meta/Skills/../../50 Notes/Trails - an associative
memory layer for the vault.md` - a note that isn't linked to anything
isn't really part of the system yet, it's just filed.

**Steps**:
1. List notes in `50 Notes/` (`type: note` or `type: person`) that have
   fewer than 2 outgoing `[[links]]` or zero backlinks - these are
   isolated, disconnected from any trail.
2. For each one, read it and scan `50 Notes/` (and any relevant MOCs) for
   notes covering a related idea.
3. Propose 1-3 candidate links per note, each with a one-line rationale
   (the trail, not just the pointer - e.g. "relates to X because both
   describe..."). Add confirmed links under the note's `## Links`
   heading. Don't silently rewrite the rest of the body.
4. If a note has picked up 3+ inbound links from otherwise-unrelated
   notes, it's becoming a hub - suggest promoting it to a MOC via
   `create-moc` instead of letting it grow into an essay on its own.
5. Optionally mark maturity in `tags` (not a new frontmatter field, per
   `frontmatter`): `seedling` (captured, unlinked), `budding` (linked but
   still close to the source wording), `evergreen` (atomic, in your own
   words, densely linked). Skip this if the user doesn't want the extra
   tags.
6. Report what was linked/promoted/tagged as a short punch list - don't
   act on ambiguous matches without confirming first.

**Depends on**: `90 Meta/Skills/frontmatter/SKILL.md`,
`90 Meta/Skills/create-moc/SKILL.md`,
`90 Meta/Skills/vault-lint/SKILL.md`,
`50 Notes/Trails - an associative memory layer for the vault.md`
