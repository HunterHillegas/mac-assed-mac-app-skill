# Mac Layout Structure

Use this for concrete Mac window composition: settings forms, toolbars, sidebars, inspectors, and bottom bars. Historical measurements below are fallback calibration, not current system constants. Prefer system layout, intrinsic control sizes, safe areas, and the app's task model; verify on supported macOS versions.

## Core Layout Tests

- Balance visual weight where it helps the task. Do not force a sidebar/content/inspector workspace or document canvas into a symmetrical composition.
- Keep margins consistent within comparable groups; intentional differences can express hierarchy or accommodate system chrome.
- Align labels and controls deliberately. Two-column forms often use trailing-aligned labels and leading-aligned controls; use native grouped forms or stacked labels when they better accommodate long text and narrow panes.
- Baseline-align controls in the same row, especially labels with pop-up buttons, text fields, combo boxes, pickers, and steppers.
- Keep related controls visually close; separate groups with whitespace, separators, or group boxes only when the grouping earns the space.
- Use regular system controls by default. Small or mini controls can suit inspectors, dense tables, utility panels, palettes, and accessory views; keep them legible and comfortable to target.
- Do not mix control sizes casually inside one pane.

## Form and Settings Spacing

Use native form spacing first. For custom layouts, these historical values can help diagnose crowding; do not impose fixed heights or override modern system spacing to match them.

- Use about 20 pt margins around ordinary window content.
- Controls directly below a titlebar or toolbar usually need about 14 pt top spacing.
- Stacked regular controls need at least 6 pt between rows.
- Use about 12 pt between a control group and bottom buttons.
- Use 12-24 pt whitespace between groups when grouping by whitespace.
- Group boxes need stronger internal padding, commonly about 16 pt on each side.
- Let system dialogs arrange their own buttons. In custom left-to-right dialogs, dismissal actions usually sit at the lower-right with the default action to the right of Cancel; place Help opposite them. Settings panes without dismissal actions can place Help in either lower corner. Check localization rather than hard-coding physical left/right everywhere.
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
- Prefer a trailing sidebar inspector for modern primary-window workflows.
- Use a floating inspector panel only when users need persistent auxiliary controls across windows or documents.
- Update the inspector when the inspected selection changes. Keep that target stable when focus moves into the inspector's own editing controls, and represent empty or mixed selections clearly.
- Hide irrelevant inspector sections; disable controls whose presence explains unavailable state.
- Use small controls in inspector panels and dense inspectors. Keep grouping strong because inspectors are information-dense by nature.
- Size inspectors for their actual labels, editors, and mixed-value states; navigation-sidebar widths need not fit a property form.

## Bottom Bars and Accessory Areas

- Use bottom bars for persistent status or controls that apply to the visible content, not for primary navigation.
- Historical bottom bars were roughly 22–32 pt high. Size modern accessory areas to their actual controls and text, without forcing those heights.
- Keep bottom-bar controls vertically centered and tightly related to the content above them.
- Use secondary text for status labels.
- Avoid turning bottom bars into a second toolbar. If a command matters globally, it probably belongs in the toolbar or menu.
