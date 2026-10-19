# Feature: Snippets with keyword expansion

Build Raycast's Snippets into Raycast Rebuild. This is "Extras: 2. Snippets"
in `docs/rebuild-order.md`. Everything below is the whole requirement; nothing
else is expected.

## What Raycast does (evidence)

- `docs/feature-inventory.md`, row "Snippets / text expansion": the backend
  stores snippets (`snippets` table, 17 `backend.snippets.*` methods) and
  syncs the keyword set to the native host (`snippets.register`, `remove` and
  `expand`). Matching and expansion happen natively.
- `docs/architecture.md`, "Snippets: keyword detection and expansion (#7)":
  - Detection uses AppKit global and local `NSEvent` monitors for keyDown and
    mouse-down, not a CGEventTap.
  - It needs Accessibility trust.
  - Matching modes are "Requires exact match" and "Requires delimiter", plus
    "Expand within words".
  - A single-expander lease file stops two Raycast builds expanding the same
    keyword.
- The real app is installed at `/Applications/Raycast.app`. The REA MCP tools
  are available if you want to inspect it further.

## Requirements

1. **Storage.** A `snippets` table with id, name, text, keyword (optional,
   unique when set), created_at, updated_at, last_used_at and use_count. Add
   it through a schema migration in `app/src-tauri/src/data/db.rs`. Snippet
   text is user data: never log it.
2. **Create Snippet:** a root command opening a form with Name, Snippet and
   Keyword. Validation:
   - name and text are required;
   - a keyword can't contain whitespace;
   - a duplicate keyword is rejected with a clear message.
3. **Search Snippets:** a root command opening a list view.
   - Each row shows the name, keyword and a text preview, plus a detail pane
     with the full expanded text.
   - The search field filters by name, keyword and text.
   - Enter pastes the snippet into the frontmost app, using the existing paste
     path that saves and restores the pasteboard.
   - The ⌘K actions are Paste, Copy, Edit and Delete. Delete asks for
     confirmation.
   - Each snippet also shows as an item in root search, by name and keyword.
4. **Placeholders,** expanded when pasted, copied or expanded by keyword:
   - `{clipboard}`: current clipboard text;
   - `{date}`, `{time}`, `{datetime}`: local, medium style;
   - `{cursor}`: the final caret position; after inserting, move the caret back
     there with left-arrow presses.

   Unknown placeholders stay as literal text.
5. **Keyword expansion** in any other app:
   - Typing a snippet's keyword replaces it with the snippet text.
   - Default mode is exact match. Expand as soon as the typed characters end
     with the keyword and the character before it is the start of input,
     whitespace or punctuation.
   - Replacement deletes the keyword with backspaces, then pastes the
     expansion, saving and restoring the pasteboard.
   - Reset the typed buffer on mouse-down, app switch, arrow keys and ⌘
     shortcuts.
   - Never expand inside Raycast Rebuild's own windows or while secure text
     input is on (password fields).
   - Expansion needs Accessibility. Without it, Search Snippets shows a
     banner, and nothing crashes.
6. **Settings:** an "Expand within words" toggle (off by default) and a
   global on/off switch for keyword expansion, stored with the existing
   settings.

## UI contract (used by the scoring tests, keep exactly)

- Search Snippets' search field has `aria-label="Search snippets"`.
- Each snippet row has `data-testid="snippet-row"` and a `data-snippet-name`
  attribute holding the snippet name.
- The Create Snippet form fields have the aria-labels `Name`, `Snippet` and
  `Keyword`.

## Environment notes

- Lockpaw runs on this Mac with active event taps and drops synthetic
  HID-level key events. The existing paste path posts ⌘V with
  `CGEventPostToPid` for that reason (see `app/src-tauri/src/clipboard/paste.rs`).
- `scripts/tools` builds "RR Paste Target", a tiny app with a text view that
  tests can type and paste into. `scripts/verify-phase4.sh` shows how to use
  it.

## Done when

- Rust unit tests cover storage, validation, placeholder expansion and
  keyword matching (exact match, delimiter, within-words, buffer resets).
- A new `scripts/verify-snippets.sh` drives the real app, in the style of the
  other `scripts/verify-*.sh`:
  - creates snippets through the UI;
  - finds them in Search Snippets and root search;
  - pastes one into RR Paste Target;
  - shows keyword expansion into RR Paste Target, or reports SKIP with the
    reason when synthetic typing can't reach the monitor;
  - saves and restores the pasteboard.

  It passes.
- `scripts/verify-phase6.sh` (the full regression chain) still passes, and so
  do all existing unit tests.
