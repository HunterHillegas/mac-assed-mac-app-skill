# Mac Layout Structure

Use this for concrete Mac window composition: settings forms, toolbars, sidebars, inspectors, and bottom bars. Keep it subordinate to the app's task model; metrics are starting points, not magic.

## Core Layout Tests

- Prefer center-equalized layouts: balance visual weight around the window's center axis without center-aligning everything.
- Consistency beats exact numbers. A 18 pt margin used consistently is less harmful than one side at 20 pt and the other at 14 pt.
- Align labels and controls deliberately. In stacked form rows, right-align category labels and left-align the controls they describe.
- Baseline-align controls in the same row, especially labels with pop-up buttons, text fields, combo boxes, pickers, and steppers.
- Keep related controls visually close; separate groups with whitespace, separators, or group boxes only when the grouping earns the space.
- Use full-size controls by default. Use small or mini controls only for inspectors, utility panels, palettes, dense accessory views, and space-constrained bottom bars.
- Do not mix control sizes casually inside one pane.

## Form and Settings Spacing

- Use about 20 pt margins around ordinary window content.
- Controls directly below a titlebar or toolbar usually need about 14 pt top spacing.
- Stacked regular controls need at least 6 pt between rows.
- Use about 12 pt between a control group and bottom buttons.
- Use 12-24 pt whitespace between groups when grouping by whitespace.
- Group boxes need stronger internal padding, commonly about 16 pt on each side.
- Help belongs at the lower-left of settings/dialog surfaces when present. Confirmation buttons belong at the lower-right, with the default action to the right of Cancel.
- Optional descriptions under checkboxes/radio buttons should be secondary text, close to the control, and aligned with the control label text rather than the checkbox/radio glyph.

## Toolbars

- Build the default toolbar from the user's sequence of work: frequent, high-visibility commands first; secondary or global utilities later.
- Group toolbar commands by task. Rank groups and commands left-to-right by importance or object hierarchy.
- Toolbar items are accelerators. Every important toolbar command still needs a menu command.
- Do not put the whole command set in the toolbar. Customization can expose extra items for broad professional tools.
- Search, share, sidebar toggles, inspector toggles, and view controls are global or structural items; keep them visually distinct from content commands.
- Use centered toolbar items only when they have a real structural job, such as title/subtitle, segmented view switching, or search in a focused utility.
- Audit toolbar overflow in the running app at narrow widths. The most important commands should survive first.

## Sidebars

- Use sidebars for sources, collections, libraries, accounts, folders, scopes, and app-owned containers.
- A sidebar should normally drive the detail area; it is not a junk drawer for buttons.
- Start with sensible width limits. Many Mac sidebars default to roughly 150-250 pt wide with a maximum near 350-400 pt; treat these as starting defaults, not hard minimums.
- Keep sidebar rows scannable: icon, title, count/status only when useful. Put row actions in menus, contextual menus, detail panes, or bottom bars.
- Sidebar contextual menus should act on the clicked row or selection and make that target obvious.
- A sidebar bottom bar can hold closely related add/remove/action controls, but keep it sparse.
- In modern translucent sidebars, avoid loud tinted icons that fight the material; selected row, text, and hierarchy should carry state.

## Inspectors

- Use inspectors for contextual properties or metadata of the current selection.
- Keep inspectors modeless, selection-aware, and quick to hide/show.
- Prefer a right sidebar inspector for modern primary-window workflows.
- Use a floating inspector panel only when users need persistent auxiliary controls across windows or documents.
- Inspector content should update immediately when selection or focus changes.
- Hide irrelevant inspector sections; disable controls whose presence explains unavailable state.
- Use small controls in inspector panels and dense inspectors. Keep grouping strong because inspectors are information-dense by nature.
- Start inspector width limits near sidebar limits unless the content has a stronger reason.

## Bottom Bars and Accessory Areas

- Use bottom bars for persistent status or controls that apply to the visible content, not for primary navigation.
- Large bottom bars are roughly 32 pt high; small bottom bars roughly 22 pt high.
- Keep bottom-bar controls vertically centered and tightly related to the content above them.
- Use secondary text for status labels.
- Avoid turning bottom bars into a second toolbar. If a command matters globally, it probably belongs in the toolbar or menu.
