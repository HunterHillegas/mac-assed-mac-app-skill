# HIG UI Rules for Mac-Assed Mac Apps

Use this as the working rulebook when updating macOS UIs. It synthesizes the Mac OS X / OS X Human Interface Guidelines source set from 2004 through 2013 and intentionally ignores iOS-only material.

## Source Priority

- Prefer 2013 guidance when versions conflict.
- Treat older guidance as useful for durable Mac principles and Aqua-era details, not as permission to revive deprecated controls.
- Keep visual style modern unless the user explicitly asks for period-accurate Aqua.
- Use [mac-assedness.md](mac-assedness.md) when the question is about originality, taste, custom controls, visual identity, or modern Apple design-language tradeoffs.

## Mental Model and App Shape

- Start with the user's objects and actions. Mac UI is noun-then-verb: select the thing, then choose the command.
- Make the primary window reflect the task model: source/list/detail, document/canvas/inspector, mailbox/message, playlist/items, project/tasks, etc.
- Put frequent, concrete actions near the content. Put complete command coverage in menus.
- Keep the basic task obvious. Secondary options should be available without competing with the core workflow.
- Use familiar metaphors only when they clarify behavior. Do not stretch a metaphor so far that it lies about what the app does.
- Make clickable and draggable things look actionable. Do not rely on invisible affordances.
- Separate structural expectations from expressive opportunities. Preserve the learned Mac structure; spend originality where it improves recognition, clarity, purpose, or delight.

## Content First

- Let user content dominate the window. Toolbars, sidebars, inspectors, and status areas should support the work.
- Avoid busy dashboards when a focused document/list/detail flow would better match the task.
- Keep app-management chores out of the user's way: setup, sync, imports, saves, and background work should be smooth and observable.
- Support full screen only when it helps focus on content. Do not force it as the primary experience.

## Menus and Commands

- Use the single macOS menu bar as a first-class command surface.
- Keep standard menus and ordering where applicable: app, File, Edit, Format, View, app-specific menus, Window, Help.
- Put every important command in a menu, even when it also exists in a toolbar, contextual menu, button, or touch/gesture path.
- Use contextual menus for shortcuts to visible-object actions, not as the only home for essential commands.
- Name menu items as actions. Prefer clear verbs: `Export…`, `Duplicate`, `Show Inspector`, `Hide Sidebar`.
- Use title-style capitalization for menu titles, menu items, push buttons, and toolbar labels.
- Use a U+2026 ellipsis for commands that need more user input before executing: `Open…`, `Export…`, `Find…`, `Print…`, `Settings…`.
- Do not use an ellipsis for commands that execute immediately, merely show a panel, or only sometimes show an alert: `Save`, `Duplicate`, `Get Info`, `Show Inspector`, `Close`.
- Use toggled menu items to reflect state. Make state text unambiguous.
- Use separators to group related menu items. Avoid long unstructured menus.
- Use keyboard shortcuts for frequent commands. Prefer standard shortcuts for standard commands; do not repurpose reserved or expected equivalents.

## Windows

- Choose window type by role:
  - Main/document windows for primary content and editing.
  - Panels for auxiliary controls that can remain available.
  - Inspectors for selected-object properties.
  - Sheets for document/window-specific modal decisions.
  - Alerts for errors, warnings, and high-risk confirmation.
  - Popovers for lightweight, transient detail tied to a control or object.
- Open new windows in predictable positions. Preserve user resizing and placement when appropriate.
- Make windows resizable unless the content truly has fixed dimensions.
- Respect main/key/inactive states. Avoid custom styling that erases focus and activation cues.
- Use window titles for document/content identity, not raw file paths.
- Support proxy/document behavior when the app is document-based and the framework provides it.
- Avoid drawers in modern macOS UI. Older HIGs documented drawers, but later guidance and platform practice moved toward sidebars, panels, popovers, and inspectors.
- Use bottom bars/status areas only for persistent status or controls that apply to the visible content.

## Toolbars, Sidebars, and Inspectors

- Use toolbars for frequent window-level commands, not every command.
- Keep toolbar items recognizable, stable, and backed by menu commands.
- Use text labels when icons alone are not universally clear.
- Keep toolbar icons visually consistent: simple, centered, same optical weight, and appropriate for the toolbar style.
- Use sidebars/source lists for navigation among collections, sources, accounts, folders, or scopes.
- Use inspectors for properties of the current selection. Keep them modeless and selection-aware.
- Use scope bars for filtering/searching within the current content, not as general navigation.

## Controls

- Use standard controls according to their semantics:
  - Push button: immediate command.
  - Checkbox: independent on/off option.
  - Radio buttons: mutually exclusive small set where all choices should be visible.
  - Pop-up button: mutually exclusive set when space is tight or choices are secondary.
  - Segmented control: closely related modes, views, or filters.
  - Slider/stepper: bounded numeric adjustment.
  - Search field: search/filter text, with standard search behavior.
  - Table/outline/list: scannable collections with selection, sorting, and keyboard navigation.
