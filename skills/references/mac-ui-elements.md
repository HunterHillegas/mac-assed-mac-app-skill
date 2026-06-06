# Mac UI Elements

Self-contained macOS UI element rules derived from Mac OS X / OS X HIG material.

## Menus

- Keep standard menus recognizable: app, File, Edit, Format when relevant, View, app-specific menus, Window, Help.
- Keep standard menus in the expected order. The menu bar is one of the strongest signals that an app belongs on the Mac.
- Use menus as the authoritative command catalog. Toolbar buttons, contextual menus, keyboard shortcuts, and gestures are accelerators, not replacements.
- Put app-wide commands in the app menu; document/content commands in File/Edit/View/app-specific menus; window management in Window; help/searchable help in Help.
- Group related commands with separators. Avoid giant flat menus.
- Use dynamic menu items when the command naturally reflects the selected object or current state.
- Use toggled menu items for persistent state. Make state text clear.
- Use contextual menus only for commands that make sense on the clicked object or selection.
- Keep Dock menu items useful for app-level quick actions and recent/common states.

## Keyboard Shortcuts

- Use shortcuts for frequent commands.
- Preserve standard shortcuts for standard commands.
- Do not assign shortcuts to every command; too many shortcuts reduce clarity and create conflicts.
- Keep shortcuts visible in menus.
- Provide keyboard navigation and selection for list/table/outline/detail workflows.

## Windows

- Use primary windows for the main work. Document-based apps should make the document/content identity clear.
- Make windows resizable unless content is inherently fixed.
- Preserve user window placement and size when it helps continuity.
- Keep titles user-facing. Do not show raw paths as titles.
- Respect active, inactive, key, and main window states.
- Use full screen when it helps focus on content, not as the only comfortable layout.
- Avoid palettes of floating windows unless the task needs persistent auxiliary tools.

## Toolbars

- Use toolbars for frequent window-level commands.
- Do not put every menu command in the toolbar.
- Group toolbar items by task.
- Use labels when icons are not self-evident.
- Keep icon size, weight, perspective, and metaphor consistent.
- Keep toolbar commands backed by menu items.
- Provide toolbar customization when the app has a broad command set and users benefit from tailoring it.
- Keep toolbar controls visually owned by the app/window chrome. Do not make them look like content-owned controls unless they actually are.

## Tabs and Multi-Document Metaphors

- Tabs should look and behave like tabs when they represent multiple documents, pages, views, or sessions within one window.
- The active tab must be unambiguous in light mode, dark mode, with two tabs, and with many tabs.
- Tabs should visually connect to the chrome or content region they control. Avoid detached button-like tabs when the user needs a document/page metaphor.
- Do not merge tab identity, location fields, and unrelated commands into one ambiguous control surface unless testing proves the ownership and active state are obvious.
- Keep close controls discoverable and spatially stable. Do not hide destructive tab-close behavior behind a representative icon or an unguessable hover transformation.
- If a new tab design is less space-efficient or scales worse for heavy tab users, it is a regression even if it looks cleaner with a few tabs.

## Sidebars, Source Lists, Scope Bars

- Use sidebars/source lists for persistent navigation among sources, collections, accounts, folders, libraries, or scopes.
- Keep sidebars scannable. Avoid stuffing controls into navigation rows.
- Use outlines when hierarchy matters.
- Use scope bars to filter/search the current content. Do not use a scope bar as primary navigation.
- Preserve sidebar selection and expansion where useful.

## Inspectors and Panels

- Use inspectors for properties of the current selection.
- Keep inspectors modeless and selection-aware.
- Use panels for auxiliary controls users may need while working.
- Do not use a panel when a popover, sidebar, or inline editor is simpler.
- Avoid drawers in modern apps; use sidebars, inspectors, popovers, split views, or panels instead.

## Popovers

- Use popovers for lightweight, transient detail attached to a source control or object.
- Keep popovers focused. Do not turn them into full workflows.
- Dismiss popovers predictably when users complete the action or click elsewhere.
- Do not use popovers for destructive confirmation when a sheet or alert would communicate risk better.

## Dialogs and Sheets

- Use sheets for modal choices tied to one window/document.
- Use app-modal dialogs only when the decision blocks the entire app.
- Keep each dialog focused on one task or decision.
- Use progressive disclosure for advanced options.
- Put controls in logical order with clear grouping.
- Provide Cancel when backing out is reasonable.
- Make default actions safe and predictable.

## Alerts

- Use alerts for errors, warnings, and consequential confirmation.
- Do not use alerts for routine choices, status, onboarding, or ordinary branching.
- State the problem clearly, then the consequence or remedy.
- Use specific action buttons: `Delete`, `Replace`, `Discard Changes`, `Keep Both`, `Cancel`.
- Avoid vague buttons: `OK`, `Yes`, `No`, `Submit`, unless no clearer action exists.
- Do not over-confirm. If undo or recovery is available, use that instead of alert fatigue.

## Controls

- Push button: immediate command.
- Icon button: command where the icon is obvious or labeled by tooltip/accessibility.
- Do not turn an icon that represents an object into a destructive command for that object on hover.
- Checkbox: independent on/off option.
- Radio buttons: small mutually exclusive set where all choices should be visible.
- Pop-up button: mutually exclusive choices when space is tight or choices are secondary.
- Pull-down menu button: commands, not value selection.
- Segmented control: compact related modes, views, filters, or choices.
- Slider: continuous bounded numeric value.
- Stepper: small incremental numeric adjustment, usually with a value field.
- Search field: search/filter text with standard search affordances.
- Table/list/outline: scannable collections with selection and keyboard behavior.
- Text field: direct text input; label clearly; validate near the field where possible.
- Progress indicator: visible status for long operations.

## Control State

- Disable unavailable controls when their existence helps users understand the model.
- Hide controls when they are irrelevant in the current context.
- Keep focus rings, selection, hover, pressed, inactive, and disabled states legible.
- Validate input without surprising users. Avoid wiping values unless the user asked.
- If a control applies immediately, make the result visible and reversible.

## Preferences and Settings

- Use preferences/settings for durable user choices.
- The app's settings must open from `Settings...` and `Command-,`.
- Settings should be a real window or panel, not an editor tab, web page, or raw configuration file.
- Do not hide primary workflow controls in preferences.
- Group preferences by user goals, not implementation subsystems.
- Keep labels concrete and searchable.
- Apply changes immediately when safe; otherwise make Apply/Revert behavior explicit.

## Services and System Text Behavior

- Support the Services menu where text, files, URLs, or selected objects should participate in system workflows.
- Make Services available from relevant context menus, not only the menu bar.
- Text fields and text views should preserve normal Mac behavior: standard editing shortcuts, selection, spelling, substitutions, smart punctuation preferences, user key bindings, dictation, VoiceOver, and focus rings.
- Be skeptical of custom text editors and cross-platform text fields. They need explicit checks for Mac editing behavior and accessibility.
