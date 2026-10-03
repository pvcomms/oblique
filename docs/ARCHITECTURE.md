# Architecture

## In one paragraph

One file, `index.html`, opened from disk or served as-is. It deals cards from a seeded shuffle
of every deck that is not struck, keeps the reader's own decks and notes in `localStorage`
under `pp-oblique`, and makes no request to anything. The sitting (what was dealt, which decks
are struck, the shuffle's seed) lives in page memory and is gone on reload.

## The file

```
index.html
  <style>
    capp:tokens            canonical palette; oblique's own hues (--rule-2, --accent-wash) after it
    .card .face .chips     the card and its controls
    .desk .panel           the shuffle, the reading, what the oblique holds to
  markup
    header.mast            name, deck, the key list
    main.table
      section              #card · #specNote · #carried · chips (#makeOwn #deal #back #again
                           #takeBack) · #turned (#note #keepNote #carryNext) · #history
      aside.desk           #shufflePanel · #readingPanel (#reading #notes) · #lawsPanel (#keptWhere)
    section.lede           the claim
    footer                 two spans
  <script>  (one IIFE)
    capp:esc               esc()
    STARTER                fifty-six cards in the page's own words
    capp:hand              rand seedOf stroke roughRect … ribbon  (canonical; used here: rand
                           seedOf roughRect roughUnderline roughStrike ribbon)
    sketch() paint()       a pen line over an element, redrawn only when its size changes
    parseCards validateCard deckCards shuffle    niwa lib/oblique.ts, by hand
    capp:dates capp:slug capp:plural
    readings()             counts, never a verdict
    KEY capp:store         readStore() persist()
    load() save()          validate the envelope row by row; write {decks, notes}
    SELF SLUGS capp:hash   fromHash() carryHref()
    SPECIMEN               one card and one note, fiction
    state                  own notes off seed dealt at pos pool order into naming sure; S.specimen
    deal back again add takeBack keepNote
    renderCard renderControls renderCarry renderHistory renderDesk renderReading render
    hands                  click and key listeners
    fresh loadSpecimen carried boot
```

## Data flow

```
localStorage[pp-oblique] ──readStore──▶ load() ──▶ own, notes ──▶ decks() ──▶ rebuild() ──▶ pool, order
location.hash ──fromHash──▶ carried() ──▶ #note.value, S.from, S.next
deal() ──▶ dealt[at] ──▶ renderCard renderControls renderHistory renderReading
keepNote() ──▶ notes.unshift({card, deck, said, at: localToday()}) ──▶ save() ──persist──▶ localStorage
```

## What it reads and writes

| Where                     | Direction          | What                                                  |
| ------------------------- | ------------------ | ----------------------------------------------------- |
| `localStorage.pp-oblique` | read+write         | `{ v: 1, decks: [{slug,title,cards}], notes: [...] }` |
| `location.hash`           | read, then cleared | `set`, `from`, `next` — the hand-off                  |
| `fonts/`                  | read               | Newsreader, Plex Mono                                 |

## Invariants

- The specimen is never written; `S.specimen` is true only while it shows, and `save()` is
  never reached from it.
- Only the hand-off's `set` goes into `#note`, through `.value`, and it is not kept until the
  reader keeps the note.
- Nothing in the canonical `capp:` blocks is edited here; the lint compares them to the spine.
- No colour is typed in script; the drawn borders take `--pen` and `--accent` through classes.

## Known sharp edges

- The hash block calls `history.replaceState`; the sitting's draws are therefore `dealt`, not
  `history`. A local named `history` would shadow the window's.
- `readStore()` drops any stored value without `v: 1`; decks kept before 0.2.0 are not read.
- A note's `at` is a local `YYYY-MM-DD`; older notes carry an ISO timestamp and are shown
  through `.slice(0, 10)` either way.
