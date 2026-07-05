---
title: Trails - an associative memory layer for the vault
type: note
created: 2026-07-05
tags: [pkm, memex, zettelkasten]
---

# Trails - an associative memory layer for the vault

## Summary

Four sources, one idea. Vannevar Bush's Memex ("As We May Think") argued
the unit of value isn't the document, it's the **trail** you cut between
documents - a mind works by association, not filing, so a system should
let you link anything to anything and retrace that path later. Niklas
Luhmann's *Zettelkasten* made this literal with paper: every slip got a
unique address and lived or died by how many other slips linked to it -
an unlinked slip was functionally forgotten. Ahrens' *How to Take Smart
Notes* extracts the *process* from Luhmann's box: write permanent notes
in your own words and **link them into the network the moment they're
written**, because structure that emerges bottom-up from links beats a
folder hierarchy planned in advance. Andy Matuschek's *Evergreen Notes*
gives the quality bar for what belongs in that network: atomic,
concept-oriented (organized by idea, not by source or date), and written
to be **densely linked** and revised over time rather than filed once and
left alone.

This vault already has the container (PARA folders, `50 Notes/` for
permanent notes, MOCs tagged `moc`). What it's missing is the discipline
all four sources share: **a note that isn't linked isn't really in the
system yet** - it's just filed. `create-moc` builds hubs once a topic has
enough notes, and `example-skill` asks for "at least one related link" on
inbox triage, but nothing revisits older notes to keep the trail-weaving
going as the vault grows. That's the gap this idea closes.

## The idea: weave trails, don't just file notes

Treat linking as an ongoing maintenance activity, not a one-time step at
capture. Periodically (or after a batch of new permanent notes lands),
an agent walks `50 Notes/` looking for notes that are topically related
but not yet connected, proposes the link with a one-line rationale (the
Memex "trail" is the rationale, not just the pointer), and flags notes
that have accumulated enough inbound links to deserve promotion to a MOC
(Luhmann's structure notes).

Deliberately **not** adopted: literal Luhmann-style alphanumeric Folgezettel
IDs (`1a1`, `1a2b`, ...). Obsidian's backlink graph and MOCs already serve
the addressing/navigation function those IDs served on paper - reintroducing
them here would just be busywork with no new capability.

See `90 Meta/Skills/weave-trails/SKILL.md` for the concrete procedure.

## Links

- `90 Meta/Skills/weave-trails/SKILL.md` - the skill this note motivates
- `90 Meta/Skills/create-moc/SKILL.md` - where a well-linked note graduates to
- `90 Meta/Skills/vault-lint/SKILL.md` - health checks this complements (lint finds orphans; this skill fixes them)
