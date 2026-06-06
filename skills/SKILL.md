---
name: mac-assed-mac-app
description: "macOS app UI guidance distilled from historical Apple Human Interface Guidelines and Mac-assed design analysis. Use when designing, auditing, reviewing, or updating SwiftUI, AppKit, Catalyst, or other desktop Mac app interfaces to feel like a proper Mac app: menus, windows, panels, dialogs, controls, labels, keyboard shortcuts, icons, preferences, help, drag and drop, feedback, platform conventions, expressive identity, and tasteful custom UI. Ignore iOS-only advice."
---

# Mac-Assed Mac App

## Purpose

Use this skill to make macOS app interfaces feel native, intentional, and Mac-like. The bundled references are self-contained derived guidance; do not require or look for the original source documents.

## References

Load only what the task needs:

- [references/hig-ui-rules.md](references/hig-ui-rules.md): compact rulebook and common violations.
- [references/mac-ui-principles.md](references/mac-ui-principles.md): mental model, workflow, feedback, trust, and Mac app shape.
- [references/mac-ui-elements.md](references/mac-ui-elements.md): menus, windows, toolbars, sidebars, panels, dialogs, alerts, and controls.
- [references/mac-ui-text.md](references/mac-ui-text.md): labels, capitalization, ellipses, punctuation, terminology, and alert copy.
- [references/mac-assedness.md](references/mac-assedness.md): platform identity, expressive software, custom UI judgment, modern macOS tradeoffs, and examples.
- [references/production-app-examples.md](references/production-app-examples.md): production screenshots that demonstrate Mac-assed structure and identity.
- [references/source-index.md](references/source-index.md): self-contained map of the derived topics.

## Workflow

1. Inspect the UI before editing: app type, primary documents/content, main windows, menus, toolbars, sidebars, dialogs, preferences, alerts, and keyboard shortcuts.
2. Identify the user's task model: noun-first objects, core workflows, destructive actions, frequent commands, and novice/expert paths.
3. Read `references/hig-ui-rules.md` and any task-specific reference. Map only the relevant rules to the current UI.
4. Fix root causes in the app's UI structure before cosmetic polish. Prefer system controls, real macOS affordances, and existing app patterns.
5. Preserve exact user-provided copy. Otherwise rewrite UI text to be user-centric, concrete, concise, and Mac-style.
6. Verify with the real app when possible: build, run, inspect menus/windows, use screenshots, exercise keyboard navigation, and check alerts/dialogs.
7. Report changes as UI behavior and platform fit, not as generic visual cleanup.

## Design Priorities

- Reflect the user's mental model. Layout, window hierarchy, menus, and labels should match how users already understand the task.
- Keep users in control. Avoid surprise automation, irreversible actions without warning, or app-management chores.
- Use standard macOS elements correctly before inventing custom UI.
- Protect structural Mac conventions while allowing personality in the expressive layer: visual language, typography, icons, motion, and carefully bounded custom controls.
- Make primary content the focus. Chrome should support scanning and action, not compete with the work.
- Keep commands discoverable through the menu bar even when toolbar buttons or contextual actions exist.
- Use feedback for every user-initiated operation. Show progress for long work and explain failures in user language.
- Make exploration safe: undo where possible, cancel where sensible, confirmation only for meaningful risk.
- Support both mouse/trackpad and keyboard use. Add shortcuts for frequent commands, not every command.
- Treat accessibility, localization, help, printing, drag and drop, and preferences as normal Mac app surfaces, not extras.

## Implementation Biases

- Prefer native SwiftUI/AppKit controls and platform behavior over web-style custom widgets.
- Prefer sidebars, split views, outline/list/table views, toolbars, inspectors, popovers, sheets, and panels where they match the task.
- Prefer document-modal sheets for document/window-specific decisions. Use app-modal alerts sparingly.
- Prefer Preferences/Settings for durable user choices; avoid using preferences as a dumping ground for core workflow controls.
- Prefer direct manipulation for visible objects: drag, reorder, resize, select, reveal, and edit in place when it matches the model.
- Prefer standard menu order, names, and keyboard equivalents. Keep toolbar/context menu commands backed by menu items.
- Prefer sentence-style explanatory text and title-style command labels, following the text rules in the reference.
- Prefer custom UI only when it clarifies the app's purpose, improves the interaction, or gives the app a coherent voice without making users relearn Mac basics.

## Do Not

- Do not import iOS patterns just because the code is SwiftUI. A Mac app still needs menus, keyboard navigation, window behavior, resizing, and pointer-friendly density.
- Do not hide essential commands only in icons, gestures, hover states, contextual menus, or empty states.
- Do not use custom controls when a standard control exists and expresses the behavior.
- Do not make alerts do ordinary workflow. Reserve them for errors, confirmation, and important state.
- Do not use three periods for command ellipses; use the U+2026 ellipsis character when an action needs more input before it can execute.
- Do not use internal implementation terms, API names, file-system paths, or developer jargon in visible UI unless the app is explicitly for that audience.
- Do not add branding where it fights native app conventions. Brand through icon craft, tone, layout restraint, and domain-specific detail.
- Do not confuse being Mac-assed with copying Apple's newest visual style. Serve the platform's learned behaviors first.

## Output Shape

When auditing or updating a UI, return:

- Key mismatches with macOS conventions.
- Concrete UI changes made or recommended.
- Any tradeoffs where older HIG guidance conflicts with modern macOS behavior.
- Verification performed, or what blocked verification.
