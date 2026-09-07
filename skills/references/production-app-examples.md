# Production App Examples

Use these screenshots as calibration examples for Mac-assed software. They are not templates to copy pixel-for-pixel; they show how production apps can be platform-specific without becoming generic or inaccessible.

Inspect the linked images with an available image viewer when using these examples. Treat them as snapshots of layout and styling, not proof of current app behavior. Keyboard navigation, menu coverage, drag and drop, accessibility, and responsiveness need separate verification.

## Proxyman

![Proxyman network inspector](images/proxyman.png)

Proxyman is a dense professional network-debugging app that still reads as a Mac app:

- It uses a familiar Mac window shape: sidebar, toolbar, table, split panes, bottom status area.
- The main object model is visible: captured traffic grouped by favorites, apps, and domains.
- The interface supports scanning and repeated work with dense tables, row selection, status badges, filters, and detail inspectors.
- Custom visual identity is present, especially in the dark theme and orange selection, but the structure stays Mac-native.
- The visible source lists, split views, toolbars, and tabular detail support an expert audience. Keyboard operation of those surfaces is a separate runtime check.

Useful lesson: a Mac-assed app can be highly specialized and information-dense when its custom styling reinforces the workflow instead of replacing platform structure.

## NetNewsWire

![NetNewsWire feed reader](images/net-news-wire.png)

NetNewsWire is a content app with classic Mac information architecture:

- It uses a three-pane layout: feed/source list, article list, reading pane.
- The hierarchy matches the user's mental model: feeds and folders on the left, selected article list in the middle, article content on the right.
- Visible selection, unread counts, toolbar controls, search, and sidebar disclosure use familiar Mac patterns; the image alone cannot establish their interaction behavior.
- The app is visually restrained so reading stays primary.
- Expressive identity shows up through feed icons, article previews, and comfortable typography rather than custom controls fighting the platform.

Useful lesson: a Mac-assed app can feel plain in the best way. The app gets out of the way by leaning on durable Mac conventions.

## What To Compare

When evaluating a UI against these examples, look for:

- Platform-native structure: sidebars, split views, toolbars, inspectors, tables, source lists, sheets, panels, menus.
- A clear task model: objects, selection, actions, state, hierarchy.
- Real production density: enough content to judge scanning, not empty marketing states.
- Expressive identity that lives above the structure: icons, color, typography, motion, tone, domain-specific details.
- Visible restraint: labels, readable contrast, clear selection, and recognizable controls. Use runtime evidence for keyboard paths and accessibility semantics.
