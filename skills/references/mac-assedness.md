# Mac-Assedness and Expressive Mac Software

Self-contained guidance derived from Simon Lou's thesis, "Opinionated, Expressive, Mac-Assed: Designing original software that feels at home on the Mac" (https://thesis.simonlou.com). Use this when a UI task is about making a Mac app feel native without making it generic.

Additional source notes incorporated here:

- Daring Fireball on Sonar: https://daringfireball.net/linked/2024/02/25/sonar
- Watts Martin on Mac app feel: https://coyotetracks.org/blog/app-feel-on-mac/
- Daring Fireball on Nova: https://daringfireball.net/linked/2020/09/24/nova
- Daring Fireball on Sketch: https://daringfireball.net/2020/11/sketch_mac_app_mac_apps
- Daring Fireball on Safari 15 tabs: https://daringfireball.net/2021/10/the_tragedy_of_safari_15_quote_unquote_tabs
- Paulo Andrade on SwiftUI Mac apps: https://pfandrade.me/blog/mac-assed-swiftui-app/

## Core Definition

- A Mac-assed app does not merely run on macOS; it thinks like a Mac app.
- Treat Mac-assedness as platform fluency: window behavior, menu structure, keyboard commands, pointer precision, density, persistence, preferences, drag and drop, inspectors, document behavior, system integration, and performance expectations.
- Do not equate Mac-assedness with blindly following Apple's newest visual style. The Mac has four decades of hardened conventions; current Apple fashion can conflict with them.
- Do not equate Mac-assedness with general ease of use. Some very Mac-like apps are complex, dense, and power-user-oriented. That can be right for the audience.
- Being a good platform citizen is not the same thing as using a native toolkit. Native controls and latest APIs help, but the deeper goal is respecting the Mac's learned behaviors.
- A non-native app can feel more Mac-like than a native app if it honors menus, Settings, Services, text input behavior, keyboard conventions, window behavior, and system integration.
- A native app can still fail as a Mac app if it breaks those expectations.

## Good Mac Citizenship

Check platform citizenship before judging visual style:

- Standard menus should exist in the expected order and contain expected commands.
- Settings should open from `Settings...` and `Command-,` in a real settings window, not an editor tab or raw configuration file.
- Services should work from the menu bar and relevant context menus.
- Text fields should inherit system text behavior: standard editing shortcuts, user key bindings, text replacements, smart punctuation preferences, spelling, focus, selection, and accessibility.
- Icons, symbols, controls, and form elements should look like they belong on current macOS, even when they are custom.
- The app should use Mac-like typography and density. Custom fonts can be expressive, but the UI should not feel imported from another platform.
- Being "technically native" is not enough; test the behaviors users learn from other Mac apps.

## Structural Layer vs Expressive Layer

Protect the structural layer:

- Menu bar as command map.
- Standard keyboard shortcuts.
- Window and document behavior.
- Selection before action.
- Source/list/detail patterns where they match the information hierarchy.
- Toolbars as window-level command surfaces.
- Inspectors and panels for auxiliary properties.
- Preferences/settings as durable choices.
- Drag and drop, undo, autosave, state restoration, Quick Look/open/reveal patterns.
- Accessibility semantics and keyboard navigation.

Use the expressive layer for identity:

- App icon and document icons.
- Custom toolbar/sidebar icons where SF Symbols are too generic.
- Typography that reinforces the task.
- Color and material choices that support hierarchy.
- Motion that explains relationships.
- Custom controls that preserve expected behavior while improving clarity or feel.
- Microcopy and tone that fit the app's audience.
- Domain metaphors that clarify purpose without turning into decoration.
- User-controlled customization that lets professional users shape the tool without destroying platform conventions.
- Documentation, onboarding, and release communication that feel like part of a serious Mac product, not an afterthought.

## Decision Rule for Custom UI

Use custom UI when at least one is true:

- It clarifies a domain concept better than a system default.
- It makes an important action more recognizable.
- It improves speed or power-user flow without hiding discoverability.
- It reinforces a coherent app identity.
- It solves a specific interaction problem that standard Mac patterns do not solve well.

