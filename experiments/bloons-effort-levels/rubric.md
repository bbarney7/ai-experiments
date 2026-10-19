# Scoring rubric

Recovered rubric snapshot, exported 2026-10-19.

**How each column is scored.** Every score is set against the rungs below, then checked against three sources: Brennen’s play notes (quoted as "You:"), the code review in `reviews/` (bugs found in the code, measured click tests, test re-runs), and the screenshots in `screenshots/`. Half points fall between two rungs. Overall is the plain average of the four, rounded half up.

| Score | Graphics | Complexity | Quality | Creativity |
|---|---|---|---|---|
| 2 | Flat shapes, blurry, towers barely told apart | Minimum: 5 towers, 1 map, formula rounds, upgrades that barely change anything | Core loop broken for a person | Nothing beyond the prompt |
| 3 | Simple shapes; towers look nearly identical | 5–6 towers with real upgrades, 1 map, 15–20 rounds, no extras | — | A theme or flavour text, mechanically generic |
| 4 | Tidy but plain; small, simple map | 5–6 towers, 1 map, 20–24 rounds, 1–2 extras (ability, auto-start, guide) | A core action fails often | A couple of small touches |
| 5 | Competent; distinct towers; plain map | 5 towers and 1 map but 30 rounds and several systems (save, retry, modes) | Works, but a bug you hit regularly or several notable bugs | A consistent identity plus 1–2 original mechanics |
| 6 | Consistent cartoon look, but "mid": samey maps or static towers | 7 towers, 2 maps, 40 rounds, freeplay, difficulties, ≤1 ability | Playable; one bug or broken feature you'd notice | Several original touches; roster still Bloons |
| 7 | Polished: distinct tower art, detailed map | 8–9 towers × 3 tiers, 3 maps, freeplay, ~1 ability | Solid; a few real bugs, mostly found in code | Many original touches, including a standout system |
| 8 | Rich: detailed maps, tier art, effects and animation you notice in play | 8–9 towers, 3 maps, freeplay, 1–4 abilities or extra systems | Only minor bugs; strong tests; no click bug | Several standout original systems you noticed in play |
| 9 | — | 9 towers × 4 tiers, 5+ abilities, 3 distinct maps, freeplay, plus 2 of: save, retry, drag-and-drop, almanac | No bugs found in play, only minor ones in code, clicks measured safe | Original cast or roster plus standout systems |

(8.5 = between 8 and 9; 9.5 = everything at 9 plus more depth, such as 7 abilities or 3 blimp tiers.) Nothing in the set reaches 10. Drag-and-drop counts toward complexity but isn't a quality bug, because the prompt didn't ask for it.
