# Mac UI Principles

Self-contained advice derived from Mac OS X / OS X HIG material. Use this when deciding the shape of a macOS app, not just polishing controls.

## Mental Model

- Start from the user's existing model of the work. A mail app is messages, mailboxes, recipients, and sending; a photo app is photos, albums, cameras, and edits; a planning app is projects, tasks, deadlines, and progress.
- Reflect that model in the window layout, navigation, toolbar groups, menu organization, and inspector/panel choices.
- Keep the core objects visible and selectable. Mac interaction expects the user to choose a noun, then choose a verb.
- For every visible noun, decide the natural verbs: select, open, reveal, copy, paste, drag, delete, rename, export, inspect, share, and undo.
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
- Do not hide destructive actions behind hover-only transformations or controls that look like object identity.
- Keep empty states useful by offering the first real action, not marketing copy.
- Use standard controls and placements so users can transfer habits from other Mac apps.
- Use progressive disclosure for depth: simple first-run surfaces, advanced options nearby, and menus/help for the full command map.

## Direct Manipulation

- Use direct manipulation where users expect to move, reorder, resize, select, reveal, or edit visible objects.
- Keep the manipulated object visible while the user acts on it.
- Show insertion points, target highlighting, invalid-drop feedback, and copy/move semantics during drag and drop.
- Preserve selection predictably after manipulation.
- Provide undo for rearranging, moving, deleting, and editing.
- If users can select an object, make copy, paste, drag, context menus, keyboard navigation, and Delete behave like they do in comparable Mac apps when the model allows it.

## Feedback and Responsiveness

- Acknowledge input immediately.
- Keep the main thread responsive. Long work needs progress, cancellation where possible, and useful status text.
- Prefer determinate progress when the app can estimate work. Use indeterminate activity only when the amount of work is unknowable.
- Explain errors in user terms: what happened, why it matters, and what the user can do next.
- Use animation to clarify relationships or transitions: sheet attached to a window, item moved into a list, window minimized, popover source. Do not animate for decoration.
- Background components should communicate through the foreground app whenever a foreground app exists.
- Current materials and scroll edge effects should clarify which controls float above content. They are not decorative motion or texture.

## Stability and Trust

- Preserve window size, position, sidebar state, visible columns, sort order, and user customization when appropriate.
- Preserve state that represents user intent, not incidental motion. Remember a workspace layout or expanded inspector; do not remember a temporary alert position dragged aside to read content behind it.
- Make enabled, disabled, selected, focused, and inactive states visually accurate.
- Avoid reflowing layouts in ways that make controls jump during ordinary use.
- Show saved/synced/error states truthfully.
- Keep destructive consequences explicit and reversible when possible.
- Evolve established UI by reducing thought, not adding it. If a redesign makes users consciously reason about active state, ownership, or basic commands they used to read instantly, it is likely worse.
- Familiar visual metaphors are functional, not decorative. Remove or restyle them only when the replacement preserves the same clarity.
- For apps that sync or bridge external systems, keep data ownership clear. Prefer official APIs, open formats, or compatible canonical storage over private lock-in.
- Documentation and onboarding are part of trust for professional Mac apps. A deep tool should explain itself with the same care it puts into the interface.
- Durable pricing, trials, update terms, and licensing can affect product trust. They are not UI controls, but they shape whether the app feels like a professional Mac tool users can keep relying on.

## Mac App Shape

- Use the menu bar as the complete command map.
- Use windows for primary work, panels/inspectors for auxiliary properties, sheets for window-specific modal choices, alerts for important warnings/errors, and preferences/settings for durable choices.
- Be unafraid of windows. Documents, comparisons, detachable palettes, inspectors, and multi-display workflows may deserve separate windows or tabs instead of being forced into one iPad-like surface.
- Use sidebars/source lists for sources and collections; use tables/lists/outlines for scannable collections; use detail panes/canvases for selected content.
- Keep chrome subordinate to user content. The main window should be a working surface, not a launch page.
- Support keyboard, mouse, trackpad, accessibility, localization, drag and drop, Help, services, printing, and system panels where they fit the app.
- Treat Mac identity as behavior plus affordances, not just visual style. A current Apple-looking app can still feel wrong if menus, windows, selection, shortcuts, density, or hierarchy are wrong.
- Let the app have a point of view. The goal is not generic system cosplay; the goal is a tool that belongs on the Mac and has a reason to exist.
- Prefer "good Mac citizen" as a practical test: menus, settings, services, text fields, keyboard behavior, windowing, typography, and symbols should behave like users expect on macOS, regardless of toolkit.
- For document apps, include document identity, edited state, autosave/versions where relevant, undo, print, reveal/open/export paths, and multi-window behavior in the app shape.
- For apps with user-owned data, support interchange where sensible: open formats, import/export, pasteboard types, drag in/out, Quick Look/reveal/open flows, and Services.
- Treat accessibility as part of the shape: VoiceOver containers, keyboard paths, rotors or equivalent navigation, and non-hover alternatives for hidden controls.

## Older Guidance, Modern Use

- Keep durable principles: mental model, consistency, user control, feedback, direct manipulation, forgiveness, discoverability, and clear text.
- Treat older Aqua visual treatments as historical unless the user wants a retro UI. Avoid brushed metal, drawer-heavy design, bevel-button-heavy palettes, and purely decorative realism in modern apps.
- Treat Mac culture as cumulative. Keep behaviors users still rely on, adopt newer system conventions when they improve clarity, and reject imported patterns that reduce Mac-specific power.