Avoid custom UI when:

- It is different only for novelty.
- It hides standard behavior users expect.
- It breaks keyboard, pointer, accessibility, focus, or disabled-state behavior.
- It requires rebuilding subtle system interactions that the app cannot maintain.
- It makes the app fight the current macOS environment without a strong reason.

Every deviation has a cognitive cost. Pay it back with a visibly better experience.

## Native Technology Judgment

- Prefer AppKit or SwiftUI with AppKit bridges when deep Mac behavior matters.
- SwiftUI can be Mac-assed, but inspect missing Mac-specific affordances and bridge where needed.
- Catalyst and web/Electron-style stacks need extra scrutiny: navigation, windowing, menu behavior, pointer handling, keyboard shortcuts, text editing, performance, accessibility, and system services often reveal the uncanny valley.
- Native code is not automatically better for every subsystem. Extension ecosystems, scripting, import/export formats, and plugin APIs can reasonably use more portable technology if the Mac shell remains excellent.
- Judge the app by citizenship and feel, not toolkit labels alone. Cocoa, AppKit, SwiftUI, Catalyst, Electron, and web technologies can all succeed or fail depending on how completely they honor Mac behavior.

## SwiftUI Mac Reality

SwiftUI can ship a good Mac app, but pure SwiftUI still needs scrutiny where AppKit solved details years ago:

- Selection has layers: active-window selection, inactive-window selection, selected-but-not-focused state, and context-menu target. Users need to see which object is selected and which pane receives keyboard input.
- System `List` often gets Mac selection and context-menu behavior right because it inherits table behavior. Custom `ScrollView`/`LazyVStack` lists must recreate focus, emphasized selection, inactive-window appearance, and context-menu target feedback deliberately.
- Read `appearsActive` and equivalent focus/emphasis state when styling custom selected rows. A selected row in an inactive window should not look like the key-window selection.
- Right-clicking an unselected object should not casually change selection. If the menu applies to the clicked object, show a separate context target affordance.
- Drag and drop is core Mac behavior. SwiftUI drag APIs may not expose enough drag-session state; avoid UI that can get stuck dimmed or stale after drops outside the window. Bridge to AppKit when source/session feedback matters.
- Keyboard support must go beyond command shortcuts. Lists need arrow-key navigation; search fields should allow typing while arrowing through results when that matches the task; panes need clear focus behavior.
- SwiftUI toolbar placement can be too abstract for complex Mac windows. Design one coherent Mac toolbar; do not accept scattered `.toolbar` modifiers if they produce surprising placement or mix sidebar/detail ownership.
- Reuse across iOS, iPadOS, and macOS is valuable, but not when it erases Mac-only behaviors. Fork or bridge platform-specific interaction where needed.

## Professional Tool Trust

Mac-assed professional apps often earn trust outside the visible UI:

- They are fast and fluid enough that the interface feels like a local tool, not a remote wrapper.
- They save through authoritative systems or open formats when possible, so users keep control of their data.
- They interoperate with adjacent workflows and web UIs instead of trapping work in a private silo.
- They document the tool with the same care as the product UI.
- They use pricing, licensing, trials, and update policies that respect long-term professional use. This is not a UI rule, but it affects whether the app feels like a durable Mac tool.

## Hierarchy and Modern macOS

- Do not let visual simplicity erase hierarchy.
- Be cautious with floating controls over content. Users may assume floating controls affect the content directly beneath them, while Mac toolbars often apply to the whole window or selection.
- Keep browser/app chrome visually distinct from user content when ownership matters. Users should not have to ask whether a control belongs to the app or the content.
- Do not let glass/translucency reduce legibility, contrast, or control recognition.
- Do not let color-matching, translucency, or edge-to-edge content blur which layer owns a button, tab, toolbar, or selection.
- Distinguish hierarchical depth from sculptural depth:
  - Hierarchical depth communicates what controls belong to and what layer they affect.
  - Sculptural depth makes something look tactile or dimensional.
