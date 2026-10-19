# Feature: Calculator in root search

Build Raycast's Calculator into Raycast Rebuild. This is Phase 7 in
`docs/rebuild-order.md`. Everything below is the whole requirement; nothing
else is expected.

## What Raycast does (evidence)

- `docs/feature-inventory.md`, row "Calculator": Raycast evaluates in a Rust
  module (`calculator-rs.node`, crates `rust_decimal`, `jiff`, `icu_calendar`),
  replacing SoulverCore. It is exposed as `backend.calculator.calculate`,
  `parseDate`, `parseDuration` and `history*`, and stores history in a
  `calculator_history` table.
- `docs/rebuild-order.md`, "7. Calculator": inline result row in root search,
  copy action, history.
- The real app is installed at `/Applications/Raycast.app`. The REA MCP tools
  are available if you want to inspect it further.

## Requirements

1. **Inline result.** When the root search query is a calculation, a
   Calculator result appears as the first item, above every other section. It
   shows the expression and the result. Other results still show below it.
2. **Evaluation lives in the Rust core** (`app/src-tauri`), not in the
   webview, matching Raycast's direction.
3. **Arithmetic:** `+ - * / ^`, parentheses, unary minus, decimals, `%` as in
   `15% of 80` and `80 + 15%`, and the constants `pi` and `e`. Functions:
   `sqrt`, `abs`, `round`, `floor`, `ceil`, `sin`, `cos`, `tan` (radians),
   `log` (base 10) and `ln`. Use decimal arithmetic, so `0.1 + 0.2` is `0.3`.
4. **Units** with `in` or `to`, case-insensitive, singular or plural:
   - length (mm, cm, m, km, in, ft, yd, mi)
   - mass (g, kg, oz, lb)
   - temperature (c, f, k; also `celsius`, `fahrenheit`)
   - volume (ml, l, cup, gal)
   - data (b, kb, mb, gb, tb; 1 kb = 1000 b)
   - time (s, min, h, day, week)
5. **Dates:**
   - `today + 3 days` and `today - 2 weeks` give a date.
   - `days until 2026-12-25` gives a count of days.
   - `2026-12-25 - 2026-10-01` gives a duration in days.
   - Dates use the local time zone.
6. **Not a calculation:** plain words (`safari`), a lone number (`2024`), and
   anything that fails to parse show no Calculator result and no error.
   Division by zero shows no result.
7. **Display:** at most 10 decimal places with trailing zeros trimmed, and
   thousands separators on screen (`1,234.5`). Copy and paste use the plain
   value (`1234.5`). Units show the unit (`3.1068559612 mi`).
8. **Actions:**
   - Enter copies the result and shows the usual toast.
   - The ⌘K action panel offers Copy Result and Paste Result. Paste Result goes
     into the frontmost app, using the existing paste path.
9. **History:** copying or pasting a result saves `{expression, result,
   created_at}` to a `calculator_history` table (a schema migration in
   `app/src-tauri/src/data/db.rs`). A root command, "Calculator History",
   lists entries newest first and is searchable. It has Copy and Delete
   actions.
10. **Speed:** evaluation must not slow root search. It has to fit inside
    the existing per-keystroke budget.

## UI contract (used by the scoring tests, keep exactly)

- The result row's element holding the result text has
  `data-testid="calculator-result"`. Its text content is the display result,
  for example `1,234.5` or `3.1068559612 mi`.
- The expression element has `data-testid="calculator-expression"`.
- No element with `data-testid="calculator-result"` exists when there is no
  result.

## Examples

| Query | Display result |
| --- | --- |
| `2+2` | `4` |
| `(3 + 4) * 2^3` | `56` |
| `0.1 + 0.2` | `0.3` |
| `15% of 80` | `12` |
| `80 + 15%` | `92` |
| `sqrt(144) / 3` | `4` |
| `1234.5 * 1` | `1,234.5` |
| `5 km in miles` | `3.1068559612 mi` |
| `72 f to c` | `22.2222222222 °C` |
| `1 gb in mb` | `1,000 MB` |
| `2 hours in minutes` | `120 min` |
| `safari` | (no result) |
| `2024` | (no result) |
| `1/0` | (no result) |

## Done when

- Rust unit tests cover the evaluator, including every example above.
- A new `scripts/verify-calculator.sh` drives the real app, in the style of
  the other `scripts/verify-*.sh`. It types queries into root search, reads the
  `calculator-result` element, checks Copy (saving and restoring the
  pasteboard), and checks that history records an entry. It passes.
- `scripts/verify-phase6.sh` (the full regression chain) still passes, and so
  do all existing unit tests.
