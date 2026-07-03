# Skill: Update Skills from Upstream Template

**When to use**: The user asks to "update the skills", "sync skills from
the template", "check for new skills upstream", or "pull the latest
skills" - refreshing `90 Meta/SKILLS/` against the public template repo
this vault was created from:
https://github.com/davidjaggi/obsidian-agentic-vault

This vault's own skills can drift from the template over time (upstream
gains new skills, or improves existing ones) and vice versa (this vault
may have local, vault-specific skills that don't exist upstream). This
skill reconciles the two without silently clobbering either side.

**Scope**: Only `90 Meta/SKILLS/` (including
`90 Meta/SKILLS/THIRD_PARTY_NOTICES.md`). Do not touch any other part of
the vault (personal content, `90 Meta/TEMPLATES/`, `CLAUDE.md`,
`AGENTS.md`, root files, etc.) - those are out of scope for this skill.

**Steps**:
1. Fetch the upstream skills tree. Prefer the `gh` CLI over a full clone:
   ```
   gh api repos/davidjaggi/obsidian-agentic-vault/git/trees/HEAD?recursive=true \
     --jq '.tree[] | select(.path | startswith("90 Meta/SKILLS/")) | .path'
   ```
   Fetch each file's raw content with:
   ```
   gh api repos/davidjaggi/obsidian-agentic-vault/contents/<path> --jq '.content' | base64 -d
   ```
   (or `gh api -H 'Accept: application/vnd.github.raw' repos/.../contents/<path>`).
2. Diff the upstream file list against the local `90 Meta/SKILLS/` tree and
   sort every path into one of:
   - **New upstream skill** - a folder/file that exists upstream but not
     locally.
   - **Updated upstream skill** - exists in both, content differs.
   - **Local-only skill** - exists locally but not upstream (a
     vault-specific skill the user built here). Never propose deleting
     these.
   - **Unchanged** - identical content, skip.
3. Report the findings as a punch list grouped by category (new /
   updated / local-only), same as `vault-lint`. Do not silently apply
   anything.
4. Once the user confirms which items to pull:
   - New skills: create the folder and write the file(s) as-is.
   - Updated skills: show a diff of what would change before overwriting,
     in case the local copy has vault-specific edits worth preserving
     (e.g. a path or plugin name tweaked for this vault). If it does,
     merge by hand instead of overwriting wholesale.
   - Local-only skills: leave untouched unless the user explicitly asks
     to remove or upstream them.
5. After applying updates, verify every skill folder still has a
   `SKILL.md` and that any `references/` subfolders came across intact.

**Depends on**: `gh` CLI authenticated against GitHub (no auth needed for
this public repo, but `gh` must be installed).
