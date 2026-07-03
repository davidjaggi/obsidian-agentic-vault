# Skill: Update Vault Structure from Upstream Template

**When to use**: The user asks to "update my vault structure", "bring the
vault up to date with the template", "sync with the template repo", or
"check what's changed upstream" - reconciling the vault's shared
framework against the public template it was created from:
https://github.com/davidjaggi/obsidian-agentic-vault

This vault (`obsidian-ai-setup`) is a personal instance of that template.
The template evolves independently (new folders, revised templates,
updated agent entry points), and this vault accumulates personal content
and, sometimes, personalized tweaks to the framework files themselves.
This skill pulls in upstream improvements without clobbering either.

**Scope** - the shared framework surface, i.e. everything that defines
*how the vault works* rather than what's *in* it:
- Top-level folder skeleton (`00 Inbox/` ... `99 Archive/` and their
  fixed subfolders) - upstream only ships `.gitkeep` placeholders here,
  so "sync" means "folder exists", never touching contents.
- `90 Meta/TEMPLATES/` (note/daily/project templates).
- `CLAUDE.md`, `AGENTS.md`, `ME.md` (agent entry points).
- `README.md` (vault structure/methodology description).
- `.obsidian/app.json` (baseline core-plugin config).

**Out of scope**:
- `90 Meta/SKILLS/` - handled by the dedicated `update-skills` skill. Run
  that skill separately (or as part of a full update, see Steps).
- Everything else: `00 Inbox/`...`60 Bases/` contents, `99 Archive/`
  contents, `90 Meta/COPILOT/`, `90 Meta/TaskNotes/`, `90 Meta/Tasks/`,
  and the rest of `.obsidian/` (personal plugin/workspace state). This is
  the user's actual vault data - never touch it.

**Steps**:
1. Fetch the upstream tree for the in-scope paths, e.g.:
   ```
   gh api repos/davidjaggi/obsidian-agentic-vault/git/trees/HEAD?recursive=true \
     --jq '.tree[] | select(.path=="README.md" or .path=="CLAUDE.md" or .path=="AGENTS.md" or .path=="ME.md" or (.path | startswith("90 Meta/TEMPLATES/")) or .path==".obsidian/app.json" or (.type=="tree" and (.path | test("^[0-9]{2} ")) and ((.path | contains("SKILLS")) | not))) | .path'
   ```
   Fetch raw content for any file with:
   ```
   gh api -H 'Accept: application/vnd.github.raw' repos/davidjaggi/obsidian-agentic-vault/contents/<path>
   ```
2. Compare against the local vault and sort into:
   - **Missing folder** - a skeleton folder upstream defines that doesn't
     exist locally yet.
   - **New/updated template** - a file under `90 Meta/TEMPLATES/` that's
     new or differs from local.
   - **Changed entry point** - `CLAUDE.md`, `AGENTS.md`, `ME.md`, or
     `README.md` differs from upstream.
   - **Changed app config** - `.obsidian/app.json` differs.
   - **Local-only** - a template or top-level folder that exists locally
     but not upstream (vault-specific addition). Never propose removing
     these.
3. Report findings as a punch list grouped by category, per the
   `vault-lint` convention. Do not silently apply anything.
4. On confirmation, apply per category:
   - Missing folders: create them (empty, or with `.gitkeep` if the vault
     tracks empty folders that way).
   - Templates: show a diff before overwriting - a locally edited
     template (e.g. a reworded daily-note prompt) should be merged by
     hand, not replaced wholesale.
   - Entry points / README: same diff-before-overwrite treatment. These
     files commonly carry vault-specific personalization (this vault's
     name, description, integrations listed) that must survive the
     merge - never do a blind overwrite.
   - App config: confirm the specific keys changing before overwriting;
     this file can carry the user's installed community plugin list.
5. For a full update, also run `update-skills` to reconcile
   `90 Meta/SKILLS/` - it follows the same fetch/diff/confirm pattern for
   that subtree.

**Depends on**: `gh` CLI installed (no auth needed, the template repo is
public). `90 Meta/SKILLS/update-skills/SKILL.md` for the skills subtree.
`90 Meta/SKILLS/vault-lint/SKILL.md` for the report-then-confirm
convention this skill follows.