- Do not make controls perform surprising side effects. If changing a value applies immediately, make the result visible and reversible.
- Disable unavailable controls instead of hiding them when their presence teaches the model. Hide only when the control is irrelevant in the current context.
- Use progressive disclosure for advanced or rarely used settings.
- Avoid custom skinned controls unless the task genuinely needs a direct-manipulation surface.
- Avoid deprecated Aqua-era controls in modern apps. Bevel buttons, drawers, and brushed-metal styling are historical guidance, not current defaults.
- If customizing controls, preserve expected control behavior, keyboard access, accessibility semantics, focus/disabled/pressed states, and future maintainability.

## Dialogs, Sheets, Alerts

- Use sheets for choices tied to a specific window or document.
- Use app-modal dialogs only when the decision truly blocks the whole app.
- Keep dialogs focused on one decision or task. Do not build full workflows inside alerts.
- Put the safest or most likely action in the default position only when it is actually safe.
- Make destructive actions explicit. Use verbs that name the consequence: `Delete`, `Remove`, `Discard Changes`.
- Provide Cancel when the user can reasonably back out.
- Explain what happened, why it matters, and what the user can do. Avoid codes and internal causes unless needed for troubleshooting.
- Do not ask for confirmation every time if undo or safe recovery is available.
- For long operations, show determinate progress when possible. If not possible, show activity plus useful status text.

## Text and Labels

- Use user terms, not implementation terms. Prefer the vocabulary of the task domain.
- Be specific where the user must choose. Do not sacrifice clarity just to save space.
- Avoid repeating context already supplied by the window, group, or dialog.
- Use title-style capitalization for menu items, push buttons, toolbar labels, and short labels/headings.
- Use sentence-style capitalization for checkbox/radio options, dialog messages, help text, and explanatory text.
- End complete sentences with punctuation. Do not punctuate fragments unless grammar requires it.
- Use one space between sentences.
- Use a colon after introductory text that labels a following control or group of controls. Do not use colons in button labels, menu items, tab titles, segmented controls, table headings, or group box titles.
- Match dialog titles to the invoking command without the ellipsis.
- Use contractions only when space is tight and meaning remains clear.

## Icons and Visual Detail

- App icons should communicate the app's purpose and genre at a glance.
- Document icons should clearly belong to the app while distinguishing document types.
- Toolbar/sidebar icons should represent actions or objects simply and consistently.
- Prefer recognizable Mac symbols and metaphors. Do not make users decode branding marks as controls.
- Provide high-resolution artwork and let the system choose the right representation.
- Use depth, texture, and realism only when they clarify object identity or interaction. Avoid decorative realism that competes with content.
- Custom iconography is valid when system symbols cannot express the concept precisely or when a coherent icon style strengthens app identity without reducing recognition.

## Direct Manipulation, Selection, Drag and Drop

- Support direct manipulation when users naturally expect it: reorder, resize, drag files/items, move selections, reveal locations, edit in place.
- Keep the manipulated object visible during the action when possible.
- Give drag feedback: valid targets, invalid targets, insertion positions, copy/move semantics, and drop result.
- Preserve selection predictably after actions.
- Provide undo for edits, moves, deletes, and reordering wherever feasible.
- Support keyboard selection and navigation alongside pointer interactions.

## Feedback, Responsiveness, and Trust

- Acknowledge every user command quickly.
- Keep the UI responsive during work. Move long tasks off the main thread.
- Show progress for operations that may take noticeable time.
- Use subtle animation to clarify relationships and transitions, not as decoration.
- Communicate background-process problems through the foreground app when one exists.
- Make autosave, versions, sync, and error recovery understandable without making users manage machinery.
- Earn trust through predictable state restoration, stable layout, accurate enabled/disabled states, and clear recovery paths.

## Preferences, Help, Accessibility, Internationalization

- Put durable user choices in Preferences/Settings. Keep task-specific controls in the task UI.
- Keep preferences grouped, labeled, and searchable if the app grows.
- Make help available but unobtrusive. Use Help menu entries, help buttons, tooltips/help tags, and contextual assistance where appropriate.
- Design for keyboard access, VoiceOver labels, sufficient contrast, dynamic text where supported, and logical focus order.
- Leave room for localized text expansion. Do not hard-code English-length assumptions into controls.
- Support standard services, sharing, printing, colors/fonts panels, and drag/drop when they fit the app domain.

## Common Mac Violations to Fix

- Essential command exists only as an unlabeled icon.
- App has no meaningful menu structure.
- Toolbar duplicates a web nav bar instead of exposing document/window commands.
- Main window is a marketing surface instead of a working surface.
- Settings are mixed into the main workflow or core controls are buried in preferences.
- Alerts are used for ordinary choices or status.
- Buttons use vague labels such as `OK`, `Submit`, `Yes`, or `No` when a consequence-specific verb would be clearer.
- Dialogs use developer nouns such as token, payload, endpoint, object, UUID, or exception for nondeveloper users.
- Commands that need input use `...` instead of U+2026, or omit the ellipsis.
- Controls, menus, and labels use inconsistent capitalization.
- Resizing breaks the layout, hides content, or fails to preserve user intent.
- Hover-only controls hide important functionality.
- Custom focus, selection, or disabled states obscure platform behavior.
- App follows the current Apple visual fashion but breaks older, hardened Mac behaviors.
- App is so neutral that its purpose, audience, or point of view disappears.
