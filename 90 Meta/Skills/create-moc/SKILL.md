# Skill: Create or Update a MOC (Map of Content)

**When to use**: A topic, Area, or Project has accumulated enough notes
(roughly 5+) that they need a hub for navigation, or the user explicitly
asks for a MOC.

**Steps**:
1. Search `60 Notes/` for an existing note tagged `moc` on the topic before
   creating a new one - update it instead of duplicating. MOCs are
   identified by the `moc` tag in frontmatter, not by folder location -
   they live alongside regular notes in `60 Notes/`.
2. Create the MOC using `90 Meta/Templates/moc.md`, named after the topic
   (e.g. `60 Notes/Obsidian Setup.md`), keeping the `tags: [moc]`
   frontmatter.
3. Link out to relevant notes under `## Notes` and `## Literature` - do not
   copy content into the MOC, only link and add a one-line description per
   link.
4. Link related MOCs under `## Related MOCs` to keep the hub graph
   navigable.
5. A MOC is a hub, not an essay - resist the urge to add analysis or
   summary beyond a sentence of context per link.

**Depends on**: `90 Meta/Templates/moc.md`
