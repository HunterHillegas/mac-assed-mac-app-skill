# Mac-Assedness and Expressive Mac Software

Self-contained guidance derived from Simon Lou's thesis, "Opinionated, Expressive, Mac-Assed: Designing original software that feels at home on the Mac" (https://thesis.simonlou.com). Use this when a UI task is about making a Mac app feel native without making it generic.

## Core Definition

- A Mac-assed app does not merely run on macOS; it thinks like a Mac app.
- Treat Mac-assedness as platform fluency: window behavior, menu structure, keyboard commands, pointer precision, density, persistence, preferences, drag and drop, inspectors, document behavior, system integration, and performance expectations.
- Do not equate Mac-assedness with blindly following Apple's newest visual style. The Mac has four decades of hardened conventions; current Apple fashion can conflict with them.
- Do not equate Mac-assedness with general ease of use. Some very Mac-like apps are complex, dense, and power-user-oriented. That can be right for the audience.
- Being a good platform citizen is related but narrower: native controls and latest APIs help, but the deeper goal is respecting the Mac's learned behaviors.

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

## Hierarchy and Modern macOS

- Do not let visual simplicity erase hierarchy.
- Be cautious with floating controls over content. Users may assume floating controls affect the content directly beneath them, while Mac toolbars often apply to the whole window or selection.
- Do not let glass/translucency reduce legibility, contrast, or control recognition.
- Distinguish hierarchical depth from sculptural depth:
  - Hierarchical depth communicates what controls belong to and what layer they affect.
  - Sculptural depth makes something look tactile or dimensional.
- Sculptural depth without hierarchy can look rich while making the interface harder to understand.
- Match the platform's level of visual quality, but do not copy it uncritically when it hurts clarity.

## Expressiveness Without Slop

- Expression is not the enemy of usability. Distinct shape, iconography, typography, and motion can make actions easier to recognize.
- Expression becomes a problem when it hides actionability, weakens contrast, obscures state, or forces users to relearn basics.
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
- Are we copying iOS, copying current Apple visuals, or serving Mac behavior?
- Does the technical foundation cap how Mac-assed this can become?
- Would a seasoned Mac user find the behavior natural after the first minute?
- Would a new user still see what is actionable?
- Does the app feel made by someone with an opinion, or assembled from defaults?
