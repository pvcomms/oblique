---
title: Harmonise to the spine
status: shipped
created: 2026-10-03
---

# 001 — Harmonise to the spine

## Why

Oblique was ported from niwa with its own copy of the pen library, its own token names
(`--paper`, `--sheet`, `--ink-2`), its own storage shape and no hand-off. Every instrument on
the contract shares those by copy, and the lint checks the copy. Nothing here changes what
the page decides, because it decides nothing: it still deals a card the reader did not choose
and never says what one means. The specimen it now opens on is one dealt card and one note,
labelled fiction and read-only.

## What changes

- Before: opens on an empty card; `localStorage` holds a bare `{decks, notes}`; a note is
  dated by `new Date().toISOString()`; no hash is read; no holds-to panel.
- After: opens on the specimen, _Make your own_ leaves it; storage is the `{ v: 1 }` envelope
  read through `readStore()` and validated row by row; a note is dated by `localToday()`;
  `#set=…&from=…&next=…` opens a fresh sitting with the text in the note for what the next
  card turns up, _Carried from <name>_ on the sheet and _Carry this to <name>_ under the
  note; a third desk panel says what the oblique holds to and where things are kept.

## Where

| File                                      | Change                                                 |
| ----------------------------------------- | ------------------------------------------------------ |
| `index.html`                              | canonical blocks, token renames, specimen, hash, panel |
| `README.md`                               | canonical headings; claim paragraph unchanged          |
| `docs/*`, `SECURITY.md`, `AGENTS.md`      | filled                                                 |
| `spine/bin/verify/steps/oblique-steps.js` | drives the specimen and the hand-off too               |

## Out of scope

Migrating decks kept before the envelope. A grain overlay (the tokens are there; the page does
not use them). Any change to the starter deck or the readings.

## Acceptance checks

```bash
cd ~/work/capp/spine
python3 bin/instrument-lint.py ../instruments/oblique
# OK oblique
cd bin/verify
node verify.mjs ~/work/capp/instruments/oblique
# OK: no console errors, page errors, CSP violations, failed or off-origin requests
node verify.mjs ~/work/capp/instruments/oblique --narrow
# OK: no console errors, page errors, CSP violations, failed or off-origin requests
node verify.mjs ~/work/capp/instruments/oblique steps/oblique-steps.js
# OK: no console errors, page errors, CSP violations, failed or off-origin requests
node reload-all.mjs oblique
# oblique        kept 262b across reload; text 2591 chars; no errors
```

- [x] Opens on the specimen, labelled fiction, card disabled, note read-only, nothing in storage
- [x] `#set=a%20test&from=spine&next=tack` puts `a test` in the note and nothing in the draft, clears the hash, shows _Carried from spine_, and the link under the note carries `set=a+test&from=oblique`
- [x] Light and dark screenshots at 1360 and 390 wide, no horizontal overflow

## Notes

The sitting's draws are `dealt`, not `history`: the canonical hash block calls
`history.replaceState`.
