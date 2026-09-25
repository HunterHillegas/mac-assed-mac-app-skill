---
name: mac-assed-mac-app
description: "Design, audit, and improve desktop macOS app UI: menus, windows, keyboard and selection behavior, native controls, UI text, and expressive identity. Use for AppKit, SwiftUI-on-Mac, Catalyst, or other Mac app surfaces; excludes iOS-only and web-only UI work."
---

# Mac-Assed Mac App

## Purpose

Make desktop macOS interfaces feel at home on the Mac: menus, windows, keyboard, selection, and hierarchy first; typography, iconography, motion, and custom controls second. Native-looking pixels do not prove native behavior.

Stay within the requested surface and mode. An audit produces findings; an implementation request authorizes relevant edits. Preserve the user's toolkit, deployment target, product intent, and exact supplied copy unless changing them is part of the request. A small label fix does not require redesigning the app.

## Reference Routing

Read the references that match the task; there is no mandatory bundle. For a broad audit, start with the rulebook and add depth where evidence warrants it. The bundled guidance is self-contained; original source documents are not a prerequisite.

| Task | Read |
| --- | --- |
| Broad audit or common Mac violations | [hig-ui-rules.md](references/hig-ui-rules.md) |
| App shape, task model, workflow, user control | [mac-ui-principles.md](references/mac-ui-principles.md) |
| Menus, commands, windows, controls, selection, drag, Services | [mac-ui-elements.md](references/mac-ui-elements.md) |
| Geometry, toolbar, sidebar, inspector, panel, preferences/settings, dense forms | [mac-layout-structure.md](references/mac-layout-structure.md) |
| Labels, capitalization, ellipses, alerts, buttons, menu or help copy | [mac-ui-text.md](references/mac-ui-text.md) |
| Branding, stock versus custom UI, iconography, personality, “does this feel Mac-assed?” | [mac-assedness.md](references/mac-assedness.md) |
| SwiftUI focus, selection, context menus, drag lifecycle, keyboard handling, toolbar overflow | [swiftui-mac-behavior.md](references/swiftui-mac-behavior.md) |
| Liquid Glass, OS-specific visuals, accessibility, document/undo architecture, historical conflicts | [current-macos-design.md](references/current-macos-design.md) |
| Visual calibration using production examples | [production-app-examples.md](references/production-app-examples.md) |
| Runtime checks and audit evidence | [mac-ui-verification.md](references/mac-ui-verification.md) |
| Topic coverage or attribution | [source-index.md](references/source-index.md) |

## Resolve Conflicts

- Check the app's supported macOS versions and SDK before prescribing an API or visual treatment. Verify availability in the installed SDK or current Apple documentation; a recent article or an OS version alone is not sufficient.
- Current Mac-specific Apple documentation and observed behavior on the supported OS guide implementation. Historical HIG material supplies durable principles, not current pixel metrics or API guarantees.
- Treat third-party critiques and this skill's taste judgments as recommendations. Explain a departure from current Apple styling through a concrete gain in legibility, behavior, or task fit.
- When only screenshots or source code are available, distinguish visible findings and likely risks from behavior that remains untested.

## Workflow

1. Inspect the relevant UI, code, or supplied images. Establish the app type, content model, affected windows/panes, and supported OS versions from available evidence.
2. Trace the user's task: object → selection/focus → command → result → recovery. Identify which pane or window owns each action.
3. Load the relevant references. Prioritize broken behavior, inaccessible actions, and unclear ownership before cosmetic polish.
4. For requested edits, make the smallest coherent improvement. Prefer system behavior and existing app patterns; use custom UI where its benefit justifies maintaining the native interaction contract.
5. Verify the changed surface with the real app when available. Choose relevant checks from [mac-ui-verification.md](references/mac-ui-verification.md); a build or screenshot alone cannot validate keyboard, drag, or accessibility behavior.
6. Report concrete changes or prioritized findings, their user impact, and verification limits. Scale the response to the task; do not pad a copy edit with an app-wide audit.

## Design Priorities

- Keep content and its hierarchy primary. Sidebars navigate; inspectors describe selection; toolbars expose frequent window commands; menus provide the command map.
- Route commands to the intended window, pane, selection, or text editor. Share command semantics across toolbar, menu, shortcut, and contextual paths; derive each path's target and availability from its actual context.
- Reward natural Mac actions: multi-select, copy, paste, drag, reveal, open, undo, resize, and restore meaningful state where the model supports them.
- Keep keyboard, pointer, text editing, accessibility, and localization intact. Avoid essential actions available only through hover, gestures, or unlabeled icons.
- Make exploration recoverable: undo for edits, cancel for interruptible work, confirmation for meaningful risk. A visible result is often sufficient feedback; routine actions do not each need a toast or alert.
- Allow personality through typography, icons, color, motion, and justified custom controls without obscuring focus, selection, hierarchy, or actionability.
- Add windows, customization, system integration, and settings where the task benefits. A menu bar utility, document editor, and single-purpose app need different amounts of UI.
- Use concrete user-facing language. File names and locations belong where users need to identify their work; internal diagnostics belong only where actionable. Follow the text reference for capitalization and command ellipses.
