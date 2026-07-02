# Mac-Assed Mac App Skill

Codex skill for designing, auditing, and polishing desktop macOS app interfaces. It distills durable Mac UI guidance into a self-contained package: menus, windows, panels, dialogs, controls, labels, keyboard behavior, help, drag and drop, feedback, platform conventions, expressive identity, and tasteful custom UI.

The packaged skill lives in [skills/](skills/). Repo-level docs live outside that folder so the distributable skill stays small and focused.

## What It Means

A Mac-assed Mac app is a phrase from Collin Donnell for an app that is unapologetically a Mac app. It is platform-specific, honors learned Mac behaviors, uses native Mac patterns where they help, and does not try to impress users with custom not-Mac-like UI that often ends up less accessible. Native toolkit pixels are not enough; menus, windows, selection, text, pasteboard, drag and drop, state, accessibility, and user-owned data need to feel right.

## Contents

- [skills/SKILL.md](skills/SKILL.md): skill metadata, trigger description, workflow, and usage rules.
- [skills/agents/openai.yaml](skills/agents/openai.yaml): UI-facing metadata for Codex skill listings.
- [skills/references/](skills/references/): self-contained reference files loaded only when a task needs them.

## Credits

- [Accidental Tech Podcast](https://atp.fm) for the June 2026 member-special discussion of Mac-assed Mac apps, especially the guidance around native behavior, power-user affordances, state, windows, drag and drop, and evolving Mac culture.
- Additional structure and calibration were informed by Mario Guzman's [Design Resources for Mac](https://marioaguzman.github.io/design/) and Justin Wetch's [HIGAgentSkills](https://github.com/justinwetch/HIGAgentSkills). This skill remains a separate, macOS-desktop-focused reference package; it does not redistribute their source text.

## Scope

This skill is for desktop Mac app UI. Keep it focused on macOS, AppKit, SwiftUI-on-Mac, Catalyst-as-Mac, and other desktop Mac app surfaces.

Do not broaden it into iOS, watchOS, web, or generic product design guidance. When older HIG guidance conflicts with modern macOS, preserve the durable platform principle and treat old visual styling as historical unless the user explicitly asks for it.

## Development

Keep the skill package concise:

- `SKILL.md` should stay under roughly 500 lines.
- Detailed rules belong in `skills/references/`.
- Reference files should remain one level below `SKILL.md`.
- Do not put README, install guides, changelogs, source PDFs, extraction notes, or local source paths inside `skills/`.
- If `SKILL.md` changes, review `skills/agents/openai.yaml` for stale display text.
- Core rules are intentionally repeated across reference files so partially loaded references stand alone. When editing a rule, grep for its other statements so the copies do not drift.

Useful local checks:

~~~sh
rg -n "pdftotext|/Users/|\.pdf|source PDFs|original filenames" skills
rg -n '\.\.\.' skills  # UI text must use the U+2026 ellipsis character; the one hit describing the violation in hig-ui-rules.md is expected
git diff --check
~~~

If a Codex skill validator is available, find it and run it against the package:

~~~sh
find ~/.codex -name quick_validate.py -type f
python3 <path-to-quick_validate.py> skills
~~~

## Install

This repo's canonical package is [skills/](skills/). Systems that support `SKILL.md` folders can use it directly. Systems that do not support Skills can use a rule file that points agents at the package.

### Codex

Codex discovers local skills at `~/.codex/skills/<skill-name>/SKILL.md`. Install this package as:

~~~text
~/.codex/skills/mac-assed-mac-app/
~~~

Use one of these install styles.

#### Symlink For Development

Best when editing this repo often. Only use this when `~/.codex/skills/mac-assed-mac-app` does not already exist, or after moving the existing installed copy aside.

~~~sh
mkdir -p ~/.codex/skills
ln -s ~/Development/OSS/mac-assed-mac-app-skill/skills ~/.codex/skills/mac-assed-mac-app
~~~

Repo edits then show up in the installed skill path without another copy step.

#### Copy For Distribution

Best when you want the installed skill to be a snapshot:

~~~sh
mkdir -p ~/.codex/skills/mac-assed-mac-app
cp -R skills/. ~/.codex/skills/mac-assed-mac-app/
~~~

Repeat the copy after edits if you use this style.

#### Verify Install

When a local validator exists:

~~~sh
python3 <path-to-quick_validate.py> ~/.codex/skills/mac-assed-mac-app
~~~

Then restart Codex after first install, or any time the old skill behavior is still showing up.

### Claude Code

Claude Code discovers personal Skills in `~/.claude/skills/` and project Skills in `.claude/skills/`. This package can be installed the same way because it already has a root `SKILL.md`.

#### Personal Skill

Symlink while developing:

~~~sh
mkdir -p ~/.claude/skills
ln -s ~/Development/OSS/mac-assed-mac-app-skill/skills ~/.claude/skills/mac-assed-mac-app
~~~

Or copy a snapshot:

~~~sh
mkdir -p ~/.claude/skills/mac-assed-mac-app
cp -R skills/. ~/.claude/skills/mac-assed-mac-app/
~~~

#### Project Skill

From a target repo, copy the package into the project-local Claude skills directory:

~~~sh
mkdir -p .claude/skills/mac-assed-mac-app
cp -R ~/Development/OSS/mac-assed-mac-app-skill/skills/. .claude/skills/mac-assed-mac-app/
~~~

Ask Claude to list available Skills or inspect `.claude/skills/mac-assed-mac-app/SKILL.md` if it does not trigger.

Reference: [Claude Code Skills](https://docs.claude.com/en/docs/claude-code/skills).

### Cursor

Cursor does not discover `SKILL.md` folders as Skills. Use a Cursor Rule that points the agent at this package.

#### Project Rule

In the target repo, copy the package into `.cursor/rules/` and add an `.mdc` rule:

~~~sh
mkdir -p .cursor/rules/mac-assed-mac-app
cp -R ~/Development/OSS/mac-assed-mac-app-skill/skills/. .cursor/rules/mac-assed-mac-app/
~~~

Create `.cursor/rules/mac-assed-mac-app.mdc`:

~~~md
---
description: Use when designing, auditing, reviewing, or updating desktop macOS app UI.
alwaysApply: false
---

Use the Mac-Assed Mac App skill package for desktop macOS UI work.

Start by reading `.cursor/rules/mac-assed-mac-app/SKILL.md`.
Load referenced files from `.cursor/rules/mac-assed-mac-app/references/` only as needed.
Keep guidance scoped to desktop Mac apps, not iOS, web, or generic product design.
~~~

For a global Cursor setup, add a User Rule in Cursor Settings > Rules with the same instruction, pointing at this repo path if Cursor can read it. Project Rules are more reliable because the reference files live inside the target repo.

Reference: [Cursor Rules](https://docs.cursor.com/context/rules).

## License

MIT. See [LICENSE](LICENSE).
