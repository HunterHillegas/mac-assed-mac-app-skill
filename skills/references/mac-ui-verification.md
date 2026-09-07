# Mac UI Verification

Choose checks for the affected behavior and app type. This is a menu of useful checks, not a requirement to exercise every surface for every edit. Use representative content and reversible actions.

## Evidence and Findings

- Screenshots establish visible hierarchy, copy, density, and state at one instant. They do not establish keyboard behavior, menu coverage, accessibility semantics, responsiveness, or successful state restoration.
- Code can identify implementation risks; a native control or passing build does not prove the surrounding behavior is correct.
- For each substantive finding, name the surface, triggering action/state, observed result, expected behavior, and user consequence. Separate confirmed failures from hypotheses and taste recommendations.
- Rank blocked work, incorrect command targets, data loss, and inaccessible actions ahead of visual polish. Report what was actually exercised and any relevant OS or tooling limit.

## Commands, Focus, and Selection

- Invoke the same command from a menu, shortcut, toolbar, and context menu where provided. Check consistent semantics and availability for each path's intended target; a context menu may target a different object than the persistent selection.
- Open two windows with different selections. Switch between them, focus a text field, then focus an inspector. Copy, Delete, and Undo should affect the intended content; editing inspector text must not delete an unrelated selected object.
- Exercise empty, single, and multiple selection. Test Shift-click ranges, Command-click toggles, keyboard movement, and selection after delete, reorder, filtering, or refresh.
- Open a context menu on a selected item, then on an unselected item. Verify which set the command affects and whether target feedback makes that clear. Dismiss without an action and check selection continuity.
- Distinguish active-window, inactive-window, focused-pane, selected-but-unfocused, and context-target appearances. No state should falsely suggest keyboard ownership.

## Text and Keyboard

- Complete the affected workflow using keyboard navigation. Respect the user's macOS keyboard-navigation settings; check focus visibility and a path out of custom controls.
- In editable text, try selection, standard editing shortcuts, Undo/Redo, and a system text substitution where appropriate. Custom key handlers must not consume text editing, input-method composition, or candidate navigation.
- In search-result workflows, check result navigation and activation while typing. Return, Escape, and arrow keys need predictable roles without breaking the text field's native behavior.

## Drag, Pasteboard, and Recovery

- Try dragging within the collection, between app windows, in from Finder, and out to a compatible app where supported.
- Test an accepted drop, rejected target, Escape cancellation, and a drop outside the source window. Source dimming and destination highlighting must clear in every case.
- Check insertion position, multi-item order, and copy/move feedback. A failed or cancelled move must leave source data intact; a successful move must not duplicate or lose items.
- Paste copied objects into a plausible receiving app. Verify that the representation is useful there, not just inside the originating app.
- Undo and redo a representative edit, deletion, or reorder. Check model state, visible selection, action names, and per-document history. For irreversible external operations, verify truthful status and the offered recovery path instead.

## Windows, Settings, and Layout

- Resize to the supported minimum and a wide window; inspect long names, empty content, dense content, toolbar overflow, and collapsed sidebars/inspectors.
- Open Settings from its menu command and Command-comma. Reopen it and verify sensible reuse/focus. Test setting application and persistence where changed.
- Close and reopen relevant windows. Distinguish closing a window from quitting the app; check new/open/reopen behavior appropriate to the app type.
- For restoration changes, relaunch with different display space available. Restore useful size and layout without leaving windows offscreen.
- For document changes, check open/save/cancel, edited state, document identity, and multiple documents as applicable. Do not infer document support from a titlebar alone.

## Accessibility and Appearance

- Use VoiceOver on the changed surface: names, roles, values, selected/mixed states, grouping, actions, and logical navigation. Labels alone are not complete accessibility.
- Inspect light/dark and active/inactive windows when visual styling changes. For custom color, motion, or materials, also check Increase Contrast, Reduce Transparency, Reduce Motion, and alternate accent colors as relevant.
- Ensure state and errors remain understandable without color alone. Check long localized labels, text-size choices where supported, and leading/trailing layout when localization affects the change.

If a check cannot run, state the missing evidence. Recommend the next useful check without claiming it passed or treating every untested behavior as a defect.
