# Mac UI Principles

Self-contained advice derived from Mac OS X / OS X HIG material. Use this when deciding the shape of a macOS app, not just polishing controls.

## Mental Model

- Start from the user's existing model of the work. A mail app is messages, mailboxes, recipients, and sending; a photo app is photos, albums, cameras, and edits; a planning app is projects, tasks, deadlines, and progress.
- Reflect that model in the window layout, navigation, toolbar groups, menu organization, and inspector/panel choices.
- Keep the core objects visible and selectable. Mac interaction expects the user to choose a noun, then choose a verb.
- Use domain metaphors when they clarify. Do not force cute metaphors onto tasks where plain structure works better.
- Make the app's conceptual model teachable from the screen: primary content, visible selection, available commands, and reversible exploration.

## User Control

- Let the user initiate and control actions. Avoid autonomous UI changes that feel like the app took over.
- Provide guardrails for dangerous actions without blocking ordinary work.
- Prefer undo, versioning, cancel, and recovery over repeated confirmation.
- Keep expert paths available without making novice paths cramped or hidden.
- Avoid app-management busywork. Setup, sync, import, save, and restore should be observable but not central.

## Discoverability

- Make important commands findable in the menu bar.
- Make clickable things look clickable and draggable things look draggable.
- Do not hide essential actions only behind hover states, gestures, contextual menus, or toolbar icons.
- Keep empty states useful by offering the first real action, not marketing copy.
- Use standard controls and placements so users can transfer habits from other Mac apps.

## Direct Manipulation

- Use direct manipulation where users expect to move, reorder, resize, select, reveal, or edit visible objects.
- Keep the manipulated object visible while the user acts on it.
- Show insertion points, target highlighting, invalid-drop feedback, and copy/move semantics during drag and drop.
- Preserve selection predictably after manipulation.
- Provide undo for rearranging, moving, deleting, and editing.

## Feedback and Responsiveness

- Acknowledge input immediately.
- Keep the main thread responsive. Long work needs progress, cancellation where possible, and useful status text.
- Prefer determinate progress when the app can estimate work. Use indeterminate activity only when the amount of work is unknowable.
- Explain errors in user terms: what happened, why it matters, and what the user can do next.
- Use animation to clarify relationships or transitions: sheet attached to a window, item moved into a list, window minimized, popover source. Do not animate for decoration.
- Background components should communicate through the foreground app whenever a foreground app exists.

## Stability and Trust

- Preserve window size, position, sidebar state, visible columns, sort order, and user customization when appropriate.
- Make enabled, disabled, selected, focused, and inactive states visually accurate.
- Avoid reflowing layouts in ways that make controls jump during ordinary use.
- Show saved/synced/error states truthfully.
- Keep destructive consequences explicit and reversible when possible.

## Mac App Shape

- Use the menu bar as the complete command map.
- Use windows for primary work, panels/inspectors for auxiliary properties, sheets for window-specific modal choices, alerts for important warnings/errors, and preferences/settings for durable choices.
- Use sidebars/source lists for sources and collections; use tables/lists/outlines for scannable collections; use detail panes/canvases for selected content.
- Keep chrome subordinate to user content. The main window should be a working surface, not a launch page.
- Support keyboard, mouse, trackpad, accessibility, localization, drag and drop, Help, services, printing, and system panels where they fit the app.
- Treat Mac identity as behavior plus affordances, not just visual style. A current Apple-looking app can still feel wrong if menus, windows, selection, shortcuts, density, or hierarchy are wrong.
- Let the app have a point of view. The goal is not generic system cosplay; the goal is a tool that belongs on the Mac and has a reason to exist.

## Older Guidance, Modern Use

- Keep durable principles: mental model, consistency, user control, feedback, direct manipulation, forgiveness, discoverability, and clear text.
- Treat older Aqua visual treatments as historical unless the user wants a retro UI. Avoid brushed metal, drawer-heavy design, bevel-button-heavy palettes, and purely decorative realism in modern apps.