- Sculptural depth without hierarchy can look rich while making the interface harder to understand.
- Match the platform's level of visual quality, but do not copy it uncritically when it hurts clarity.
- The active object should be the visually clearest object, not the most muted one. Selection and active-tab states must pop in light mode, dark mode, and small sets.

## Expressiveness Without Slop

- Expression is not the enemy of usability. Distinct shape, iconography, typography, and motion can make actions easier to recognize.
- Expression becomes a problem when it hides actionability, weakens contrast, obscures state, or forces users to relearn basics.
- Novel styling is not a justification by itself. Change that breaks established habits needs to work better, not merely look fresher.
- The app's purpose should guide its style. A code editor, writing tool, invoice app, music tool, and photo organizer do not need the same tone.
- A visually quiet app can still be expressive through reduction, type, spacing, file model, and workflow.
- Playfulness is valid on the Mac when it reinforces a coherent tool. Keep delight small, purposeful, and durable.
- Do not make "boring" domains look careless. A serious utility can still have taste.

## Design Decision Framework

When making a disputed UI choice, score the option against:

- Purpose: Does it support what the app is for?
- Mac conventions: Does it respect learned platform behavior?
- Usability: Is it legible, discoverable, responsive, accessible, and low-friction for the target users?
- Current macOS fit: Does it feel plausible in today's system environment?
- Expression: Does it give the app a specific point of view without overriding the above?
- Maintenance: Can the team preserve this behavior and style across OS releases?

Prefer decisions where expression strengthens purpose and structure. Reject decisions where expression replaces structure.

## Example Patterns

Sketch:

- Strong Mac structure: canvas center, pages/layers sidebar, inspector, menu-backed toolbar commands.
- Custom iconography can work when it communicates app-specific concepts better than generic symbols.
- Variable/contextual toolbars can surface relevant actions, but risk hiding discoverability when unavailable actions vanish instead of appearing disabled.
- Pro apps can optimize for keyboard-driven experts, but menus and visible command paths still matter.

Nova:

- A highly custom visual language can still feel Mac-like when source lists, Services, title/path behavior, tabs, split views, and responsiveness behave correctly.
- Custom colorful icons can define app identity when they are coherent and recognizable.
- Classic preferences/settings with large category icons can be nostalgic and functional when the inner controls remain standard.
- Native feel matters strongly in categories dominated by cross-platform apps.
- Visual and functional customization can be a strength when users can shape the tool around their work.
- Documentation quality matters for professional tools; it is part of the product experience.

Sonar:

- A lightweight Mac task UI can coexist with enterprise issue-tracking power when the app keeps the workflow fast, local-feeling, and intuitive.
- Syncing through official APIs and staying compatible with the canonical web UI reinforces trust and avoids data lock-in.

iA Writer:

- Expressiveness can come from reduction. A focused writing app can use mostly system controls and still feel distinct through typography, document model, modes, and restraint.
- Purpose-specific type choices can be felt more than noticed.
- Plain file formats and direct file access can reinforce Mac trust and user control.
- Checkboxes and tabbed preference windows can feel more Mac-like than mobile-style toggles.

## Audit Prompts

Ask these while reviewing a macOS UI:

- Does this app protect the Mac structural layer?
- What is the app's own voice?
- Which custom choices improve clarity or purpose?
- Which custom choices are merely decorative?
- Where has visual fashion weakened hierarchy?
- Did a visual change make the user think about something that used to be automatic?
- Are we copying iOS, copying current Apple visuals, or serving Mac behavior?
- Does the technical foundation cap how Mac-assed this can become?
- If this is SwiftUI, did we test the Mac details SwiftUI does not guarantee: focus, selection emphasis, context menus, drag sessions, keyboard navigation, and toolbar placement?
- Would a seasoned Mac user find the behavior natural after the first minute?
- Would a new user still see what is actionable?
- Does the app feel made by someone with an opinion, or assembled from defaults?
- Does it behave like a good Mac citizen in Settings, Services, menus, text fields, and keyboard paths?
- Does the surrounding product experience, including documentation and data ownership, support long-term trust?
