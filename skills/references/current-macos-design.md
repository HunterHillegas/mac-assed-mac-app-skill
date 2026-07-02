# Current macOS Design Sources

Use this when a task depends on current macOS behavior, macOS 26+ visual language, AppKit specifics, accessibility, icons, document architecture, undo, or conflicts between older HIG guidance and current Apple design direction.

## Source Map

- Apple HIG current component pages: menus, windows, toolbars, sidebars, alerts, drag and drop, SF Symbols, and app icons.
- WWDC25, Build an AppKit app with the new design: AppKit adoption for Liquid Glass, toolbars, sidebars, inspectors, scroll edge effects, controls, menus, and custom glass UI.
- WWDC25, Get to know the new design system: system-wide shape, hierarchy, grouping, continuity, and Liquid Glass as a functional layer.
- WWDC20, Adopt the new look of macOS: Big Sur-era bridge from older Mac chrome to full-height sidebars, unified toolbars, safe areas, and SF Symbols.
- WWDC25, Make your Mac app more accessible to everyone: Mac VoiceOver structure, containers, rotors, accessibility focus, and hover/gesture fallbacks.
- AppKit document, undo, text, and pasteboard docs: document lifecycle, undo manager behavior, text-system expectations, and data interchange.
- Apple Design Resources and Icon Composer: current macOS UI kits, SF Symbols, system fonts, app icon templates, layered icons, and appearance modes.
- Tahoe icon critiques from Tonsky, Jim Nielsen, and Rogue Amoeba: useful calibration against visual noise, especially menu icons.

## Current macOS 26+ Judgment

- Treat Liquid Glass as a top-level functional layer for navigation and important controls, not as a background texture.
- Let hierarchy come from structure, layout, grouping, and ownership before material effects.
- Keep Mac density. Mini, small, and medium controls remain appropriate for compact inspectors, dense tables, utility panes, and professional workflows.
- Use large or extra-large controls only for the primary actions people launched the app to perform.
- Avoid hard-coded control heights. Current controls are taller than older macOS controls, and apps need flexible layout.
- Use concentric shapes when nesting controls or containers in current macOS UI. If corners feel pinched, flared, or visually unrelated, the shapes are fighting the system.
- Keep scroll edge effects functional. Use them to preserve legibility where floating controls overlap scrollable content; do not stack them or use them as decoration.
- Prefer current APIs for window structure: split view controllers, sidebar and inspector behaviors, safe areas, layout regions, and titlebar/split item accessories.
- If older HIG advice conflicts with current macOS visuals, keep the durable behavioral rule and update the appearance only when it preserves clarity.
- Current Apple guidance is organized across platforms, so Mac-specific audits still need real Mac verification: menu behavior, windowing, selection, text editing, pasteboard, drag and drop, state restoration, and accessibility.

## Toolbars, Sidebars, and Inspectors

- Group toolbar controls by function and frequency. Related icon buttons can share a backing; text buttons should generally stand alone so they do not read as one combined command.
- Do not leave noninteractive toolbar items on button-like glass. Titles, status labels, and counters should not look clickable.
- Keep toolbar commands menu-backed. Current floating toolbars did not remove the menu bar as the command map.
- Use prominent toolbar treatment sparingly for state or a truly primary action.
- Move secondary toolbar actions into a More menu when the toolbar becomes crowded, but keep those commands accessible and discoverable.
- Use sidebars for navigation and inspectors for properties. In current macOS, sidebars can float above content while inspectors sit alongside it; preserve that ownership distinction.
- Let rich content extend behind floating sidebars only when the content remains centered, readable, and unobscured.
- Audit light, dark, high-contrast, active, inactive, full-screen, and resized window states after adopting glass or new sidebar behavior.

## Menus and Icons

- Current macOS allows broader menu-icon use, but icons still need a reason.
- Add menu icons when they speed recognition of object types, destinations, spatial layouts, devices, apps, media, or frequently scanned key actions.
- Skip menu icons when they merely restate the label, add indentation noise, or make a mixed menu harder to scan.
- Keep icon columns visually consistent within a menu section. Inconsistent icon/no-icon rows can make text alignment worse.
- Prefer recognizable SF Symbols for system-like commands. Use custom symbols only when the metaphor is domain-specific and clearer than the generic option.
- Test menus on the target OS. If the system adds icons automatically, judge the real rendered menu, not the source code alone.

