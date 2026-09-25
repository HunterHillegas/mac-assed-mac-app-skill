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

- Brent Simmons's [That About Wraps It Up for Stock Mac UI](https://inessential.com/2026/09/22/that-about-wraps-it-up-for.html) informs the stock-versus-custom UI decision guidance.
- [Accidental Tech Podcast](https://atp.fm) for the June 2026 member-special discussion of Mac-assed Mac apps, especially the guidance around native behavior, power-user affordances, state, windows, drag and drop, and evolving Mac culture.
- Paulo Andrade's [Using SwiftUI to Build a Mac-assed App in 2026](https://pfandrade.me/blog/mac-assed-swiftui-app/) and [A WWDC 26 Update on Building a Mac-assed App with SwiftUI](https://pfandrade.me/blog/swiftui-mac-assed-wwdc26-update/) for concrete SwiftUI guidance on selection prominence, context-menu targeting, drag-session lifecycle, keyboard intent, and toolbar limitations.
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
- Keep detailed rules and API advice in their owning reference; other files can summarize the principle and link to it. When editing a shared rule, search for other statements so they do not drift.
- Route narrow tasks directly to the relevant reference. Use the rulebook for broad audits; do not make every task load the whole package.
- Distinguish historical calibration, current Apple guidance, editorial judgment, and verified app behavior. Confirm version-sensitive API claims against the target SDK or official documentation.

Useful local checks:

~~~sh
rg -n "pdftotext|/Users/|\.pdf|source PDFs|original filenames" skills
rg -n '\.\.\.' skills  # UI text must use the U+2026 ellipsis character; the one hit describing the violation in hig-ui-rules.md is expected
git diff --check
~~~

If a Codex skill validator is available, find it and run it against the package:

~~~sh
rg --files --hidden ~/.codex/skills ~/.agents/skills -g quick_validate.py
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

Cursor supports `SKILL.md` packages in `.cursor/skills/` for a project or `~/.cursor/skills/` for personal use. See [Cursor Agent Skills](https://cursor.com/docs/skills).

#### Project Skill

From the target repo, copy the package into the project skill directory:

~~~sh
mkdir -p .cursor/skills/mac-assed-mac-app
cp -R ~/Development/OSS/mac-assed-mac-app-skill/skills/. .cursor/skills/mac-assed-mac-app/
~~~

#### Personal Skill

~~~sh
mkdir -p ~/.cursor/skills/mac-assed-mac-app
cp -R skills/. ~/.cursor/skills/mac-assed-mac-app/
~~~

Run the personal-copy commands from this repo. Keep the reference files with `SKILL.md`; a rule that only duplicates the entrypoint loses the bundled guidance.

## License

MIT. See [LICENSE](LICENSE).
