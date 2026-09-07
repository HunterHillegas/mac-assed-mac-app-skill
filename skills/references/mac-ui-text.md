# Mac UI Text

Self-contained text, label, and command guidance derived from Mac OS X / OS X HIG material.

## Voice

- Use user-centric terms from the task domain.
- Avoid implementation terms unless the app is explicitly for technical users.
- Be concrete and brief. Do not sacrifice clarity for shortness.
- Keep UI text calm. Avoid hype, marketing copy, cute phrasing, and apology-heavy errors.
- Prefer verbs that name the action and nouns users recognize.

## Capitalization

These conventions describe English UI. Preserve established product terminology and use the target locale's capitalization and punctuation rules for translations.

- Use title-style capitalization for:
  - Menu titles
  - Menu items
  - Push buttons
  - Toolbar item labels
  - Labels/headings that are not full sentences
- Use sentence-style capitalization for:
  - Checkbox text
  - Radio button text
  - Dialog messages
  - Alert explanations
  - Help text
  - Full-sentence labels
- In title style, capitalize first and last words, nouns, pronouns, verbs, adjectives, adverbs, and longer prepositions. Lowercase short articles, short prepositions, and coordinating conjunctions unless first or last.
- In sentence style, capitalize the first word and proper nouns. End complete sentences with punctuation; leave fragments unpunctuated.

## Ellipses

- Use the single ellipsis character `…`, not three periods.
- For menu commands, add an ellipsis when further information is required to complete the action: `Open…`, `Save As…`, `Export…`, `Print…`.
- Preserve platform-standard labels such as `Settings…`. Do not infer punctuation solely from a verb: a `Find` action that focuses an existing search field differs from a command that opens a search dialog requiring input.
- Current macOS push-button guidance also uses ellipses for buttons that open another window, view, or app where people can provide input, such as an `Edit…` button in Settings. Check the actual control and destination instead of applying a menu example blindly.
- Do not add an ellipsis when the action executes immediately.
- Do not add an ellipsis just because an alert might appear in some cases.
- For menu commands that simply show a panel or inspector, preserve standard labels such as `Get Info`, `Show Inspector`, `Show Fonts`, and `Show Colors`.

Sources: [Apple menu labels](https://developer.apple.com/design/human-interface-guidelines/menus), [macOS push buttons](https://developer.apple.com/design/human-interface-guidelines/buttons).

## Colons

- Use a colon in introductory text that labels a following control or group: `Sort by:`, `Default format:`, `Open with:`.
- Do not use colons in push buttons, menu items, tab titles, segmented controls, table column headings, or group box titles.
- Do not use a colon at the end of checkbox/radio text unless that text introduces a dependent control.

## Button Labels

- Use action verbs.
- Use consequence-specific labels for destructive or risky actions.
- Prefer `Delete`, `Remove`, `Replace`, `Discard Changes`, `Keep Both`, `Cancel` over `OK`, `Yes`, `No`, `Submit`.
- When a task dialog needs a title, match the command that opened it, minus its ellipsis. Alert titles instead describe the situation; do not replace an informative warning with a bare command name.
- Keep default buttons safe. Do not make a destructive action the default unless the user has clearly chosen that path and the label is explicit.

## Menu Labels

- Use verb phrases for commands.
- Keep labels short but specific.
- Avoid repeating context supplied by the menu title or current selection.
- Use `Show/Hide` for visibility toggles.
- Use `Use/Stop Using`, `Enable/Disable`, or checked menu items when state needs clarity.
- Use consistent object names across menu, toolbar, alert, and Help text.

## Labels and Field Text

- Label every non-obvious control.
- Put labels close to their controls.
- Avoid internal IDs, API names, exception names, and database terms unless useful to the audience. Show user file names and locations when needed to identify, reveal, or recover work; a path is not inherently developer jargon.
- Placeholder text is a hint, not a label. Do not rely on placeholder text as the only field description.
- Avoid restating the group/window title in each label.
- Leave room for localization; expect labels to expand.

## Alerts and Errors

- First sentence: what happened.
- Next sentence if needed: why it matters or what to do.
- Buttons: specific available actions.
- Avoid blaming the user.
- Avoid exposing internal implementation causes unless users can act on them.
- For recoverable failures, offer the recovery path.
- For irreversible or hard-to-recover actions, name what will be lost.

## Help, Tooltips, Accessibility Text

- Use Help menu entries for searchable user help.
- Use tooltips/help tags for controls whose purpose is not obvious from label/icon.
- Accessibility labels should name purpose or action. Expose role, value, and selected/mixed state through native semantics or separate accessibility properties; do not duplicate the role or mutable state in a label the system already announces.
- Help text should answer task questions: what this does, when to use it, what happens next.
- For complex Mac windows, accessibility grouping should match how a user navigates: toolbar, sidebar, content, inspector, table, selected item, and detail.
- Hover-only controls need another named path through visible UI, menus, context menus, or accessibility actions.

## Punctuation and Spacing

- Use one space between sentences.
- Use real punctuation characters when they matter: `…` for ellipsis, curly apostrophes only if the surrounding file/style already uses them.
- Avoid exclamation points in system UI.
- Do not end fragment labels with periods.
