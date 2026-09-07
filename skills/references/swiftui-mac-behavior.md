# SwiftUI Mac Behavior

Use this for SwiftUI-specific interaction decisions. General behavior belongs in [mac-ui-elements.md](mac-ui-elements.md); choose runtime checks from [mac-ui-verification.md](mac-ui-verification.md).

## Availability and Implementation Choice

- Check the project's SDK and minimum macOS version before using any API below. Newer or beta APIs need verified signatures, availability, and a supported fallback; do not raise the deployment target as a UI cleanup side effect.
- Preserve working SwiftUI behavior. Prefer a narrow AppKit bridge when a demonstrated gap cannot be met by supported SwiftUI APIs; toolkit choice alone is not a defect.
- Use documentation and the installed SDK for API facts. Articles explain motivation and observed limitations, which may change with an OS release.

## Selection and Context Targets

- Start with `List` or `Table` when their selection behavior matches the task. A custom `ScrollView`/`LazyVStack` collection must supply selection, focus, keyboard navigation, and context-target feedback explicitly; do not rely on assumptions about SwiftUI's internal AppKit implementation.
- Use `appearsActive` for active appearance. It is not a synonym for focus: a main window's toolbar can appear active while another window is key.
- Read `backgroundProminence` inside the row content to adapt foreground contrast to its background. System collections and selection styles propagate it; a custom collection must choose and propagate prominence consistent with its actual selection, pane focus, and active appearance. Setting it does not implement selection or focus.
- Resolve context-menu actions against their supplied item IDs or the clicked target, not an unrelated global selection. A menu on a selected row can operate on the selected set; a menu on an unselected row needs an unambiguous target. Follow the system collection's behavior rather than forcing right-click to always change or never change selection.
- Use `contextMenu(forSelectionType:menu:primaryAction:)` with a selection-supporting container such as `List` or `Table`. It does not activate in a plain custom stack without that container support. For custom rows, use row-scoped menus with explicit target IDs; if needed target feedback remains unavailable, bridge narrowly or report the limitation.

## Command and Keyboard Routing

- Scope selection and command handlers to the intended scene/window. Use `focusedValue` for values tied to focus within a view hierarchy and `focusedSceneValue` for values available throughout the active scene. A scene-wide selection alone does not establish which pane or text editor owns an editing command.
- Keep app-object commands from intercepting Cut, Copy, Paste, Delete, or Undo while a text editor owns that action.
- Prefer semantic handlers such as `onMoveCommand` for directional navigation when appropriate. Use `onKeyPress` for behavior that needs actual key events, with deliberate handling of consumed versus unhandled input.
- Do not intercept arrow keys globally. Scope result navigation to the search interaction and preserve text editing, input-method composition, and candidate selection.

## Drag Lifecycle and Reordering

- Observe source lifecycle with `onDragSessionUpdated` when supported. Reset transient visuals on completion and cancellation, including external drops; destination hover callbacks alone cannot establish that a source drag ended.
- Use the final performed operation to decide source-side move handling. Do not delete the source merely because it left the view or because move was offered as a possible operation.
- Where supported, use `reorderable()` on dynamic content together with a surrounding `reorderContainer` and a model update for the resulting difference. The modifier alone does not persist the new order. Confirm current availability before adopting these newer APIs.
- Use stable item identities and preserve order when moving multiple items. For older targets, retain a working supported SwiftUI implementation or use an AppKit bridge where required.

## Toolbars and Documents

- Design one coherent toolbar per window with clear sidebar/content/inspector ownership. Inspect the rendered result of distributed `.toolbar` modifiers at wide and narrow widths.
- Where supported, `visibilityPriority` controls which items enter overflow first. It does not establish placement, command targeting, or grouping.
- SwiftUI `DocumentGroup` is a valid starting point for file-based apps, including document commands and multiple documents on macOS. Use AppKit document architecture when the app needs its additional control; do not prescribe a rewrite solely for Mac credibility.
- Verify undo ownership and document lifecycle explicitly. A scene declaration does not establish that custom model edits register coherent undo operations.

## Primary API References

- [Active appearance](https://developer.apple.com/documentation/swiftui/environmentvalues/appearsactive)
- [Background prominence](https://developer.apple.com/documentation/swiftui/environmentvalues/backgroundprominence)
- [Selection-aware context menus](https://developer.apple.com/documentation/swiftui/view/contextmenu(forselectiontype:menu:primaryaction:))
- [Focused values](https://developer.apple.com/documentation/swiftui/focusedvalues)
- [Menu-bar command routing](https://developer.apple.com/documentation/swiftui/building-and-customizing-the-menu-bar-with-swiftui)
- [Input and event modifiers](https://developer.apple.com/documentation/swiftui/view-input-and-events)
- [Drag-session updates](https://developer.apple.com/documentation/swiftui/view/ondragsessionupdated(_:))
- [Reordering collections](https://developer.apple.com/documentation/swiftui/reordering-items-in-lists-stacks-grids-and-custom-layouts)
- [Toolbar visibility priority](https://developer.apple.com/documentation/swiftui/toolbarcontent/visibilitypriority(_:))
- [DocumentGroup](https://developer.apple.com/documentation/swiftui/documentgroup)
