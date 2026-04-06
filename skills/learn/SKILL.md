---
name: learn
description: Capture session learnings into CLAUDE.md, memory files, second brain wiki, and sync to the claude-config GitHub repo
user_invocable: true
---

# /learn — Capture Session Learnings

Review the current conversation and persist learnings across three layers, then sync to GitHub.

## Steps

### 1. Identify Learnings

Scan the conversation for:
- **Corrections** the user made ("no, not that", "don't do X", "that's wrong")
- **Confirmed approaches** that worked ("yes exactly", "perfect", accepted without pushback)
- **New gotchas** discovered (bugs, surprising behavior, things that broke)
- **Architecture/design changes** made during the session
- **User preferences** revealed (workflow, communication style, tools)
- **Project context** (deadlines, stakeholders, constraints, external systems)

### 2. Update Project CLAUDE.md

If the current project has a `CLAUDE.md` in the repo root, update it with:
- New gotchas or "IMPORTANT" warnings discovered
- Architecture changes (new files, changed patterns, updated data flow)
- New key commands or environment variables
- Updated descriptions of existing sections if they're now stale

Do NOT add information that's already there or that can be derived from code.

### 3. Create/Update Memory Files

Save learnings to `~/.claude/projects/<project-key>/memory/`:
- **feedback** memories for corrections and confirmed approaches
- **user** memories for user preferences and profile info
- **project** memories for project context (convert relative dates to absolute)
- **reference** memories for external system pointers

Check existing memories first — update rather than duplicate. Update `MEMORY.md` index.

### 4. Second Brain Wiki Check

Scan the session for professional knowledge worth persisting beyond this project:
- New concepts, frameworks, or mental models encountered
- Tool/technique insights that apply broadly (not project-specific config)
- Architectural patterns worth remembering across projects
- Surprising findings or non-obvious lessons learned

If anything qualifies, update `~/second-brain/wiki/`:
- Create or update pages in `entities/`, `concepts/`, `sources/`, or `synthesis/`
- Add `[[wikilinks]]` cross-references to related existing pages
- Update `wiki/index.md` with new/changed pages
- Append entry to `wiki/log.md`
- Follow the schema in `~/second-brain/CLAUDE.md`

Then commit:
```bash
cd ~/second-brain && git add -A && git commit -m "learn: <brief description of what was added>"
```

Most sessions will have nothing wiki-worthy — skip this step if so. Project-specific gotchas belong in CLAUDE.md and memory, not the wiki.

### 5. Sync to claude-config Repo

The global config repo lives at `/Users/edevard/claude-config` (GitHub: `edevardHvide/claude-config`).

Run this sync:

```bash
# Sync settings
cp ~/.claude/settings.json /Users/edevard/claude-config/settings/
cp ~/.claude/settings.local.json /Users/edevard/claude-config/settings/ 2>/dev/null

# Sync global skills
rsync -a --delete ~/.claude/skills/ /Users/edevard/claude-config/skills/

# Sync all project memories
for dir in ~/.claude/projects/*/memory; do
  projname=$(basename $(dirname "$dir"))
  mkdir -p "/Users/edevard/claude-config/memory/$projname"
  rsync -a "$dir/" "/Users/edevard/claude-config/memory/$projname/"
done
```

### 6. Commit and Push

```bash
cd /Users/edevard/claude-config
git add -A
git commit -m "Sync learnings from <project-name> session"
git push origin main
```

Also commit CLAUDE.md changes in the current project repo if modified.

## Important

- Do NOT save ephemeral task details (current debugging state, in-progress work)
- Do NOT duplicate information already in code, git history, or existing memories
- Convert relative dates to absolute dates in project memories
- Keep MEMORY.md index concise (under 200 lines)
- If a memory already exists on the same topic, UPDATE it rather than creating a new one