## Documents and Undo

- Document-based apps should make document identity, edited state, save/revert, printing, autosave, versions, and multiple windows feel native.
- Prefer AppKit document architecture when the app genuinely edits user-owned documents or files.
- All persistent document changes should be undoable. A partial undo chain can make the document state dishonest or inconsistent.
- Put undo registration near model primitives where possible; set user-facing undo action names at the command/action layer.
- Undo/Redo menu labels should name the user intent, not the implementation operation.
- Undo selection changes when it helps visual continuity, especially in drawing, layout, editing, or multi-pane document tools.

## Text, Pasteboard, and Services

- Treat standard Mac text behavior as a contract: selection, spelling, substitutions, smart punctuation, dictation, key bindings, undo, focus rings, and accessibility.
- Be skeptical of custom text editors, cross-platform text fields, and canvas-based inputs unless they deliberately preserve Mac text expectations.
- Use pasteboard types and Services when app objects, files, URLs, rich text, images, or selections should move between apps.
- Make copy, paste, drag, export, reveal, share, and open flows preserve user ownership of data.

## Accessibility

- Mac accessibility is a navigable tree, not a flat touch-order list. Group related controls into useful containers without over-nesting.
- Test with VoiceOver keyboard navigation through windows, sidebars, inspectors, toolbars, lists, and dialogs.
- Use rotors or equivalent navigation shortcuts when a visual scan has an accessibility counterpart, such as bookmarks, headings, errors, pages, sections, or results.
- Hover-only and gesture-only actions need accessible alternatives through visible commands, menus, context menus, or explicit accessibility actions.
- Keep accessibility focus and keyboard focus coherent, but do not assume they are the same state.

## Icons and Design Resources

- Use Apple Design Resources for current macOS UI kit calibration, fonts, app icon templates, SF Symbols, and platform appearance checks.
- SF Symbols integrate with the system font, weights, scales, variable rendering, and accessibility features; prefer them for system-like controls.
- Custom symbols should match the app's visual language while preserving the weight, optical size, and metaphor clarity of nearby system symbols.
- Current app icons can be layered, appearance-aware, and delivered through Icon Composer, but icon identity still starts with a clear metaphor and strong silhouette.
- Keep source artwork simple and controllable. Do not bake dynamic glass effects, masks, or appearance-specific hacks into the base artwork unless the pipeline requires it.

## Source URLs

- https://developer.apple.com/design/human-interface-guidelines/menus
- https://developer.apple.com/design/human-interface-guidelines/windows
- https://developer.apple.com/design/human-interface-guidelines/toolbars
- https://developer.apple.com/design/human-interface-guidelines/sidebars
- https://developer.apple.com/design/human-interface-guidelines/alerts
- https://developer.apple.com/design/human-interface-guidelines/drag-and-drop
- https://developer.apple.com/design/human-interface-guidelines/sf-symbols
- https://developer.apple.com/design/human-interface-guidelines/app-icons
- https://developer.apple.com/videos/play/wwdc2025/310/
- https://developer.apple.com/videos/play/wwdc2025/356/
- https://developer.apple.com/videos/play/wwdc2020/10104/
- https://developer.apple.com/videos/play/wwdc2025/229/
- https://developer.apple.com/documentation/AppKit/developing-a-document-based-app
- https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/UndoArchitecture/Articles/AppKitUndo.html
- https://developer.apple.com/documentation/AppKit/NSTextView
- https://developer.apple.com/documentation/appkit/nspasteboard/
- https://developer.apple.com/design/resources/
- https://developer.apple.com/videos/play/wwdc2025/361/
- https://tonsky.me/blog/tahoe-icons/
- https://blog.jim-nielsen.com/2025/icons-in-menus/
- https://weblog.rogueamoeba.com/2026/01/10/removing-tahoes-unwanted-menu-icons/
