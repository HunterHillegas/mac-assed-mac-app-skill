# Mac-Assed Mac App Skill

Codex skill for designing, auditing, and polishing desktop macOS app interfaces. It distills durable Mac UI guidance into a self-contained package: menus, windows, panels, dialogs, controls, labels, keyboard behavior, help, drag and drop, feedback, platform conventions, expressive identity, and tasteful custom UI.

The packaged skill lives in [skills/](skills/). Repo-level docs live outside that folder so the distributable skill stays small and focused.

## What It Means

A Mac-assed Mac app is a phrase from Collin Donnell for an app that is unapologetically a Mac app. It is platform-specific, uses native Mac patterns, and does not try to impress users with custom not-Mac-like UI that often ends up less accessible.

## Contents

- [skills/SKILL.md](skills/SKILL.md): skill metadata, trigger description, workflow, and usage rules.
- [skills/agents/openai.yaml](skills/agents/openai.yaml): UI-facing metadata for Codex skill listings.
- [skills/references/](skills/references/): self-contained reference files loaded only when a task needs them.

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

Useful local checks:

~~~sh
rg -n "pdftotext|/Users/|\.pdf|source PDFs|original filenames" skills
git diff --check
~~~

If a Codex skill validator is available, find it and run it against the package:

~~~sh
find ~/.codex -name quick_validate.py -type f
python3 <path-to-quick_validate.py> skills
~~~

## Install

Codex discovers local skills at `~/.codex/skills/<skill-name>/SKILL.md`. This repo's canonical package is [skills/](skills/), which should be installed as:

~~~text
~/.codex/skills/mac-assed-mac-app/
~~~

Use one of these install styles.

### Symlink For Development

Best when editing this repo often. Only use this when `~/.codex/skills/mac-assed-mac-app` does not already exist, or after moving the existing installed copy aside.

~~~sh
mkdir -p ~/.codex/skills
ln -s ~/Development/OSS/mac-assed-mac-app-skill/skills ~/.codex/skills/mac-assed-mac-app
~~~

Repo edits then show up in the installed skill path without another copy step.

### Copy For Distribution

Best when you want the installed skill to be a snapshot:

~~~sh
mkdir -p ~/.codex/skills/mac-assed-mac-app
cp -R skills/. ~/.codex/skills/mac-assed-mac-app/
~~~

Repeat the copy after edits if you use this style.

### Verify Install

When a local validator exists:

~~~sh
python3 <path-to-quick_validate.py> ~/.codex/skills/mac-assed-mac-app
~~~

Then restart Codex after first install, or any time the old skill behavior is still showing up.

## License

MIT. See [LICENSE](LICENSE).
