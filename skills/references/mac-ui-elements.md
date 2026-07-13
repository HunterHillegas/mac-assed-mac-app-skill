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
- Arrow keys should move the active list/table/outline selection when that pane has focus.
- Search fields in command/search workflows should not trap all keyboard behavior if users need arrow keys to move through results while keeping the query focused.

## Windows

- Use primary windows for the main work. Document-based apps should make the document/content identity clear.
- Make windows resizable unless content is inherently fixed.
- Preserve user window placement and size when it helps continuity.
- Keep titles user-facing. Do not show raw paths as titles.
- Respect active, inactive, key, and main window states.
- Use full screen when it helps focus on content, not as the only comfortable layout.
- Avoid palettes of floating windows unless the task needs persistent auxiliary tools.
- Do not force a sophisticated desktop workflow into one window because the implementation started on iPad, web, or mobile.
- Support multiple windows for multiple documents, projects, comparisons, or independent workspaces when the model calls for it.
- Let users detach or separate inspectors, palettes, tabs, or documents when scale, multiple displays, or comparison workflows make that useful.

## Toolbars

- Use toolbars for frequent window-level commands.
- Do not put every menu command in the toolbar.
- Group toolbar items by task, function, and frequency so related controls share clear ownership.
- Use labels when icons are not self-evident.
- Keep icon size, weight, perspective, and metaphor consistent.
- Keep toolbar commands backed by menu items.
- Provide toolbar customization when the app has a broad command set and users benefit from tailoring it.
- Restore toolbar customization, item order, labels/icons choice, and visibility when those choices are supported.
- Keep toolbar controls visually owned by the app/window chrome. Do not make them look like content-owned controls unless they actually are.
- Do not make noninteractive toolbar status, titles, or counters look like buttons, including when adopting glass-backed toolbar items.
- Use prominent toolbar treatment sparingly for state or a truly primary action.
- In SwiftUI, audit final toolbar placement in the running app. Semantic placements and distributed `.toolbar` modifiers can produce toolbars that do not match the intended Mac hierarchy.
- Where available, use `.visibilityPriority` to control which SwiftUI toolbar items enter overflow first. It does not fix poor grouping, placement, or ownership.

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
- Preserve the distinction between a navigation sidebar and a property inspector. Current sidebars may float above content; inspectors remain selection/property surfaces.
- Let content extend behind a floating sidebar only when the content remains readable, centered, and unobscured.
- Use scope bars to filter/search the current content. Do not use a scope bar as primary navigation.
- Preserve sidebar selection and expansion where useful.
- Preserve nuanced selection styling: key-window selection, inactive-window selection, selected-but-not-focused rows, and context-menu target feedback are distinct states.
- Prefer system `List`, table, or outline behavior when it gives correct Mac selection and context-menu affordances for free. Recreate those details before replacing it with a fully custom stack.
- In SwiftUI, read `appearsActive` for active-window styling and `backgroundProminence` for selection emphasis. For a custom collection, derive prominence from focus and pass it through the environment so unfocused selection remains visible but subdued.
- Do not pretend context-menu targeting is selection. If SwiftUI cannot expose the open-menu target for a custom collection, use a system collection, bridge to AppKit, or record the limitation.

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
- Add menu or toolbar icons when they speed recognition of object types, destinations, spatial layouts, devices, apps, media, or key scanned actions. Skip them when they merely restate text or add alignment noise.
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
- Context menus need a visible target when the menu applies to an object other than the selected object.
- Inactive windows should visually recede; custom colored controls and rows should respect active-window state.

## Selection and Pasteboard

- Use standard selection behavior for lists, tables, outlines, grids, canvases, and custom collections.
- Support command-click for noncontiguous selection and shift-click for ranges when multi-selection is meaningful.
- Preserve separate selected, focused, inactive, and context-menu-target states. A right-click on an unselected object should not destroy a meaningful multi-selection unless the command clearly targets only the clicked object.
- Make Edit menu commands reflect the current selection: Cut, Copy, Paste, Duplicate, Delete, Select All, Find, and related commands should enable only when they make sense.
- When selected objects are copied, put useful representations on the pasteboard: plain text, rich text, file URLs, image data, URLs, or app-specific types as appropriate.
- When pasted into another app, the result should be useful. A file selection might paste file names into a text editor and file URLs into a file-aware destination.
- Let selected objects be dragged out, rearranged, or dropped into compatible places when the model supports it.
- If custom selection or pasteboard behavior is incomplete, document the gap during review and prefer a system list/table/outline/control where possible.

## Drag and Drop

- Treat drag and drop as a first-class Mac interaction: import files, reorder lists, move content between panes/windows, and expose valid drop targets where the model supports it.
- Support dragging in from Finder and other apps, dragging out to Finder or compatible apps, and dragging between windows when the data model supports it.
- Show source feedback, insertion points, target highlighting, copy/move semantics, and invalid-drop feedback.
- Support spring-loaded navigation, hover expansion, or equivalent delayed target reveal when users need to drag through hierarchy.
- Avoid drag-source visuals that can get stuck when a drop completes outside the window or app.
- In SwiftUI, use `.onDragSessionUpdated` when available to observe source-side start, updates, and completion, including drops outside the view. Bridge to AppKit when the deployment target or available API cannot keep source and target state correct.
- Prefer `.reorderable` for straightforward reordering on OS 27+; use lower-level drag/drop behavior when the task needs richer transfer or destination semantics.

## Preferences and Settings

- Use preferences/settings for durable user choices.
- The app's settings must open from `Settings…` and `Command-,`. On modern macOS the app-menu item is named `Settings…`; `Preferences…` is the historical name.
- Settings should be a real window or panel, not an editor tab, web page, or raw configuration file.
- Do not hide primary workflow controls in preferences.
- Do not ship a complex Mac app with no durable customization. Good defaults matter, but power users should be able to shape frequent workflows.
- Group preferences by user goals, not implementation subsystems.
- Keep labels concrete and searchable.
- Apply changes immediately when safe; otherwise make Apply/Revert behavior explicit.

## Services and System Text Behavior

- Support the Services menu where text, files, URLs, or selected objects should participate in system workflows.
- Make Services available from relevant context menus, not only the menu bar.
- Text fields and text views should preserve normal Mac behavior: standard editing shortcuts, selection, spelling, substitutions, smart punctuation preferences, user key bindings, dictation, VoiceOver, and focus rings.
- Be skeptical of custom text editors and cross-platform text fields. They need explicit checks for Mac editing behavior and accessibility.
- Use pasteboard types and Services for user-owned data that should move between apps: files, URLs, images, rich text, selected objects, and exports.
