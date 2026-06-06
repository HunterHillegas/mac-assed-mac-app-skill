# Repository Instructions

## Scope

- This repo packages the `mac-assed-mac-app` Codex skill.
- The distributable skill is the `skills/` directory.
- Repo docs, process notes, and maintenance instructions stay at the repo root, not inside `skills/`.

## Skill Rules

- Keep the skill tightly scoped to desktop macOS app UI.
- Ignore iOS-only, watchOS-only, web-only, and generic product-design advice unless it directly affects a Mac app.
- Preserve the distinction between Mac structure and expressive identity: menus, windows, keyboard, selection, hierarchy first; typography, iconography, motion, custom controls second.
- Do not reintroduce source PDFs, source extraction artifacts, original filenames, or local source paths into the distributable package.
- Keep `skills/SKILL.md` concise and under roughly 500 lines.
- Put detailed guidance in one-level `skills/references/*.md` files and link them directly from `skills/SKILL.md`.
- Update `skills/agents/openai.yaml` when the skill name, description, or default usage changes.

## Editing

- Prefer small, reviewable doc edits.
- If a function, script, or documented workflow changes, update nearby comments and docs in the same change.
- Do not change non-test content only to satisfy a test; adjust the test or stub when that is the real issue.
- Treat unexpected worktree changes as user or other-agent work. Inspect before editing overlapping files; do not revert them without explicit approval.

## Verification

Before handoff, run the useful gate for the change:

~~~sh
rg -n "pdftotext|/Users/|\.pdf|source PDFs|original filenames" skills
git diff --check
~~~

If a local skill validator exists, run it against `skills/` as well. If unavailable, say so.

## Install Sync

Installing is separate from editing this repo. When asked to install or refresh the skill, copy `skills/.` into:

~~~text
~/.codex/skills/mac-assed-mac-app/
~~~

Validate the installed copy when possible. If Codex still uses stale behavior after copying, restart Codex.

## Git

- Safe commands by default: `git status`, `git diff`, `git log`.
- Branch changes, pushes, destructive operations, and amend commits require explicit user consent.
- Use Conventional Commits when committing.
